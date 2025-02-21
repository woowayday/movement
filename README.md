# Movement Labs Contracting Language (MLCL)

Welcome to the **Movement Labs Contracting Language (MLCL)** – an experimental programming language designed to facilitate the development of smart contracts and movement-based operations in decentralized environments.

This language focuses on enabling **movement programming** within blockchain ecosystems, where users can create contracts that involve complex asset movements, automation of decentralized tasks, and robotic transactions on the blockchain.

## Features
- **Movement Logic**: MLCL allows for easy definition of movement patterns and flow for tokens, assets, and other blockchain resources.
- **Smart Contracts**: Write and deploy smart contracts with built-in support for asset transfer, staking, and decentralized operations.
- **Interoperability**: Easily integrates with major blockchain networks like Ethereum, Solana, and others.
- **Extensibility**: Extend MLCL to include custom movement patterns and behaviors tailored to your project’s needs.

## Installation

To get started with MLCL, you need to install the necessary tools and set up your environment.

1. **Install Node.js** (for JavaScript-based tools and integration):
    - [Download Node.js](https://nodejs.org/)

2. **Clone the Repository**:
    ```bash
    git clone https://github.com/yourusername/mlcl.git
    cd mlcl
    ```

3. **Install Dependencies**:
    MLCL uses `npm` to manage dependencies. To install them, run:
    ```bash
    npm install
    ```

4. **Compile the MLCL Code**:
    MLCL code needs to be compiled before deployment. To compile your code:
    ```bash
    npm run compile
    ```

5. **Deploy Your Contract**:
    MLCL contracts can be deployed to Ethereum, Solana, or any compatible blockchain network. Follow the specific deployment instructions for your chosen platform.

## Example: Basic MLCL Smart Contract

Here’s an example of a simple smart contract written in **MLCL** that transfers tokens between two users:

```mlcl
module movement::loops {
    use std::vector;

    // Sum of first N natural numbers using while loop
    fun sum_using_while(n: u64): u64 {
        let sum = 0;
        let i = 1;
        while (i <= n) {
            sum = sum + i;
            i = i + 1;
        };
        sum
    }

    // Sum of first N natural numbers using for loop
    fun sum_using_for(n: u64): u64 {
        let sum = 0;
        for (i in 1..(n+1)) {
            sum = sum + i;
        };
        sum
    }

    // Sum of first N natural numbers using infinite loop
    fun sum_using_loop(n: u64): u64 {
        let sum = 0;
        let i = 1;
        loop {
            if (i > n) break;
            sum = sum + i;
            i = i + 1;
        };
        sum
    }

    // Sum of first N natural numbers using vector and fold
    fun sum_using_vector(n: u64): u64 {
        let numbers = vector::empty<u64>();
        let i = 1;
        while (i <= n) {
            vector::push_back(&mut numbers, i);
            i = i + 1;
        };
        vector::fold(numbers, 0, |acc, num| acc + num)
    }

    #[test_only]
    use std::debug;

    #[test]
    fun test_sum_functions() {
        let n = 10;
        let expected_sum = 55; // Sum of 1 to 10

        assert!(sum_using_while(n) == expected_sum, 0);
        assert!(sum_using_for(n) == expected_sum, 1);
        assert!(sum_using_loop(n) == expected_sum, 2);
        assert!(sum_using_vector(n) == expected_sum, 3);

        debug::print(&sum_using_while(n));
        debug::print(&sum_using_for(n));
        debug::print(&sum_using_loop(n));
        debug::print(&sum_using_vector(n));
    }
}
