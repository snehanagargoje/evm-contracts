“This repository contains my practice smart contracts and EVM experiments.”
# EVM Practice Contracts

This repository contains my personal practice smart contracts to learn Solidity and EVM development. 
All contracts have been tested locally using Hardhat/Remix.

Files:
- SimpleStorage.sol – basic storage contract
- ERC20Token.sol – practice ERC-20 token
- NFTContract.sol – practice ERC-721 NFT
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleStorage {
    uint256 private data;

    function set(uint256 _data) public {
        data = _data;
    }

    function get() public view returns (uint256) {
        return data;
    }
}


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply);
    }
}



// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract MyNFT is ERC721 {
    uint256 public tokenCounter;

    constructor() ERC721("MyNFT", "MNFT") {
        tokenCounter = 0;
    }

    function mintNFT(address to) public {
        _safeMint(to, tokenCounter);
        tokenCounter++;
    }
}


