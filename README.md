# Pallet assets chain extension

> :warning: **Chain extension contains vulnerabilities**: Don't use it in the
> production. Fixing vulnerabilities requires changes on `pallet-assets` to expose
> some data about the owner, admin, issuer, etc.

The repository contains full implementation(`ink` and `substrate` parts) of the `pallet-assets`
chain extension.

The crate can be imported on the parachain side with `substrate` and `substrate-std` features:

```
...

# Contracts specific packages
pallet-contracts = { git = "https://github.com/paritytech/substrate", package = "pallet-contracts", default-features = false }
pallet-contracts-primitives = { git = "https://github.com/paritytech/substrate", package = "pallet-contracts-primitives", default-features = false }
pallet-contracts-rpc-runtime-api = { git = "https://github.com/paritytech/substrate", package = "pallet-contracts-rpc-runtime-api", default-features = false }

# Chain extension for `pallet-assets`
pallet-assets = { git = "https://github.com/paritytech/substrate", package = "pallet-assets", default-features = false }
pallet-assets-chain-extension = { git = "https://github.com/727-Ventures/pallet-assets-chain-extension", default-features = false, features = ["substrate"]  }
# ^^^^^^^^^^^^^^^^^^^^^^^^^^^
# Here imported with `substrate` feature

...


std = [
	...
	"pallet-assets/std",
	"pallet-assets-chain-extension/substrate-std", # <---- Here impoted with `substrate-std` feature
]

...
```

[Example of how to enable](https://github.com/paritytech/substrate-contracts-node/pull/146)

The crate can be imported on the smart contract side with `ink` and `ink-std` features:

```
...

# Ink deps
ink = { version = "~4.0.0-beta", default-features = false }

pallet-assets-chain-extension = { git = "https://github.com/727-Ventures/pallet-assets-chain-extension", default-features = false, features = ["ink"]  }
# ^^^^^^^^^^^^^^^^^^^^^^^^^^^
# Here imported with `ink` feature

...

std = [
	...
	"pallet-assets-chain-extension/ink-std", # <---- Here impoted with `ink-std` feature
]

...
```

[Example of how to use](https://github.com/Supercolony-net/openbrush-contracts/pull/168)