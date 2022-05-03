# Create Task >>>>
## ETH >> BNB
**Step1**
 1. [user]On ethereum network
 2. [user]Start to create a Lucks
 2. [user]Select a NFT (ethereum)
 3. [user]Input settings
 4. [system]Estimate Gas Fee --> *BridgeLucks(quoteLayerZeroFee)*
 4. [user]Approval NFT collection --> *ProxyNFTStation*
 5. [user]Submit Tx --> *ExecuteLucks(createTask)*
 6. [ExecuteLucks] Input datas basic check
 7. [ExecuteLucks] Check & Depoist & Transfer NFT to *ProxyNFTStation*
 8. [ExecuteLucks] Call bridge.createTask --> *BridgeLucks*
 9. [BridgeLucks] Send message to BNBChain via layerzero
 10. [system]Done. wait for tx finish.
 
**Step2**
 1. [BridgeLucks]On BNBChain network
 2. [BridgeLucks]Recieve remote message, invokeCreateTask --> *ExecuteLucks*
 3. [ExecuteLucks]Create task on BNBChain
 4. [ExecuteLucks]Done


 ## BNB >> BNB
**Step1**
 1. [user]On BNBChain network
 2. [user]Start to create a Lucks
 2. [user]Select a NFT (BNBChain)
 3. [user]Input settings
 4. [system]Estimate Gas Fee --> *BridgeLucks(quoteLayerZeroFee)*
 4. [user]Approval NFT collection --> *ProxyNFTStation*
 5. [user]Submit Tx --> *ExecuteLucks(createTask)*
 6. [ExecuteLucks] Input datas basic check
 7. [ExecuteLucks] Check & Depoist & Transfer NFT to *ProxyNFTStation*
 8. [ExecuteLucks] Call createTaskLocal
 9. [system]Done. wait for tx finish.



 # Join Task >>>>
 1. [user]Only on BNBChain network
 2. [user]Select a Task to Join (BNBChain)
 3. [user]Submit Tx --> *ExecuteLucks(joinTask)*
 4. [ExecuteLucks] Send Payment --> *ProxyTokenStation*

  # Cancel Task >>>>
  ## ETH -> BNB
  **Step1**
 1. [user]On ethereum network
 2. [user]Select a Task to Cancel (BNBChain)
 3. [system]Estimate Gas Fee --> *BridgeLucks(quoteLayerZeroFee)*
 4. [user]Submit Tx --> *ExecuteLucks(cancelTask)*
 5. [ExecuteLucks] Check Locked NFT --> *ProxyNFTStation*
 8. [ExecuteLucks] Call cancelTaskLocal --> *BridgeLucks*
 9. [BridgeLucks] Send message to BNBChain via layerzero
 10. [ExecuteLucks] Unlock or Withdraw NFT --> *ProxyNFTStation*.
 11. [system]Done. wait for tx finish.

 **Step2**
 1. [BridgeLucks]On BNBChain network
 2. [BridgeLucks]Recieve remote message, invokeCancelTask --> *ExecuteLucks*
 3. [ExecuteLucks]Cancel task on BNBChain
 4. [ExecuteLucks]Done

## BNB >> BNB
**Step1**
 1. [user]On BNBChain network
 2. [user]Select a Task to Cancel (BNBChain)
 3. [system]Estimate Gas Fee --> *BridgeLucks(quoteLayerZeroFee)*
 4. [user]Submit Tx --> *ExecuteLucks(cancelTask)*
 5. [ExecuteLucks] Check Locked NFT --> *ProxyNFTStation*
 8. [ExecuteLucks] Call cancelTaskLocal
 10. [ExecuteLucks] Unlock or Withdraw NFT --> *ProxyNFTStation*.
 11. [system]Done. wait for tx finish.


# Close Task >>>>
## ETH -> BNB  or BNB -> BNB
**Step1**
 1. [user]On BNBChain network
 2. [user]Select a Task to Close (BNBChain)
 3. [user]Submit Tx --> *ExecuteLucks(closeTask)*
 4. [ExecuteLucks] Call closeTaskLocal
 5. [ExecuteLucks] Request VRF to drawing number --> *LucksVRF*
 6. [system]Done. wait for tx finish.

 **Step2**
 1. [LucksVRF]On BNBChain network
 2. [LucksVRF]Recieve ChainLink Callback, invoke PickWinner --> *ExecuteLucks*
 3. [ExecuteLucks]Done


 
# PickWinner >>>>
## ETH -> BNB  or BNB -> BNB
**Step1**
 1. [operator]Only On BNBChain network
 2. [operator]Select a Task to PickWinner (BNBChain)
 3. [operator]Submit Tx --> *ExecuteLucks(pickWinner)*
 4. [ExecuteLucks] Call pickWinnerLocal
 5. [ExecuteLucks] transferPayment to Seller & Winners --> *ProxyTokenStation*
 5. [ExecuteLucks] call bridge.transferNFTs to Winner --> *BridgeLucks*
 6. [system]Done. wait for tx finish.

 **Step2**
 1. [LucksVRF]On Ethereum network
 2. [BridgeLucks]Recieve remote message, invokeTransferNFTs --> *ExecuteLucks*
 3. [ExecuteLucks]transfer NFTs ownership to Winner --> *ProxyNFTStation*
 4. [ExecuteLucks]Done

