# aptos cli使用笔记-UBUNTU

参考链接：https://aptos.dev/nodes/local-testnet/using-cli-to-run-a-local-testnet

## 0x1ENV:

Ubuntu-22.04

devnet

https://explorer.aptoslabs.com/account/0xc3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9/resources

https://github.com/aptos-labs/aptos-core

https://github.com/aptoseden/move-tutorial/blob/main/sdk-examle/aptos/deploy-counter-to-devnet.md

https://github.com/aptoseden/move-tutorial/blob/main/sdk-examle/aptos/use-cli.md

## ox2 Download aptos cli

```
wget https://github.com/aptos-labs/aptos-core/releases/download/aptos-cli-v1.0.5/aptos-cli-1.0.5-Ubuntu-22.04-x86_64.zip
```

## 0x3 Setup

```
unzip aptos-cli-0.3.2-MacOSX-x86_64.zip
sudo mv aptos /usr/bin/
zdzd@oracle:~/Desktop$ aptos info
{
  "Result": {
    "build_branch": "main",
    "build_cargo_version": "cargo 1.66.1 (ad779e08b 2023-01-10)",
    "build_commit_hash": "d57b97bae0b64b617869f2ff26e749e503848846",
    "build_is_release_build": "true",
    "build_os": "linux-x86_64",
    "build_pkg_version": "1.0.5",
    "build_profile_name": "cli",
    "build_rust_channel": "1.66.1-x86_64-unknown-linux-gnu",
    "build_rust_version": "rustc 1.66.1 (90743e729 2023-01-10)",
    "build_tag": "",
    "build_time": "2023-02-01 00:55:54 +00:00",
    "build_using_tokio_unstable": "true"
  }
}
```



## 0x4 Init

```
zdzd@oracle:~/move$ export PROFILE=zdzd
zdzd@oracle:~/move$ aptos init --profile $PROFILE
Configuring for profile zdzd
Choose network from [devnet, testnet, mainnet, local, custom | defaults to devnet]
devnet
Enter your private key as a hex literal (0x...) [Current: None | No input: Generate new key (or keep one if present)]

No key given, generating key...
Account c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9 doesn't exist, creating it and funding it with 100000000 Octas
Account c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9 funded successfully

---
Aptos CLI is now set up for account c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9 as profile zdzd!  Run `aptos --help` for more information about commands
{
  "Result": "Success"
}

```

## 0x5 Move Complie

```
aptos move compile --package-dir hello_blockchain --named-addresses hello_blockchain=$PROFILE 
Compiling, may take a little while to download git dependencies...
INCLUDING DEPENDENCY AptosFramework
INCLUDING DEPENDENCY AptosStdlib
INCLUDING DEPENDENCY MoveStdlib
BUILDING Examples
{
  "Result": [
    "c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9::message"
  ]
}

```

## 0x6 Move Publish

```
aptos move publish --package-dir hello_blockchain --named-addresses hello_blockchain=$PROFILE  --profile $PROFILE
Compiling, may take a little while to download git dependencies...
INCLUDING DEPENDENCY AptosFramework
INCLUDING DEPENDENCY AptosStdlib
INCLUDING DEPENDENCY MoveStdlib
BUILDING Examples
package size 1734 bytes
Do you want to submit a transaction for a range of [748800 - 1123200] Octas at a gas unit price of 100 Octas? [yes/no] >
yes
{
  "Result": {
    "transaction_hash": "0xd742f3f40c4991adae974e47395414513b1c85bd5cb27eb9c5475dcb4ff4fe51",
    "gas_used": 7488,
    "gas_unit_price": 100,
    "sender": "c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9",
    "sequence_number": 0,
    "success": true,
    "timestamp_us": 1675651932035249,
    "version": 11743617,
    "vm_status": "Executed successfully"
  }
}
```

## 0x7 Move Run

```
aptos move run --function-id c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9::message::set_message --args string:Hello-zdzd-changed!  --profile $PROFILE
message::set_message --args string:Hello-zdzd!  --profile $PROFILE
Do you want to submit a transaction for a range of [74700 - 112000] Octas at a gas unit price of 100 Octas? [yes/no] >
yes
{
  "Result": {
    "transaction_hash": "0x6158d06cb349655340c9cc7ec4dfe5847be2f8a6f30aae72d57ca0347ae18b41",
    "gas_used": 782,
    "gas_unit_price": 100,
    "sender": "c3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9",
    "sequence_number": 1,
    "success": true,
    "timestamp_us": 1675652658634389,
    "version": 11748971,
    "vm_status": "Executed successfully"
  }
}

```

## 0x8 Move Test

```
zdzd@oracle:~/move/aptos-core/aptos-move/move-examples/hello_blockchain$ aptos move test --named-addresses hello_blockchain=$PROFILE
INCLUDING DEPENDENCY AptosFramework
INCLUDING DEPENDENCY AptosStdlib
INCLUDING DEPENDENCY MoveStdlib
BUILDING Examples
Running Move unit tests
[ PASS    ] 0xc3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9::message_tests::sender_can_set_message
[ PASS    ] 0xc3c3c19fe405c4424b3ce6e76e4768f49bf326588f126dbb977b3ebdbc2209c9::message::sender_can_set_message
Test result: OK. Total tests: 2; passed: 2; failed: 0
{
  "Result": "Success"
}

```

