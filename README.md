# metis-fixture-orders

**Test fixture for [METIS](https://github.com/openzigs/metis).** This is not a real service. It is the *provider* in a three-repo portfolio used to test METIS's cross-product edge detection and impact analysis:

| Repo | Role |
|---|---|
| `metis-fixture-orders` (this repo) | Owns the Orders API, the `customers` and `orders` tables, and publishes `order.created` |
| `metis-fixture-billing` | Calls the Orders API, reads `orders` and `customers`, subscribes to `order.created`, and publishes `invoice.issued` |
| `metis-fixture-notify` | Subscribes to `invoice.issued` and reads `invoices` |

A change here, for example a new required field on a customer, should show billing as directly downstream and notify as two hops away.
