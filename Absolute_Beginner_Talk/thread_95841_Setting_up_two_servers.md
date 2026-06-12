---
title: "Setting up two servers"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by bphar on 2005-11-27
This is my first post, and full dive into Linux!  I have been tinkering with Linux for about a year now, and am finally getting to install it on a broad scale.  I teach a computer class in a middle school, and got the green light to convert my 35 computers from Novell to Linux.  Prototype for the district!!  I am also writing the five year district technology plan, and want to demonstrate the benefits for Linux in Education.  

  On to my problem. I have 35 computers and want to create two servers to handle the load, but can not find the instructions on how to connect them together.  Also, I will eventually need to set up a file server as well.  Edubuntu installed great, and all is well for one server (AMD 2500, 2 gb RAM, 160 gb HDD, 2x 10/100/1000 NIC) just not beefy enough for all 35 clients at the same time without bottlenecking.  

Thanks,
Brent

---

### Post by EC-Rider on 2005-11-27
Dear Brent,

I am sorry I can't help you, but I think this is a great initiative! Please keep on going, good luck.

Regards,
Eric

---

### Post by coza on 2005-12-06
Hi ,

What exactly do you want the servers to 'share' if you join them up ? 
You could just set them up as you would do two small networks, and have one server manage 20 and the other 15. Would this not work?
When you say that you get bottlenecks with all 35 clients running simultaneously, how do you mean ? What happens ?

Coza

---

### Post by bphar on 2005-12-11
Can I use two separate computers on the same network?  Or, do I need to put one on one switch and one on another?

Also, when I get all 35 computers opening OpenOffice they lock up and take about 5 min to load.  Also, when they all log off it locks up the system and takes over 5 min to log out.  Often nothing works when everyone is working on different projects in OOo and Ktouch.  It is very slow to respond to new programs being opened.  

I listened to a podcast by the creator of LTSP and they stated that once one instance of OOo was open the other computers requesting to open should be fast due to the basic program is already loaded.  It seems to me that each computer terminal requesting OOo opens as if they were the first request.  I have tried to have OOo at the server to keep open OOo program to speed the process, but to no avail.

Any suggestions?  Maybe I need to do some tweaking, but I am not sure how to at this time - or even where to look for the information to do the tweaking.

Brent

---

### Post by coza on 2005-12-20
I would  setup the two servers on different networks, unless you can differentiate between which server each client will boot from. I'm not sure if or how this works.

---

### Post by kosmic on 2005-12-20
Ok, what is the specs of your server ? how much ram does it have ? are the clientes conected to a Bridge ? a switch or a Hub ? what is your ethenet speed ? 10MBiT - 100MBiT or 1000MBiT
 
LTSP should be prety fast with the right ram :) and rigth ethernet devices :)

---

### Post by bphar on 2006-01-30
I have two machines running:
1)  AMD 2500+ (1.8 gig)
     2.5 gigs RAM
     (2) 10/100 NIC - one for internet and one with crossover to other server
     (1) 10/100/1000 NIC - this one to clients
     18 gig SCSI 15k with controller card
     160 gig ultra IDE 133

2)  AMD 2500+ (1.8 gig)
     2 gigs RAM
     (2) 10/100 NIC - one for internet and one with crossover to other server
     (1) 10/100/1000 NIC - this one to clients
     100 gig ultra IDE 133 with controller card

(2) Dell network switchs

(35) Dell optiplex GX-1 
       450mhz 
       128 RAM
       8.7 gig HDD
       PXE boot NIC

All runs great on one machine, until I get over 20 clients.  That is why the second server.  I can set box 2 to NFS /home to box 1, but how to get the two to load balance.

I also have a new server I just ordered this week to add to this group, and add more clients school wide.  Dell - (2) zeon 2.8, 3 gig RAM, (2) 73 gig SCSI 15k HDD, (2) 10/100/1000 NIC.

Thanks for your help.

Brent

---

