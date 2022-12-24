# 404 Auction House

This project is a <b>mock up of eBay</b>, hosted using docker. <br>
It is a digital marketplace hosted locally where the users can create listings that can be sold in either of 2 ways - "immidiate buy" or "auction".<br>


## Core Features:
1. Signup and Login.
2. Seperate Admin Functionalities.
3. Create listings to sell and categorize items.
4. "Buy Now" feature.
5. Push listing to "Auction" and/or take part in one.
6. Search feature.
7. Cart, Watchlist and Checkout features.
8. Notifications sent to the user's email on multiple instances (might have to check span).
9. Customer Support.
10. Data persistance.


## Overview
The project uses the microservie architecture with 6 bounded contexts.<br>
For a detailed overview, please go to the architecture folder in this repository. The following diagram gives a high level overview of the architecture. <br>
![image info](/architecture/high_level_architecture.png)


## How to Execute:
1. To run, cd to the working directory and execute:
```
docker-compose up --build
```
2. Navigate to "http://127.0.0.1:5005/" on your browser.
3. Only an admin can create more admins. <br>
To create your first admin, open Postman or any similar software and execute the following POST command:
```
http://127.0.0.1:5003/signUp?user_name=<enter_admin_username>&first_name=<enter_first_name>&last_name=<enter_last_name>&date_of_birth=<enter_in_YYYY-MM-DD_format>&phone_number=<enter_10digit_number>&address=<enter_address>&email=<enter_valid_email_id_for_admin>&password=<enter_admin_password>&admin_status=True
```
4. Once you log in as a user/admin and create an item, it is defaulted to the "Buy Now" feature. If you want to push the item for auction, please enter the corresponding "Item ID" and press the "Add for Auction" button. Now navigate to the "Auction" portal and continue.

5. Once you're done, Ctrl+C to stop the server. Once this is done, the data will no longer persist. The execute the following to take down the containers.
```
docker-compose down
```


## List of all Features Covered:
1. <b>FrontEnd Functions:</b>

- Create User
- Delete User
- Suspend User
- Login
- Logout
- See active actions
- Add Item
- Bid on Item
- Remove Item
- Purchase Item
- Flag Item
- Add item to cart
- Add item to watchlist
- Checkout

2. <b>Database Functions:</b>

- Data is stored in a persistent manner as long as the Docker containers are running. 
- Retrieve of stored data by both Frontend and Backend services. 
- Ability to perform all CRUD operations on the data from both the Frontend and Backend services.
- Scalable database.

3. <b>Admin Functions:</b>

- Early stop for an auction.
- Remove and/or block a user.
- Add, modify, or remove categories.
- View all items that have been flagged by users. 
- View all auctions currently in progress with the feature to sort auctions based on start and end times.
- Examine metrics for closed auctions in a given timeframe (last day, week, month, etc)
- Examine emails that are received by customer support, and respond to these emails within the admin functionality. 

4. <b>Auction Functions:</b>

- List of items for bidding.
- Auction starts when the current time matches the start time defined by the user.
- Allows auction window to be set by the bidder, and starts countdown to the end of the bidding window once auction begins.
- Allows bid to be placed, and an increment bid amount entered by the user.
- Allows item to be categorized by user.
- Allows search of items on the site by keyword, or item category.
- Allows item to be placed on a watchlist for a user.
- Allows multiple bids to be placed at once by different users.
- Alerts seller when their item has been bid on with an email.
- Alerts buyer via email when someone has placed a higher bid on the item they had bid current high bid on.
- Shopping cart feature that will store multiple items in it while the user shops on the site.
- Allows item to be placed in the shopping cart if the "Buy Now" feature is selected
- Places item in a user's cart and proceeds to automatic checkout if they have the winning bid when the auction expires.
- Allows a user to checkout from their cart once there are items in it.
- Alerts both seller and bidders when on predetermined time setting, 1 day before bidding ends, 1 hour before bidding ends, etc.
- Removes an auction and item once bidding is complete and checkout is successful.

5. <b>User Functions:</b>

- Create a new user. A user has the ability to buy item or place bids on a item(s) or place an item for sale, or all.
- Update a user’s information
- Delete a user
- Suspend an account
- List an item for auction
- Update an item
- Flag an item as inappropriate or counterfeit
- Categorize an item based on existing categories or create an new category if needed.
- Delete an item if its set to "Buy Now". If set to "Auction" allows delete only when there are no bids placed on it.
- Bid on an item, and update that bid if another user outbids that user.
- See a list of all items that are currently being bid on by that user.
- Add item to cart directly via the "Buy Now" functionality.
- Automatic checkout of an auction on winning.

### Contact
For any questions please contact:<br>
Prajval Mohan<br>
prajval.mohan23@gmail.com
