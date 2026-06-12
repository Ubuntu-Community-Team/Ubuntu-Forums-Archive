---
title: "Windows/Ubuntu network with dial-up questions...."
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by OscarGortez on 2005-09-29
First off I can't even get my windows and ubuntu machines to see eachother yet, so i'm guessing I'll have to get samba and fool around with that, since nothing that comes on ubuntu seems to really do that job at this point (which is a whole other issue but any tips on getting that to work are appreciated)..

My question however is, once I get the network running, will i be able to connect to the internet on my Ubuntu machine, through a windows machine using a dail-up connection... like the set up would be one computer running Ubuntu and one computer running XP pro... both networked together, but only the windows machine has a modem, and I'd like them to both be able to go online at the same time if need be....  is that even possible? and if so how would i go about doing that, or if you're not sure toss some ideas my way for my to try out once I get them networked together properly.

---

### Post by SilentCacophony on 2005-09-29
Are you speaking of something like windows Internet Connection Sharing (ICS) which lets windows route network traffic, or by using a hardware router?

I don't think ubuntu can do ICS, though I could be wrong...

The normal way to do that would be to to have a router between the modem and both computers, which lets them share the connection, and also networks them together for file access.

---

### Post by matthewv on 2005-09-29
I'm pretty sure that Ubuntu can be set up to work with Windows ICS. I did it once on SUSE. You need to configure Ubuntu to use the windows machine as the gateway by setting the gateway address in the network settings to 192.168.0.1 (the ip address of the windows machine) and then add your ISPs DNS servers to the DNS tab. If I remember correctly thats all there is to it.

To get your machines to see each other I would upgrade to Breezy rather than playing round with Samba. I couldn't get my machine to see a windows network in Hoary but Breezy was fine.

---

### Post by cwaldbieser on 2005-09-30
[QUOTE=SilentCacophony]Are you speaking of something like windows Internet Connection Sharing (ICS) which lets windows route network traffic, or by using a hardware router?
I don't think ubuntu can do ICS, though I could be wrong...
The normal way to do that would be to to have a router between the modem and both computers, which lets them share the connection, and also networks them together for file access.[/QUOTE]
A hardware router generally saves you a lot of bother when doing setup, but you definitely can share your Internet connection through Ubuntu.  The technical term for this is called NAT (network address translation), and you can usually configure it through a firewall front end like Firestarter or Guidedog.

---

### Post by OscarGortez on 2005-09-30
Well the computer's are networked together with a hub, no router, and the one has an internal winmodem...

How would I set up a shared Internet connection through a firewall though?  I mean I'll download firestarter or something and check it out but, Matthewv's gateway address suggestion seems more logical to me.

---

### Post by nitricacid on 2005-09-30
[QUOTE=OscarGortez]Well the computer's are networked together with a hub, no router, and the one has an internal winmodem...

How would I set up a shared Internet connection through a firewall though?  I mean I'll download firestarter or something and check it out but, Matthewv's gateway address suggestion seems more logical to me.[/QUOTE]


If you are using a hub then you obvoisly have 2 different I.P.'s and thus have 2 different connections if you are using dial up, rite?
Or are you using one dial up connection and just splitting the connection?

Unless you have DSL or Cable your internet must be slow as anything.

---

### Post by cwaldbieser on 2005-09-30
[QUOTE=OscarGortez]Well the computer's are networked together with a hub, no router, and the one has an internal winmodem...

How would I set up a shared Internet connection through a firewall though?  I mean I'll download firestarter or something and check it out but, Matthewv's gateway address suggestion seems more logical to me.[/QUOTE]
That way will also work, but you need to do something on XP to tell it to share the Internet connection as well.  I don't actually recall what dialogs you have to go into to configure XP, though-- something in My Network Places.

I am pretty sure you need some sort of NAT though (either Windows Internet Connection Sharing or GNU/Linux style NAT), or else you run into the following situation:

Ubuntu <--> WinXP <--> Internet

In this diagram, WinXP has to IP addresses.  The local IP address that Ubuntu can see, and the Internet IP address that other computers on the Internet can see.  Now say Ubuntu sends a packet to a computer on the Internet *without* NAT.  Let's say Ubuntu is IP 192.168.0.3 on the local LAN.  A web server on the Internet receives a packet and it wants to reply.  But the sender address in 192.168.0.3-- that's not a valid Internet address!  It is reserved for local use.  So the web server can't send a reply back.

With NAT (aka Internet Connection Sharing), when Ubuntu sends the packet and it passes through WinXP, WinXP alters the packet so it looks like it is sending it through its Internet IP address.  It keeps track of the connection, so when the web server replies, it knows to send the packet back to Ubuntu.

In Firestarter, there is an option Preferences -> Network settings for Internet connection sharing.  I have never used it with dialup, but the type of device shouldn't really matter.  In that scenario, Ubuntu would need to dial in, and it would share its connection.

---

### Post by matthewv on 2005-09-30
To set up internet connection sharing with xp and ubuntu:
Go to My Network Places on the XP machine. From the sidebar, select Setup a home or small office network. Run through the wizard. When it asks about running the wizard on other computers just tell it you'll manage it yourself.
Go to your ISPs website and write down both the primary and secondary DNS servers.
On your Ubuntu machine go to System --> Administration --> Networking
Select your network card (usually eth0) and press Properties. Give your ubuntu computer a static ip adress in the 192.168.0.* range (192.168.0.2 is a good idea, don't do 192.168.0.1), assign a subnet mask of 255.255.255.0, and set the gateway to 192.168.0.1. Press OK.
Then, go to the DNS tab and add the DNS server addresses you copied down earlier, first the primary and then the secondary. Press OK and you should be all set. I haven't done this in ubuntu but I had it all running in SUSE (got DSL now :)).

---

### Post by OscarGortez on 2005-10-01
thanks for all the advice I'll be sure to let you know how it all goes once I get the machines to actually see each other :-p

---

