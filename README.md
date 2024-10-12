# Unichain Node

![image](logo.png)

This repository contains the relevant configuration to run your own node on the Unichain network.

### Troubleshooting

If you encounter problems with your node, please open a [GitHub issue](https://github.com/Uniswap/unichain-node/issues)

### Supported Networks

| Network      | Status |
|-------------------| ------ |
| Testnet (Sepolia) | ✅     |


### Usage

1. Ensure you have an Ethereum L1 full node RPC available, and set `OP_NODE_L1_ETH_RPC` & `OP_NODE_L1_BEACON` (in the `.env.sepolia` file). If running your own L1 node, it needs to be synced before Unichain will be able to fully sync.
2. Run:

```

sudo apt update && sudo apt upgrade -y

```

```
sudo apt install docker.io

```

```
sudo curl -L "https://github.com/docker/compose/releases/download/v2.20.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

```
```
git clone https://github.com/Uniswap/unichain-node

```
```
cd unichain-node
nano .env.sepolia

```
Change 02 line below: 

```
OP_NODE_L1_ETH_RPC=https://ethereum-sepolia-rpc.publicnode.com
OP_NODE_L1_BEACON=https://ethereum-sepolia-beacon-api.publicnode.com

```

```
docker compose up -d

```

3. You should now be able to `curl` your Unichain node:

```
curl -d '{"id":1,"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false]}' \
  -H "Content-Type: application/json" http://localhost:8545
```

4. Check logs

```
docker logs unichain-node-op-node-1 -f

```

5. Take Private_key and add to Metamask wallet

```
cat ~/unichain-node/geth-data/geth/nodekey

```
6. Faucet Unichain Sepolia Testnet in here : (https://thirdweb.com/unichain-sepolia-testnet)
   
7. To stop your node, run:
   
```
docker compose down

```

#### Persisting Data

By default, the data directory is stored in `${PROJECT_ROOT}/geth-data`. You can override this by modifying the value of
`HOST_DATA_DIR` variable in the [`.env`](./.env) file.
You can check RPC Gateway to Ethereum Fastest, free-est, and privacy first RPC endpoint for the Ethereum network. Connect reliably to Web3 with ease!
link : (https://ethereum-sepolia.publicnode.com/).
