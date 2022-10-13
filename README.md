# ➟ add-to-estuary

Store your files on IPFS & Filecoin via [Estuary](https://estuary.tech/) from a GitHub Action

![better together](https://bafkreideca5qwa3yrregubuesznsudwndszkdze2dmn7rg2k4ma3uldpyi.ipfs.w3s.link/)

A [composite github action][1]. It's [just yaml!](./action.yml)

## Example

```yml
jobs:
  run-action:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2

    - id: add_to_estuary
      uses: olizilla/add-to-estuary@main
      with:
        estuary_api_key: ${{ secrets.ESTUARY_API_KEY }}
        path_to_add: 'dist/cool-cat.gif'
    
    # use the CID estuary returned for something fun!
    - run: echo ${{ steps.add_to_estuary.outputs.cid }}
```

## Inputs
You must provide the `path_to_add` and an `estuary_api_key` to get the magic.

### path_to_add
File path to add to Estuary. _required_

### estuary_api_key
API Key for Estuary. _required_

### estuary_api_url
URL for Estuary instance and endpoint to POST the files to. 

_Default_ https://shuttle-4.estuary.tech/content/add-car

### gateway_url
URL for IPFS gateway for preview urls

_Default_ https://dweb.link


## Outputs
You can grab the `cid` and `url` values for use in subsequent steps in your workflows, for things like setting a dnslink to publish a website on IPFS.

### cid
The IPFS Content ID for the directory e.g. bafkreihc7sejzq4ab4kygfyjvs4ye7bxyzgfdpzt7caqkizqnzgf6zgogi'

### url
The IPFS gateway URL for the directory e.g https://dweb.link/ipfs/bafkreihc7sejzq4ab4kygfyjvs4ye7bxyzgfdpzt7caqkizqnzgf6zgogi'


[1]: https://docs.github.com/en/actions/creating-actions/creating-a-composite-action
