# Foundry ERC20

# Getting Started

## Requirements

- git
- foundry

## Quickstart

```
git clone https://github.com/spyros-zikos/foundry-custom-erc20-token
cd foundry-custom-erc20-token
forge install 
forge build
```

# Usage

## OpenZeppelin

[OpenZeppelin Contracts Docs](https://docs.openzeppelin.com/contracts/4.x/)
<br><br>
[OpenZeppelin GitHub Repo](https://github.com/OpenZeppelin/openzeppelin-contracts)
<br>

### Installing OpenZeppelin Contracts Package

```bash
forge install OpenZeppelin/openzeppelin-contracts --no-commit
```

## Start a local node

```
make anvil
```

## Deploy

This will default to your local node. You need to have it running in another terminal in order for it to deploy.

```
make deploy
```

## Deploy - Other Network

[See below](#deployment-to-a-testnet-or-mainnet)

## Testing

There are 4 test tiers.

1. Unit
2. Integration
3. Forked
4. Staging

This repo we cover #1 and #3. 

```
forge test
```

or 

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test Coverage

```
forge coverage
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file.

- `PRIVATE_KEY`: The private key of your account.
  **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

2. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```
make deploy ARGS="--network sepolia"
```


## Scripts

After deploy to a testnet or local net, you can run the scripts. 

Using cast deployed locally example: 

```
cast send <ERC20_CONTRACT_ADDRESS> "transfer()"  --value 0.1ether --private-key <PRIVATE_KEY> --rpc-url $SEPOLIA_RPC_URL
```


## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see and output file called `.gas-snapshot`


# Formatting


To run code formatting:
```
forge fmt
```
