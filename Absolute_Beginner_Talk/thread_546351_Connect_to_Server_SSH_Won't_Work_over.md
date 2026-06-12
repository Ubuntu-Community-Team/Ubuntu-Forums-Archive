---
title: "Connect to Server SSH Won't Work over"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-09-08
I have a laptop and a desktop. These two machines are both running 7.10, connected by a crossover cable, and i can ssh between them in the command line quite happily. however, i cannot use the connect to server feature. i cannot understand why, as i have openssh-client and server installed on both machines.

could it be to do with a recent kerberos upgrade? because i have checked both firewalls [firestarter] and both remote hosts are allowed through each one.

i just dont get it. i have had it working before, i cant see why it wont now. it says it is connecting, on both boxes, but nothing happens. eventually this window disappears, and i am left with a blank desktop

---

### Post by Jose Catre-Vandis on 2007-09-08
What are you putting in all the boxes?

Assume:

Service Type:  SSH

Server:             IP address or hostname (ensure hostname in hosts file)

User:                Must be a valid user on server machine

If all goes well, you should find a new ssh folder in nautilus.Click on this, enter password for "User" and you're in.

---

### Post by SuperAndy on 2007-09-09
thats exactly what i am doing. i have done this before between the two computers, and between external servers from each machine.

the desktop has the IP 192.168.1.1, and the laptop has an IP 192.168.1.2.

---

### Post by Jose Catre-Vandis on 2007-09-09
"Might" be a bug? have a look on launchpad see if others are also suffering? (Can't help further as am on edgy/fiesty/other...

---

### Post by SuperAndy on 2007-09-09
well, i am going to reinstall feisty, as i had a dabble with fglrx and it went a bit wrong. so if it works after that, its one of those things. if not, i will have a deeper look at it.

---

### Post by SuperAndy on 2007-09-09
it works. just one of those things i guess...

---

