# SplitMain

*0xSplits*

> SplitMain

A composable and gas-efficient protocol for deploying splitter contracts.

*Split recipients, ownerships, and keeper fees are stored onchain as calldata &amp; re-passed as args / validated via hashing when needed. Each split gets its own address &amp; proxy for maximum composability with other contracts onchain. For these proxies, we extended EIP-1167 Minimal Proxy Contract to avoid `DELEGATECALL` for `receive()` to accept hard gas-capped `sends` &amp; `transfers`.*

## Methods

### PERCENTAGE_SCALE

```solidity
function PERCENTAGE_SCALE() external view returns (uint256)
```

constant to scale uints into percentages (1e6 == 100%)




#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined

### acceptOwnership

```solidity
function acceptOwnership(address split) external nonpayable
```

Accepts transfer of the controlling address of mutable split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of mutable split to accept ownership transfer for

### cancelOwnershipTransfer

```solidity
function cancelOwnershipTransfer(address split) external nonpayable
```

Cancels transfer of the controlling address of mutable split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of mutable split to cancel ownership transfer for

### createSplit

```solidity
function createSplit(address[] accounts, uint32[] percentAllocations, uint32 splitterFee, address owner) external nonpayable returns (address split)
```

Creates a new split with recipients `accounts` with ownerships `percentAllocations`, a keeper fee for splitting of `splitterFee` and the controlling address `owner`



#### Parameters

| Name | Type | Description |
|---|---|---|
| accounts | address[] | Ordered, unique list of addresses with ownership in the split
| percentAllocations | uint32[] | Percent allocations associated with each address
| splitterFee | uint32 | Keeper fee paid by split to cover gas costs of distribution
| owner | address | Controlling address (0x0 if immutable)

#### Returns

| Name | Type | Description |
|---|---|---|
| split | address | undefined

### getERC20Balance

```solidity
function getERC20Balance(address split, contract ERC20 token) external view returns (uint256)
```

Returns the current erc20Balance of split `split` and erc20 token `token`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Split to return balance for
| token | contract ERC20 | Token to return balance for

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined

### getETHBalance

```solidity
function getETHBalance(address split) external view returns (uint256)
```

Returns the current eth balance of split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Split to return eth balance for

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | uint256 | undefined

### getHash

```solidity
function getHash(address split) external view returns (bytes32)
```

Returns the current hash of split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Split to return hash for

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | bytes32 | undefined

### getNewPotentialOwner

```solidity
function getNewPotentialOwner(address split) external view returns (address)
```

Returns the current newPotentialOwner of split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Split to return newPotentialOwner for

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined

### getOwner

```solidity
function getOwner(address split) external view returns (address)
```

Returns the current owner of split `split`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Split to return owner for

#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined

### makeSplitImmutable

```solidity
function makeSplitImmutable(address split) external nonpayable
```

Turns mutable split `split` immutable



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of mutable split to turn immutable

### predictSplitAddress

```solidity
function predictSplitAddress(address[] accounts, uint32[] percentAllocations, uint32 splitterFee) external view returns (address split)
```

Predicts the address for an immutable split created with recipients `accounts` with ownerships `percentAllocations` and a keeper fee for splitting of `splitterFee`



#### Parameters

| Name | Type | Description |
|---|---|---|
| accounts | address[] | Ordered, unique list of addresses with ownership in the split
| percentAllocations | uint32[] | Percent allocations associated with each address
| splitterFee | uint32 | Keeper fee paid by split to cover gas costs of distribution

#### Returns

| Name | Type | Description |
|---|---|---|
| split | address | undefined

### splitBalanceFor

```solidity
function splitBalanceFor(address split, address[] accounts, uint32[] percentAllocations, uint32 splitterFee) external nonpayable
```

Splits the eth balance for split `split`

*`accounts`, `percentAllocations`, and `splitterFee` are verified by hashing &amp; comparing to the hash in storage associated with split `split`*

#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of split to split balance for
| accounts | address[] | Ordered, unique list of addresses with ownership in the split
| percentAllocations | uint32[] | Percent allocations associated with each address
| splitterFee | uint32 | Keeper fee paid by split to cover gas costs of distribution

### splitERC20BalanceFor

```solidity
function splitERC20BalanceFor(address split, contract ERC20 token, address[] accounts, uint32[] percentAllocations, uint32 splitterFee) external nonpayable
```

Splits the ERC20 `token` balance for split `split`

*`accounts`, `percentAllocations`, and `splitterFee` are verified by hashing &amp; comparing to the hash in storage associated with split `split`*

#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of split to split balance for
| token | contract ERC20 | Address of ERC20 to split balance for
| accounts | address[] | Ordered, unique list of addresses with ownership in the split
| percentAllocations | uint32[] | Percent allocations associated with each address
| splitterFee | uint32 | Keeper fee paid by split to cover gas costs of distribution

### transferOwnership

```solidity
function transferOwnership(address split, address newOwner) external nonpayable
```

Begins transfer of the controlling address of mutable split `split` to `newOwner`

*Two-step ownership transfer inspired by [dharma](https://github.com/dharma-eng/dharma-smart-wallet/blob/master/contracts/helpers/TwoStepOwnable.sol)*

#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | Address of mutable split to transfer control for
| newOwner | address | Address to begin transferring control to

### updateSplit

```solidity
function updateSplit(address split, address[] accounts, uint32[] percentAllocations, uint32 splitterFee) external nonpayable
```

Updates an existing split with recipients `accounts` with ownerships `percentAllocations` and a keeper fee for splitting of `splitterFee`



#### Parameters

| Name | Type | Description |
|---|---|---|
| split | address | undefined
| accounts | address[] | Ordered, unique list of addresses with ownership in the split
| percentAllocations | uint32[] | Percent allocations associated with each address
| splitterFee | uint32 | Keeper fee paid by split to cover gas costs of distribution

### walletImplementation

```solidity
function walletImplementation() external view returns (address)
```

address of wallet implementation for split proxies




#### Returns

| Name | Type | Description |
|---|---|---|
| _0 | address | undefined

### withdrawFor

```solidity
function withdrawFor(address account, bool eth, contract ERC20[] tokens) external nonpayable
```

Withdraw eth &amp;/ ERC20 balances for account `account`



#### Parameters

| Name | Type | Description |
|---|---|---|
| account | address | undefined
| eth | bool | Bool of whether to withdraw eth
| tokens | contract ERC20[] | Addresses of ERC20s to withdraw for



## Events

### CreateSplit

```solidity
event CreateSplit(address indexed split)
```

emitted after each successful split creation



#### Parameters

| Name | Type | Description |
|---|---|---|
| split `indexed` | address | undefined |

### OwnershipTransfer

```solidity
event OwnershipTransfer(address indexed split, address indexed previousOwner, address indexed newOwner)
```

emitted after each successful split ownership transfer



#### Parameters

| Name | Type | Description |
|---|---|---|
| split `indexed` | address | undefined |
| previousOwner `indexed` | address | undefined |
| newOwner `indexed` | address | undefined |

### SplitBalance

```solidity
event SplitBalance(address indexed split, uint256 amount)
```

emitted after each successful ETH balance split



#### Parameters

| Name | Type | Description |
|---|---|---|
| split `indexed` | address | undefined |
| amount  | uint256 | undefined |

### SplitERC20Balance

```solidity
event SplitERC20Balance(address indexed split, contract ERC20 token, uint256 amount)
```

emitted after each successful ERC20 balance split



#### Parameters

| Name | Type | Description |
|---|---|---|
| split `indexed` | address | undefined |
| token  | contract ERC20 | undefined |
| amount  | uint256 | undefined |

### UpdateSplit

```solidity
event UpdateSplit(address indexed split)
```

emitted after each successful split update



#### Parameters

| Name | Type | Description |
|---|---|---|
| split `indexed` | address | undefined |

### Withdrawal

```solidity
event Withdrawal(address indexed account, bool eth, contract ERC20[] tokens, uint256[] amounts)
```

emitted after each successful withdrawal



#### Parameters

| Name | Type | Description |
|---|---|---|
| account `indexed` | address | undefined |
| eth  | bool | undefined |
| tokens  | contract ERC20[] | undefined |
| amounts  | uint256[] | undefined |



## Errors

### ETHWithdrawalFailed

```solidity
error ETHWithdrawalFailed(uint256 amount)
```

ETH withdrawal of `amount` failed



#### Parameters

| Name | Type | Description |
|---|---|---|
| amount | uint256 | undefined |

### InvalidNewOwner

```solidity
error InvalidNewOwner(address newOwner)
```

Invalid new controlling address `newOwner` for mutable split



#### Parameters

| Name | Type | Description |
|---|---|---|
| newOwner | address | undefined |

### InvalidSplit__AccountsAndAllocationsMismatch

```solidity
error InvalidSplit__AccountsAndAllocationsMismatch(uint256 accountsLength, uint256 allocationsLength)
```

Array lengths of accounts &amp; percentAllocations don&#39;t match (`accountsLength` != `allocationsLength`)



#### Parameters

| Name | Type | Description |
|---|---|---|
| accountsLength | uint256 | undefined |
| allocationsLength | uint256 | undefined |

### InvalidSplit__AccountsOutOfOrder

```solidity
error InvalidSplit__AccountsOutOfOrder(uint256 index)
```

Invalid accounts ordering at `index`



#### Parameters

| Name | Type | Description |
|---|---|---|
| index | uint256 | undefined |

### InvalidSplit__AllocationMustBePositive

```solidity
error InvalidSplit__AllocationMustBePositive(uint256 index)
```

Invalid percentAllocation of zero at `index`



#### Parameters

| Name | Type | Description |
|---|---|---|
| index | uint256 | undefined |

### InvalidSplit__InvalidAllocationsSum

```solidity
error InvalidSplit__InvalidAllocationsSum(uint32 allocationsSum)
```

Invalid percentAllocations sum `allocationsSum` must equal `PERCENTAGE_SCALE`



#### Parameters

| Name | Type | Description |
|---|---|---|
| allocationsSum | uint32 | undefined |

### InvalidSplit__InvalidHash

```solidity
error InvalidSplit__InvalidHash(bytes32 hash)
```

Invalid hash `hash` from split data (accounts, percentAllocations, splitterFee)



#### Parameters

| Name | Type | Description |
|---|---|---|
| hash | bytes32 | undefined |

### InvalidSplit__InvalidSplitterFee

```solidity
error InvalidSplit__InvalidSplitterFee(uint32 splitterFee)
```

Invalid splitterFee `splitterFee` cannot be greater than 10% (1e5)



#### Parameters

| Name | Type | Description |
|---|---|---|
| splitterFee | uint32 | undefined |

### InvalidSplit__TooFewAccounts

```solidity
error InvalidSplit__TooFewAccounts(uint256 accountsLength)
```

Invalid number of accounts `accountsLength`, must have at least 2



#### Parameters

| Name | Type | Description |
|---|---|---|
| accountsLength | uint256 | undefined |

### Unauthorized

```solidity
error Unauthorized(address sender)
```

Unauthorized sender `sender`



#### Parameters

| Name | Type | Description |
|---|---|---|
| sender | address | undefined |

