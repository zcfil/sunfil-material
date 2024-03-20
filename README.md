# sunfil-material
合约项目：https://github.com/zcfil/sunfil.git  

前端项目：https://github.com/zcfil/sunfil-web.git  

后端项目：https://github.com/zcfil/sunfil-server.git  
	

## sunfil简介

    sunfil属于一个流动质押平台，节点拥有者可以抵押受益人或者owner地址获得对应的借款额度，存款方只要有FIL都可以加入。
    理论上贷款利率以及存款利率是交给市场决定的，通过资金池的利用率计算出实际利率8~30%左右。资金池利用率越高，相对应的利息也就越高，
    迫使贷方还币以及吸引更多FIL加入以缓解资金池压力。对于持续掉算力扣币节点到达一定比率会触发投票机制，用于决定是否强制终止该节点扇区
    用于偿还其所欠的债务，投票权重由存币者比重决定，也就是一切行为交给市场裁决。
    
## sunfil合约组成
    
    sunfil池子由8个合约组成，分别为：资金池合约（sunPond.sol），借贷合约（DebtTokens.sol），计算合约（InterestRateFormula.sol），节点信息管理合约（manageNode.sol），
    节点操作合约（opNode.sol），利率合约（rate.sol），质押合约（StakingPool.sol），投票合约（vote.sol）

### sunPond合约：
    1.管理资金池的支付权限如opNode合约的借贷、还款、节点提现功能，StakingPool合约的存款、取款等功能。
    2.管理资金池的地址权限如manageNode合约的入职、离职、修改操作人等功能，opNode合约的修改worker、control地址等功能。
    也就是说：
    sunPond合约部署一起来以后要将StakingPool合约、opNode合约、manageNode合约的部署地址分别传入sunPond合约'GrantPayableAuthority'接口，用以获取支付权限
    sunPond合约部署一起来以后要将StakingPool合约、opNode合约、manageNode合约的部署地址分别传入sunPond合约'GrantOpAuthority'接口，用以地址操作权限

### manageNode合约：
    一个加入sunfil节点名单，包含节点入职、离职、修改操作人等操作，管理着所有加入池子节点信息。

### opNode合约：
    一个sunfil节点操作者，进行借贷、还款、修改worker、control地址等操作。

### DebtTokens合约：
    一个借款账本，用以记录opNode合约借贷、还款等信息，包括对应借贷信息查询。

### StakingPool合约：
    一个存款账本，储户进行质押、解质押、质押信息查询等操作，保存着储户存款信息的一个合约。

### rate合约：
    一个利率设置者，设置平台基础值、贷款、存款、负债、杠杆、年化等相关利率计算。虽然说利率是交给市场的，但是利率合约不存任何数据，也是可以随时替换的。

### InterestRateFormula合约：
    一个利率计算公式，用以计算缩放因子相关的方法，不存任何数据也是可以随时替换的

### vote合约:
    清算投票，获取投票提案、固化投票人及投票权重、参与投票等操作。

# English
    Sunfil is a mobile pledge platform, where node owners can mortgage the beneficiary or owner's address to obtain the corresponding loan amount. Depositors can join as long as they have FIL.

    In theory, loan interest rates and deposit interest rates are determined by the market, and the actual interest rate is calculated to be around 8-30% based on the utilization rate of the fund pool. The higher the utilization rate of the fund pool, the higher the corresponding interest rate,

    Forcing lenders to repay coins and attracting more FILs to join to alleviate the pressure on the fund pool. A voting mechanism will be triggered when a certain percentage of continuously losing computing power and coin deduction nodes are reached, which is used to determine whether to forcibly terminate the sector of the node

    Used to repay its debts, the voting weight is determined by the proportion of depositors, which means all actions are subject to market decision-making.

## project
contract：https://github.com/zcfil/sunfil.git
web：https://github.com/zcfil/sunfil-web.git
server：https://github.com/zcfil/sunfil-server.git

## sunfil introduction

    The sunfil pool consists of 8 contracts, namely: fund pool contract (sunPond. sol), loan contract (DebtTokens. sol), calculation contract (InterestRateFormula. sol), and node information management contract (manageNode. sol),

    Node operation contract (opNode. sol), interest rate contract (rate. sol), staking contract (StackingPool. sol), voting contract (vote. sol)


### sunPond：
    1. Manage the payment permissions of the fund pool, such as the borrowing, repayment, and node withdrawal functions of opNode contracts, and the deposit and withdrawal functions of StackingPool contracts.

    2. Manage the address permissions of the fund pool, such as the functions of joining, leaving, and modifying operators in the management node contract, as well as the functions of modifying workers and controlling addresses in the opNode contract.

    That is to say:

    After deploying the sunPond contract, the deployment addresses of the StackingPool contract, opNode contract, and manageNode contract should be passed into the 'GrantPayableAuthority' interface of the sunPond contract to obtain payment permissions

    After the deployment of the sunPond contract, the deployment addresses of the StackingPool contract, opNode contract, and manageNode contract should be passed into the 'GrantOpAuthority' interface of the sunPond contract, respectively, to enable address operation permissions

### manageNode：
    A list of Sunfil nodes that includes operations such as node onboarding, resignation, and modifying operators, managing all information related to joining pool child nodes.

### opNode：
    A Sunfil node operator performs operations such as borrowing and lending, repayment, modifying workers, and controlling addresses.

### DebtTokens：
    A loan ledger used to record information such as opNode contract loans and repayments, including corresponding loan information queries.

### StakingPool：
    A deposit ledger is a contract in which depositors perform operations such as pledging, de pledging, and querying pledge information, and store their deposit information.

### rate：
    An interest rate setter who sets platform base values, loans, deposits, liabilities, leverage, annualized, and other related interest rate calculations. Although interest rates are handed over to the market, interest rate contracts do not hold any data and can be replaced at any time.

### InterestRateFormula：
    An interest rate calculation formula used to calculate scaling factor related methods, which can be replaced at any time without storing any data

### vote:
    Clearing voting, obtaining voting proposals, solidifying voters and voting weights, participating in voting, and other operations.