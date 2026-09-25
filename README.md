# Algoland NFT Market Prototype

A Laravel 8 prototype for creating and exploring NFT-style Algorand Standard Assets (ASAs). The app lets a connected wallet sign asset-creation transactions, stores uploaded media on IPFS, and reads collectible metadata from the Algorand indexer.

This is an experimental prototype, not a complete buy-and-sell marketplace. The repository contains wallet, asset creation, explore, and collection flows; it does not implement a completed purchase or sale flow.

## Features

- Connect through the prototype's Algoland, AlgoSigner, or MyAlgo wallet providers.
- Create a one-unit Algorand asset with name, description, and IPFS image metadata.
- Explore matching asset-creation transactions on the configured Algorand network.
- View matching assets held by the connected account.
- Laravel Blade interface with Alpine.js and Laravel Mix frontend assets.

## Stack

- PHP 7.4 or 8.x and Laravel 8
- MySQL
- Node.js/npm and Laravel Mix
- Algorand node and indexer services
- IPFS daemon API

## Local setup

1. Install PHP, Composer, Node.js/npm, MySQL, and an IPFS daemon. The default IPFS configuration expects its API at `localhost:5001`.
2. Clone this repository and install PHP dependencies:

   ```sh
   composer install
   ```

3. Install frontend dependencies and build the assets:

   ```sh
   npm install
   npm run dev
   ```

4. Configure a local `.env` file from `.env.example`. Set the database connection values, then generate an application key:

   ```sh
   php artisan key:generate
   ```

5. Configure the Algorand node and indexer endpoints and credentials in `config/algorand.php`. The current configuration targets an older Algorand testnet service and may need replacing with a supported endpoint.
6. Create the configured database and run migrations:

   ```sh
   php artisan migrate
   ```

7. Start Laravel:

   ```sh
   php artisan serve
   ```

   Open [http://localhost:8000](http://localhost:8000).

## Important security and status notes

This repository is an old experimental prototype and is not ready for production or real-value accounts. The current repository tracks a `.env` file and includes Algorand service credentials in source configuration; these should be revoked or rotated, removed from the repository and its history where possible, and loaded from environment variables before public deployment. The wallet page can also display a session seed phrase. Do not enter or use a valuable wallet with this code.

Wallet integrations, network endpoints, and dependencies may have changed since the project was last updated. Verify that they still work before attempting to run the app.

## License

`composer.json` declares MIT, but this repository does not currently include a license file. Add the appropriate license file before redistributing the project.
