# Lab: Robot Warehouse with Compass

In this lab we will be familiarizing ourselves with our database structure, and operations by creating a couple of different collections, and playing around with some data using Compass, MongoDB's GUI tool. 

We will be creating a warehouse (database) that houses robots (collection). Every robot (the document) will have unique properties.


## Setting Up MongoDB Atlas Cluster
MongoDB Atlas is a fully managed cloud database service that makes it easy to set up, operate, and scale MongoDB deployments. Follow the steps below to create a MongoDB Atlas cluster:

### Step 1: Sign Up or Log In
If you don't have an account, sign up for MongoDB Atlas. If you already have an account, log in to your MongoDB Atlas account.

[MongoDB Atlas](https://cloud.mongodb.com/)

### Step 2: Create a New Cluster
After logging in, click on the Build a Cluster button.

Choose the free plan. You can also edit your provider and region

Name your cluster "mongo-practice"

Click the Create Cluster button to initiate the cluster creation process.

![Cluster set up example](./Screenshot(83).png)

### Step 3: Configure Cluster Settings
Set up authentication by creating a MongoDB user with a username and password. MongoDB can autogenerate a secure password for you, make sure you copy the password for later use

In the Connection Security section, configure your IP Whitelist settings to allow connections from your application servers. You can add your IP address or specify a range. Since we are using replit, we will need to add the IP address `0.0.0.0/0`, however, it is crucial to note that this setting grants access to any IP address, and as a best practice, this configuration should not be employed in production-level applications due to security considerations.

Once the cluster is created, click on the Connect button.

### Step 4: Connect to Your Cluster
After configuring the cluster settings, click on the Connect button again.

Choose the Connect Your Application option.

Copy the connection string provided. This string contains the necessary information to connect your application to the MongoDB Atlas cluster.

### Step 5: Connect Your Application
To access our database on replit, we will need to add our connections string to our secret keys, in VScode, we do this in our .env files

### Example connection string (replace `<username>`, `<password>`, and `<clustername>` with your actual credentials)
`mongodb+srv://<username>:<password>@<clustername>.mongodb.net/<dbname>`

In compass, we will use the same connection string to view our database. In New Connection, paste your connection string and click `Save & Connect` to get started with our lab!

## Creating the Warehouse in MongoDB Compass

At the bottom of the grey sidebar, there will be a + button to create a database. In the pop-up form, enter the database name as "warehouse" and the collection name as "robots" and create the database.

In the sidebar, you should now see the warehouse database with the robots collection within it.


## Populating our Robots


### CREATE a Robot: 

>A document in a collection is an individual data entity. In our metaphor, it's an individual robot.

Click the 'Add Data' button to open a dropdown. Select 'Insert Document' to create a new document within the Compass GUI.

This brings up an Insert to Collection pop-up that contains a JSON object. This JSON is the data that comprises the document. It will also define the traits on each individual robot.

Add the following keys to your JSON robot and fill out the value appropriately.

- creatorName 
- robotName
- robotColor
- serialNumber

**Be sure to put all keys and values in quotation marks. If the key is not in a quotation marks, you will get an insertion error.**

Create at least *five* individual robots in your robots collection. 

### READ the Robots:

Compass already performs READ for you by displaying every document in the collection in the GUI. Hooray! Near the Add Data button, you will see buttons to change the way your data is displayed as it is read.

### UPDATE a Robot:

 Hover over an existing robot and you will see several buttons appear on the right hand side of the entry. Click the pencil to edit the robot. 

 Try adding and removing keys, and updating values. Remember, this is a JSON object. 


### DELETE a Robot:

To delete, simply hover over the document you want to delete and click the trashcan button. The robot (document) is now removed from the collection.


## Expanding the Warehouse

Let's define our robots more specifically and split them up according to two traits: "friend" or "killer".

Create two new collections within the warehouse, "killer-robots" and "friend-robots". You will see a button to do this when you hover over the warehouse database in the sidebar.

Populate both collections with new robots of your design, along with the following key: value pairs.

If the robot is a killer in the killer-robots collection, add:

```js
"killer": true
"friend": false
```

And if the robot is a friend in the friend-robots collection, add the same with the boolean values switched.

>Consider a real-world analogue where you might split up similar pieces of data based upon specific values they possess



## Compass Functionality


### FIND a Robot:

The search bar above our documents is powerful but specific. You will need to enter what you are looking for as a key: value pair exactly as it appears in the document.

```js
{ "creatorName": "Matt" }
```

You can also view past queries using the rotational clock to the right of the "Find" button.

### Database Tabs

Along the top of the collection, you will see the following tabs: Documents, Aggregations, Schema, Explain Plan, Indexes, and Validation. You will likely **only** utlize the Document tabs in this course, but understanding the others will expand your database knowledge.

Documents are what you have been working with: this shows all documents within the collection.

[Aggregations](https://www.mongodb.com/docs/compass/current/aggregation-pipeline-builder/) are to build an aggregation pipeline. This is used to process a large volume of documents.

[Schema](https://www.mongodb.com/docs/compass/master/schema/) is for analyzing your data based upon its schema. You will be utilizing schemas later on in the unit.

[Explain Plan](https://www.mongodb.com/docs/compass/master/query-plan/) is for understanding query execution metrics.

[Indexes](https://www.mongodb.com/docs/compass/current/indexes/) is for special data structures (indexes) that improve query performance by portioning a collection's data.

[Validation](https://www.mongodb.com/docs/manual/core/schema-validation/) is for setting up schema validation rules within MongoDB. You will be setting up schema validation within your JavaScript in this course.

