---
title: "Local Network with Ubuntu Linux 7.04 as a Server"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Peter Alien on 2007-09-29
Hello, i wanted to make a local network with Ubuntu Linux 7.04 as a Server and put 5 PC Clients and a Router with Internet Access, but i don't know how to configure the Ubuntu Linux to create that.

The Server will run Ubuntu 7.04 and the other PCs will run WinXP Pro.

Can someone help me with that ?


I have some urgency, please.
I'll really apreciate...
Many many thanks.

---

### Post by Kilz on 2007-09-29
What you are asking is an advanced topic. But not that awfuly difficult. Are you thinking of a wired or wireless network/router? Secondly the server , what will it be used for? Will it be web pages with php and mysql(lamp), a mail server for email, a file server thats just a place to store file in a central location, or a mixture of thew above? What are the specs on the server?

---

### Post by Peter Alien on 2007-10-01
It's a wired network (CAT5 cables)

And it's a network with 5 PC Clients and a Server (Ubuntu 7.04 with Gnome) with a Router.

All clients have to connect to Internet and it runs a Database application from the server.


I just don't know how to configure Ubuntu to recognize the Router and the PC clients.



Can you help me?

---

### Post by sab0403 on 2007-10-01
If it runs a Database application, you most likely need to set it up as a file server for Windows, and also install the database software (and configure it) on the server. However I agree with the poster above that this is an advanced topic and not suitable for the "Absolute Beginners" forum. I would suggest you move it to the appropiate forum, most likely "Networking and Wireless"

Anyway, the factibility of you running your database application depends on what it's developed on. Does it use MySQL? or some propietary database? Is it developed in C, C#, Java, Perl, Python? We could use more technical details in order to help you out. But for starters, here's the tutorial for setting up Samba (the file server, which is what you need to access remote files on the server):

[http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

---

### Post by lynxus on 2007-10-01
> I just don't know how to configure Ubuntu to recognize the Router and the PC clients.

Do you mean network wise?
if so then goto admin menu and add the details in the network section?
or using ifconfig in the terminal.

Give the server an ip and subnet and a default gateway of the routers IP

---

### Post by Peter Alien on 2007-10-02
Well... for now... it runs a Database Application. The database is in MS Access, but i thinks it was better if it could be MySQL, because i thing Access is slow and weak :(


i'm sorry but i couldn´t undersant the expression "network wise", i'm portuguese and i don't understand some words :( but it's a normal intranet (ethernet) with several PCs that run WinXP Pro attached to a Linux Server.

---

