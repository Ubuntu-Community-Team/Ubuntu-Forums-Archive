---
title: "help me understand routing"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by xrado on 2006-04-09
for instance i have:
router 192.168.1.1
comp1 192.168.1.111
comp2 192.168.0.112

both computers are connected to router. How do i make computer to see each other?
what routes do i have to set?

thanks for any advice!

---

### Post by ubernoob on 2006-04-09
your question isn't clear. But if i understand you right, you should set network mask to 255.255.0.0 or change the comp2 to 192.168.1.112

---

### Post by cwaldbieser on 2006-04-09
[QUOTE=xrado]for instance i have:
router 192.168.1.1
comp1 192.168.1.111
comp2 192.168.0.112

both computers are connected to router. How do i make computer to see each other?
what routes do i have to set?

thanks for any advice![/QUOTE]
You haven't really given quite enough information for someone to answer your question.

Routers are just machines that route packets from one network to another.  A network is a group of similar IP addresses.  A given IP address on your network will be composed of a network-part and a host-part.

For example, a typical home network might be 192.168.0.0/24.  This notation means that the first 24 bits (or the first 3 numbers of the IP address) are used to identify the network, and the last 8 bits (or the last IP address number) are used to identify a computer on the network.  

The key thing to note here is that you need to specify how much of an IP address represents the network, and how much is reserved for individual computers on the network.

Another common way of expressing this is with a netmask.  This is similar to what you will see if you issue the "route" command in the terminal.  It is expressed 192.168.0.0/255.255.255.0.

The numbers corresponding to the network part match up with a "255".  The numbers left for the host part match up with a "0".

Computers on the same network can talk to each other without having to do anything special.  So if I tweak the example you gave:
router 192.168.1.1/255.255.0.0
comp1 192.168.1.111/255.255.0.0
comp2 192.168.0.112/255.255.0.0

All your computers are on the 192.168.0.0/255.255.0.0 network, so they can all talk to each other without any other special setup.  However, if I make the configuration look like this:
router 192.168.1.1/255.255.255.0
comp1 192.168.1.111/255.255.255.0
comp2 192.168.0.112/255.255.255.0

Now, comp1 is part of the 192.168.1.0/255.255.255.0 network, and comp2 is part of the 192.168.0.0/255.255.255.0 network.  Since they are on different networks, they need the router to deliver network packets to the other network for them.

In order to do this, each computer will need a routing table entry that tells it where to send packets if the destination is on a foreign network.  So if comp1 wants to send a message to comp2 on the 192.168.0.0/24 network, it needs a routing entry that says, "packets going to the 192.168.0.0/24 network should be sent to router.  router will know how to deliver the packet after that."

If you just have one router in your home network, it is typical that you would just set your default route to point to your router.  That means that packets destined for ANY foreign network should be sent to your router, and it will sort it out.

Now, after that long winded explanation, if you have a simple home setup like I expect you do, you should be able to just plug both computers into your router and change their IP addresses and netmasks so that they are on the same network.  Then you should be abe to ping from one to the other with no problem.

The networking GUI should let you change the appropriate settings, or you should be able to use the "ifconfig" and "route" commands from the terminal.  To make permanaent changes from the terminal, you will need to edit /etc/network/interfaces.

If you need more particulars, just ask.

---

### Post by xrado on 2006-04-09
thank you both for explanation, things much clearer now. i just experiment a little with my small home network. i know that if i have everything in C class it will just work...but im trying to figure out how to access to another subnet..not any particular reason..im just curious. thanks again!

cwaldbieser: ...i actuality printed out you explanation :)

---

