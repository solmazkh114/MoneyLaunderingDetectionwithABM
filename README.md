# Money Laundering Detection Model

This project simulates the detection of potential money laundering activities during the placement stage, using an agent-based approach. The model is built with the Mesa package, which is a Python package specifically designed for agent-based modeling.

## Money Laundry

Money laundering is the process by which individuals or organizations disguise the origins of illegally obtained money to make it appear as though it comes from legitimate sources. This process typically occurs in three stages:

- Placement: In the first stage, illicit funds are introduced into the financial system. This is often done by breaking up large amounts of money into smaller, less suspicious sums and depositing them into banks or other legitimate financial institutions. Common methods include depositing cash into bank accounts, purchasing high-value items (like real estate or luxury goods), or using businesses that deal with a lot of cash (like casinos or retail stores) to "clean" the money. This stage is risky because it involves handling physical cash or other assets that can easily be traced back to illegal activity.

- Layering: Once the money has entered the financial system, the next step is to separate the illicit funds from their source through a series of complex transactions. These transactions may involve multiple bank accounts, companies, or countries, making it difficult to trace the original source of the money. The goal is to obscure the money’s origin by moving it through a variety of financial channels. For instance, funds might be transferred between offshore accounts, used to buy and sell assets, or mixed with the legitimate revenue of a business. Layering often involves electronic transfers, shell companies, or investments in commodities.

- Integration: In the final stage, the laundered money is reintroduced into the legitimate economy, appearing to be clean and legal. By this stage, the funds can be used for any legal purpose, such as purchasing assets, investing in businesses, or making other major financial transactions. Since the money has passed through various financial institutions and transactions, it becomes difficult for law enforcement agencies to trace it back to its illegal origins.

This project is a simple simulation of the placement stage, where money launderers receive funds through multiple small transactions. The model focuses on detecting suspicious patterns early on by analyzing transaction behaviors and flagging unusual activities. This helps illustrate how financial institutions might track and identify potential laundering activity.

## Mesa Package
The project uses the Mesa library for agent-based modeling. Mesa allows us to simulate the behavior of agents (e.g., customers) as they interact with the financial system. To run this project, you need Python 3.11 or higher. You can install Mesa using the folloing commands:

```pip install --upgrade mesa[rec]```

To install the latest features:

```pip install --upgrade --pre mesa[rec]```


## How Does the Project Work?
The model uses two main criteria to flag suspicious accounts:

1. Number of Transactions: If a customer performs more than a threshold number of transactions within a short time frame, they are flagged.
2. Suspicious Score: This is a metric we defined to track the likelihood of money laundering based on transaction behavior. It is a custom metric designed to flag unusual patterns of behavior and desined in a way that if multiple suspicious transactions occur consecutively, the penalty escalates. This is a simplistic approach based on the assumption that repeated unusual transactions should be penalized more heavily. In real-world scenarios, a more sophisticated method defined by financial regulations would be used.

## Agent Attributes
Each agent (customer) in the model has six key attributes:

- `is_launderer`: Boolean flag indicating if the customer is engaging in laundering. We use these attributes to have control over the transaction patterns of the customers we would like to consider as launderer.
- `percent_laundery`: The percentage of creating agents as launderers. 
- `account_balance`: The customer's starting balance which is initialized randomly. 
- `history_log`: A list of past transactions, tracking the amount and time difference between transactions.
- `status`: Either "normal" or "flagged" based on their suspicious score. At the beginning, we assume all customers are normal. In the iteration of modeling, if the model determines the customer transactions are not normal, the customer will be flagged and not allowed to perform more transactions. 
- `suspicious_score`: A score assigned based on the customer's transaction history. We initially assigned a value based on the customer's initial balance amount. More balance, greater suspicious score. 

## Model Validation
After running simulations, we analyze the results to ensure the model correctly flags customers with suspicious behavior (the ones that we initially defined as launderer (`is_launderer =True`). We look at patterns in flagged transactions and validate that the model responds appropriately to unusual activity.

