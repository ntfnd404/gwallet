# GWallet

Welcome!

GWallet is a minimalistic and pragmatist crossplatform lightweight opensource brainwallet for people that want to hold the most important cryptocurrencies in the same application with ease and peace of mind.

[![Licence](https://img.shields.io/github/license/diginex/geewallet.svg)](https://github.com/diginex/geewallet/blob/master/LICENCE.txt)

| Branch    | Description                                                                | CI status                                                                                                                                                                                                         |
| --------- | -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| oldstable | (v0.1.0.x) ETC & ETH support, console-based frontend, cold-storage support | Linux: [![Linux CI pipeline status badge](http://gitlab.com/DiginexGlobal/geewallet/badges/oldstable/build.svg)](https://gitlab.com/DiginexGlobal/geewallet/commits/oldstable)                                    |
| stable    | (v0.2.0.x) +BTC&LTC support (including SegWit & RBF support) + DAI (ERC20) | Linux: [![Linux CI pipeline status badge](http://gitlab.com/DiginexGlobal/geewallet/badges/stable/build.svg)](https://gitlab.com/DiginexGlobal/geewallet/commits/stable)                                          |
| master    | main branch where ongoing development takes place (unstable)               | Linux: [![Linux CI pipeline status badge](http://gitlab.com/DiginexGlobal/geewallet/badges/master/build.svg)](https://gitlab.com/DiginexGlobal/geewallet/commits/master)                                          |
|           |                                                                            | Windows: [![Windows CI pipeline status badge](https://dev.azure.com/diginex/geewallet/_apis/build/status/geewallet-master-build-and-test)](https://dev.azure.com/diginex/geewallet/_build/latest?definitionId=1)  |
| frontend  | +Xamarin.Forms frontends (now: Android & iOS & Gtk & Mac; soon: UWP)       | Linux: [![Linux CI pipeline status badge](http://gitlab.com/DiginexGlobal/geewallet/badges/frontend/build.svg)](https://gitlab.com/DiginexGlobal/geewallet/commits/frontend)                                      |

[![Balances mobile-page screenshot](https://raw.githubusercontent.com/diginex/geewallet/master/img/screenshots/mobile-balances.png)](https://raw.githubusercontent.com/diginex/geewallet/master/img/screenshots/mobile-balances.png)

## Principles

GWallet is a wallet that prioritizes convenience & security over privacy. Examples:

1. Convenience: it is a lightweight wallet (you don't need to download whole blockchains to use it, unlike with Bitcoin Core's wallet).
2. Convenience over privacy (I): it's a wallet that handle multiple cryptocurrencies, so its UX needs to be as generic as possible to accomodate them, therefore only contains minimal currency-specific features. For example, given that the concept of "change-addresses" doesn't exist in the Ethereum world (a concept initially thought to help privacy in the bitcoin world, but which doesn't achieve much of it in the end), then it is not used by GWallet even when sending bitcoin, to avoid cluttering the UI/UX with currency-specific features/complexities. We will still be investigating the support of more robust privacy features such as the ones provided by TumbleBit or ConfidentialTransactions.
3. Convenience over privacy (II): servers from other wallets' infrastructure is reused (e.g. Electrum's Stratum protocol), however TLS communication is still unsupported (this only hinders privacy but doesn't pose any security risk).
4. Security (I): GWallet is a desktop/mobile wallet, not an online/web wallet like others (e.g. web wallets are easy targets: https://twitter.com/myetherwallet/status/988830652526092288 ).
5. Security (II): GWallet has cold-storage support (you can run it in off-line mode and import/export transactions in JSON files), but not hardware wallet support. Remember, cold storage is not the same as 'hardware wallet'. GWallet is a software wallet, but which works in air-gapped devices (computers/smartphones) thanks to its cold-storage support, which means that it's safer than hardware wallets (after all, bugs and security issues are constantly being found on hardware wallets, e.g.: https://saleemrashid.com/2018/03/20/breaking-ledger-security-model/).
6. Convenience (II): there are no pre-generated seeds, geewallet is a brainwallet that uses your passphrase as a seed phrase, so that you don't need to keep backups anymore (and if you have any doubt about the security of this, understand that a hacker will always want to try to solve the WarpWallet challenge rather than target you directly).

In the development side of things, we advocate for simplicity:
1. We will always be standing in the shoulders of giants, which means that we should not reinvent the wheel, thus we have a complete commitment to opensource as way of evolving the product and achieving the maximum level of security/auditability; unlike other multi-currency wallets (cough... Jaxx ...cough).
2. We will try to only add new features to the UX/UI that can be supported by all currencies that we support, and we will prioritize new features (Layer2: micropayments) over support for new currencies (no shitcoins thanks).
3. Thanks to our usage of Xamarin.Forms toolkit, our frontends are based on a single codebase, instead of having to repeat logic for each platform.

## Features

Comparing our product to other wallets in terms of features, we would want to highlight the following:

| Wallet\Feature | Multi-currency | Opensource | Cold Storage | Brain seed | Truly crossplatform* |
| -------------- | -------------- | ---------- | ------------ | ---------- | -------------------- |
| Copay/Bitpay   | No             | **Yes**    | No           | No         | **Yes**              |
| Electrum       | No             | **Yes**    | **Yes**      | No         | No                   |
| Bread          | **Yes**        | **Yes**    | **Yes**      | No         | **Yes**              |
| Samourai       | No             | **Yes**    | **Yes**      | No         | No                   |
| Jaxx           | **Yes**        | No         | No           | No         | **Yes**              |
| Coinomi        | **Yes**        | No         | No           | No         | **Yes**              |
| ParitySigner   | No             | **Yes**    | **Yes**      | No         | **Yes**              |
| imToken        | **Yes**        | No         | **Yes**      | No         | No                   |
| status.im      | No             | **Yes**    | No           | No         | **Yes**              |
| Edge           | **Yes**        | **Yes**?   | No           | No         | No                   |
| WarpWallet     | No             | **Yes**    | No           | **Yes**    | No                   |
| <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/geewallet.svg?sanitize=true" /> | <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/Yes.svg?sanitize=true" /> | <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/Yes.svg?sanitize=true" /> | <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/Yes.svg?sanitize=true" /> | <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/Yes.svg?sanitize=true" /> | <img src="https://raw.githubusercontent.com/diginex/geewallet/frontend/img/markdown/Yes.svg?sanitize=true" /> |

*=With truly crossplatform we mean Mobile (both Android & iPhone) & Desktop (main OSs: Linux, macOS & Windows)

As you can see, geewallet is a good mixup of good features, which others never manage to get together in the same app. I should add to this that geewallet's future maintainability is very high due to:
- Using a functional programming language.
- Having lots of automated tests.
- Employing a single code base for all frontends, requiring much less manpower and specific expertise.


## Roadmap

This list is the (intended) order of preference for new features:

- Xamarin.Forms frontends (in progress, see the 'frontend' branch)...
- ETH/ETC state channel support.
- Raiden support.
- Bitcoin/Litecoin payment channels support.
- Lightning support (upgrading to NBitcoin 4.0.0.12 to be protected from malleability).
- Payment channels support.
- Mac/Windows CI support via Travis & AppVeyor respectively.
- Flatpak & snap packaging.
- Paranoid-build mode (using git submodules instead of nuget deps), depending on this RFE (https://github.com/dotnet/sdk/issues/1151) or using any workaround mentioned there.
- Fee selection for custom priority.
- Multi-sig support.
- Use bits instead of BTC as default unit.
(See: https://www.reddit.com/r/Bitcoin/comments/7hsq6m/symbol_for_a_bit_0000001btc/ )
- MimbleWimble support?
- Threshold signatures.
- ETH gas station (to pay for token transactions with token value instead of ETH).
- Decentralized naming resolution? (BNS/ENS/OpenCAP/...)
- Decentralized currency exchange? or crosschain atomic swaps?
- Tumblebit support?

## Dev roadmap

(Only intelligible if you're a GWallet developer):
- Switch to use https://github.com/madelson/MedallionShell in Infra.fs (we might want to use paket instead of nuget for this, as it's friendlier to .fsx scripts, see https://cockneycoder.wordpress.com/2017/08/07/getting-started-with-paket-part-1/, or wait for https://github.com/Microsoft/visualfsharp/pull/5850).
- Refactor bitcoin support to use NBitcoin's TransactionBuilder.
- Study the need for ConfigureAwait(false) in the backend (or similar & easier approaches such as https://blogs.msdn.microsoft.com/benwilli/2017/02/09/an-alternative-to-configureawaitfalse-everywhere/ or https://github.com/Fody/ConfigureAwait ).

## Anti-roadmap

Things that are not currently on our roadmap:

- ZCash/Dash/Monero support (I don't like the trusted setup of the first, plus the others use substandard
privacy solutions which in my opinion will all be surpassed by MimbleWimble).
- BCash (as it's less evolved, technically speaking; I don't want to deal with transaction malleability
or lack of Layer2 scaling).

# How to compile/install/use?

The recommended way is to install the software system wide, like this:

```
./configure.sh --prefix=/usr
make
sudo make install
```

After that you can call `gwallet` directly.


## Feedback

If you want to accelerate development/maintenance, please donate at... TBD.
