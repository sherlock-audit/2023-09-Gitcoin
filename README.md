
# Gitcoin Allo contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
All EVM compatible chains + Zkync Era
___

### Q: Which ERC20 tokens do you expect will interact with the smart contracts? 
All 
___

### Q: Which ERC721 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Which ERC777 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Are there any FEE-ON-TRANSFER tokens interacting with the smart contracts?

Yes. When funding a pool on Allo.sol
___

### Q: Are there any REBASING tokens interacting with the smart contracts?

None
___

### Q: Are the admins of the protocols your contracts integrate with (if any) TRUSTED or RESTRICTED?
RESTRICTED
___

### Q: Is the admin/owner of the protocol/contracts TRUSTED or RESTRICTED?
TRUSTED

The contracts are upgradable and the admin is trusted. 

The owner of Allo.sol can
- recover funds from Allo.sol 
- flag contracts as cloneable 
- set the base fee, percent fee , registry address and treasury address

The owner of Registry.sol can recover funds from Registry.sol 

___

### Q: Are there any additional protocol roles? If yes, please explain in detail:
* **Profile Owners:** Users who create profiles using the `Registry` contract. These profiles are central to protocol interactions, offering a unique identity for users and enabling secure external calls through the `Anchor` contract.
    
* **Profile Member:** Members of a Registry profile have specific access rights as defined by the profile's owner.

* **Allo Owner:** Individuals who control the `Allo` contract, possessing the authority to manage fund recovery, fee parameters, and treasury addresses. Their role is pivotal in ensuring the protocol's financial stability.
  

* **Pool Creator** A user who can create new pools using custom or cloneable strategies. They can specify metadata, strategy addresses, managers, and other parameters during pool creation.
    
* **Pool Administrator** Users with administrative control over specific pools. They can manage pool managers, enabling effective pool governance.
    
* **Pool Manager** Users who manage funds within specific pools. They can allocate and distribute funds according to the pool's strategy
___

### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
ERC20, EIP-712
___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
Fee skirting where pool manager directly fund the pool without paying the fees
___

### Q: Please provide links to previous audits (if any).
New
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)?
- Metadata struct references IPFS 
- DonationVotingMerkleDistributionBaseMerkle has calculations which happens off-chain based on which a merkle root is generated and uploaded. The pool manager is a trusted role and is expected to use https://github.com/gitcoinco/pluralistic.js
___

### Q: In case of external protocol integrations, are the risks of external contracts pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality.
No
___

### Q: Do you expect to use any of the following tokens with non-standard behaviour with the smart contracts?
Yes as we support all ERC20 tokens.
___

### Q: Add links to relevant protocol resources
- https://docs.allo.gitcoin.co/
- https://github.com/allo-protocol/allo-v2/blob/main/audit-resources.md
___



# Audit scope


[allo-v2 @ 0b881ef4a0013d2809374c9ea69f4cf1288dfe62](https://github.com/allo-protocol/allo-v2/tree/0b881ef4a0013d2809374c9ea69f4cf1288dfe62)
- [allo-v2/contracts/core/Allo.sol](allo-v2/contracts/core/Allo.sol)
- [allo-v2/contracts/core/Anchor.sol](allo-v2/contracts/core/Anchor.sol)
- [allo-v2/contracts/core/Registry.sol](allo-v2/contracts/core/Registry.sol)
- [allo-v2/contracts/core/interfaces/IAllo.sol](allo-v2/contracts/core/interfaces/IAllo.sol)
- [allo-v2/contracts/core/interfaces/IRegistry.sol](allo-v2/contracts/core/interfaces/IRegistry.sol)
- [allo-v2/contracts/core/interfaces/IStrategy.sol](allo-v2/contracts/core/interfaces/IStrategy.sol)
- [allo-v2/contracts/core/libraries/Clone.sol](allo-v2/contracts/core/libraries/Clone.sol)
- [allo-v2/contracts/core/libraries/Errors.sol](allo-v2/contracts/core/libraries/Errors.sol)
- [allo-v2/contracts/core/libraries/Metadata.sol](allo-v2/contracts/core/libraries/Metadata.sol)
- [allo-v2/contracts/core/libraries/Native.sol](allo-v2/contracts/core/libraries/Native.sol)
- [allo-v2/contracts/core/libraries/Transfer.sol](allo-v2/contracts/core/libraries/Transfer.sol)
- [allo-v2/contracts/strategies/BaseStrategy.sol](allo-v2/contracts/strategies/BaseStrategy.sol)
- [allo-v2/contracts/strategies/donation-voting-merkle-base/DonationVotingMerkleDistributionBaseStrategy.sol](allo-v2/contracts/strategies/donation-voting-merkle-base/DonationVotingMerkleDistributionBaseStrategy.sol)
- [allo-v2/contracts/strategies/donation-voting-merkle-distribution-direct-transfer/DonationVotingMerkleDistributionDirectTransferStrategy.sol](allo-v2/contracts/strategies/donation-voting-merkle-distribution-direct-transfer/DonationVotingMerkleDistributionDirectTransferStrategy.sol)
- [allo-v2/contracts/strategies/donation-voting-merkle-distribution-vault/DonationVotingMerkleDistributionVaultStrategy.sol](allo-v2/contracts/strategies/donation-voting-merkle-distribution-vault/DonationVotingMerkleDistributionVaultStrategy.sol)
- [allo-v2/contracts/strategies/qv-base/QVBaseStrategy.sol](allo-v2/contracts/strategies/qv-base/QVBaseStrategy.sol)
- [allo-v2/contracts/strategies/qv-simple/QVSimpleStrategy.sol](allo-v2/contracts/strategies/qv-simple/QVSimpleStrategy.sol)
- [allo-v2/contracts/strategies/rfp-committee/RFPCommitteeStrategy.sol](allo-v2/contracts/strategies/rfp-committee/RFPCommitteeStrategy.sol)
- [allo-v2/contracts/strategies/rfp-simple/RFPSimpleStrategy.sol](allo-v2/contracts/strategies/rfp-simple/RFPSimpleStrategy.sol)

