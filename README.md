# README

## BGP Router

### High Level Aproach

For this project of creating a BGP Router, we first worked on running the starter code with the given simulation and making sure that we understood the given code, such as how the arguments are parsed, how messages are received from the neighbors, and the way the handshake message is sent to the neighbors. Then, we started working on the project by implementing the *update* and *data* messages. While working on the *update* message, we started building the forwarding table and also implemented sending copies of a message to the other neighbors. For the *data* message, we loop through the forwarding table, apply prefix matching, and check all of the rules to find the entry that best matches the destination, then send the message to that route. After confirming that our implementation for the *update* and *data* messages worked properly, we started implementing support for the *dump* message and the *table* response. After implementing these, we were able to confirm that we built the forwarding table correctly and also pass the level-1 tests. 

Next, we verified if we implemented the rules for the *data* message correctly by running the level-2 config files. After fixing some minor bugs, we were able to pass the level-2 tests. 

Then, we worked on passing the level-3 tests by implementing support for the withdraw message. For handling the *withdraw* message, we loop through our forwarding table, compare the entries, and remove the one that matches with the one from the message. After implementing this, we passed the level-3 tests. 

Next, we added support for the various rules for enforcing peering and provider/customer relationships to the *update*, *withdraw*, and *data* message handling functions. Adding this allowed us to pass the level-4 tests. 

After passing the level-4 tests, we tested the longest-prefix matching that we implemented before by running the level-5 config files. We were able to pass the level-5 tests after fixing some bugs, such as a bug when we have an entry with a netmask of '0.0.0.0'. 

Finally, we implemented route aggregation and disaggregation to pass the level-6 test cases. For route aggregation and disaggregation, we added logic to our functions for handling the *update* and *withdraw* messages so that aggregation was done after every *update* message and dissagregation was done before carrying out every *withdraw* message. After adding this, all of the test cases passed for our router. 

---

### Challenges

One significant challenge we faced was initially trying to implement the project in Java, since neither of us worked on the previous projects in Python. It ended up being more trouble than it was worth trying to figure out how to compile and run the simulation for a program in Java, so we switched to using Python instead, which ended up being a lot easier. Another challenge we faced was correctly setting the peer address value for an entry in the forwarding table and sending copies of messages to the correct neighbor. 

---

### Properties/Features of our design

One good property of our design is that we have seperate functions for handling each type of message we may receive, such as an *update* message, *data* message, *withdraw* message, or *dump* message. This makes our code easy to read. Additionally, another good property is that we created separate functions for functionality that is repeated throughout our code, such as sending copies of a message to neighbors, turning an address into an interger, etc..

---

### Testing

We tested the code by running the given config files and checking the output of the simulation to make sure our program was running correctly. For every level of tests, we made sure that all of the test cases for a level passed before moving on to impelment the next thing. We also added print statements to print the forwarding table after every *update* message to make sure we were creating the right entries for an update message or during aggregation.  
