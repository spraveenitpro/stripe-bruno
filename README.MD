# Stripe Bruno Collection

This repository contains a set of [Bruno](https://www.usebruno.com/) HTTP request files for interacting with the Stripe API. These requests are organized to help you test and automate common Stripe operations such as customer management, payment methods, and payment intents.

## Prerequisites

- [Bruno](https://www.usebruno.com/) installed on your machine.
- A valid Stripe test secret key (already included in the requests, but you should replace with your own for security).

## Requests Overview

### 1. Authenticate.bru

- **Purpose:** Test authentication with Stripe using your secret key.
- **Method:** GET `/v1/charges`
- **Usage:** Verifies that your API key is valid and can access Stripe resources.

### 2. Get Customers.bru

- **Purpose:** Retrieve a list of customers from your Stripe account.
- **Method:** GET `/v1/customers`
- **Usage:** Fetches all customers for review or further processing.

### 3. Create Customer.bru

- **Purpose:** Create a new customer in Stripe.
- **Method:** POST `/v1/customers`
- **Body:** `name`, `email`
- **Usage:** Adds a new customer to your Stripe account.

### 4. Create Payment method.bru

- **Purpose:** Create a new payment method (card) in Stripe.
- **Method:** POST `/v1/payment_methods`
- **Body:** `type`, `card[token]`
- **Usage:** Registers a new card payment method using a test token.

### 5. Attach Payment method.bru

- **Purpose:** Attach a payment method to a customer.
- **Method:** POST `/v1/payment_methods/{payment_method_id}/attach`
- **Body:** `customer`
- **Usage:** Links a payment method to a specific customer.

### 6. Create Payment intent.bru

- **Purpose:** Create a new payment intent for processing a payment.
- **Method:** POST `/v1/payment_intents`
- **Body:** `amount`, `currency`, `automatic_payment_methods[enabled]`, `customer`, `receipt_email`
- **Usage:** Initiates a payment process for a customer.

### 7. Confirm Payment intent.bru

- **Purpose:** Confirm a payment intent to complete the payment process.
- **Method:** POST `/v1/payment_intents/{payment_intent_id}/confirm`
- **Body:** `return_url`, `payment_method`
- **Usage:** Finalizes the payment after creating and attaching a payment method.

## How to Use

1. Open this collection in Bruno.
2. Update the API keys in each request with your own Stripe test secret key for security.
3. Run the requests in sequence for a full payment flow:
   - Authenticate → Create Customer → Create Payment Method → Attach Payment Method → Create Payment Intent → Confirm Payment Intent
4. Inspect responses and use as needed for your development or testing.

## Security Note

**Do not share your secret API keys publicly.** The keys in these files are for demonstration and should be replaced with your own.

---

Feel free to modify this README as your collection grows or your workflow changes!
