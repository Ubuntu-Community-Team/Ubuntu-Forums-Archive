---
title: "Backup Evolution contacts"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Exdevon on 2007-12-08
Sorry its probably basic, but I can't work out how to backup my contact list - I can't even find it's folder to make a copy.
Please help!
Thanks

---

### Post by mikeyphi on 2007-12-08
> **Exdevon said:**
> Sorry its probably basic, but I can't work out how to backup my contact list - I can't even find it's folder to make a copy.
Please help!
Thanks

Select your 'Home' folder; from the drop-down menu select 'view'/ 'show hidden files'.....open the file named .evolution - open addressbook/local/system - there you should find the addressbook.db

However you could open Evolution and select File/ backup settings to do a manual backup

Or you could use Simple Backup (sbackup) available through Synaptic to do unattended regular backups of (mostly) everything!

---

### Post by Exdevon on 2007-12-08
Many thanks, I'll give it a go.

I notice you are using Ubuntu 7.10 - have you had any problems accessing internet?   I upgraded from 7.04 and have not been able to connect via lan to my router.  I get a few packet sends and returns but no further. The lan uses Eth0 with roaming enabled. (the router works fine via wireless to my laptop).

Any suggestions before I return to 7.04 ?

---

### Post by mikeyphi on 2007-12-08
> **Exdevon said:**
> Many thanks, I'll give it a go.

I notice you are using Ubuntu 7.10 - have you had any problems accessing internet?   I upgraded from 7.04 and have not been able to connect via lan to my router.  I get a few packet sends and returns but no further. The lan uses Eth0 with roaming enabled. (the router works fine via wireless to my laptop).

Any suggestions before I return to 7.04 ?

I have a wire connection to a second computer- set up with a static address and a wireless connection, with wep,  to my router - I have roaming deselected on both connections.

---

### Post by bigken on 2007-12-08
in evolution go to file select backup settings this will back mail addresses calender ect

---

### Post by Exdevon on 2007-12-08
Many thanks to Mikephy and Bigken for solution to locating and backing up evolution.  Straightforward when you know how!

However, I am still in trouble with the lan connection in Ubuntu 7.10.
I have unticked roaming and set to static using the address data from sudo ifconfig, but sill no connection other than a few send & receive packets.

Any other suggestions?

---

### Post by Exdevon on 2007-12-13
OK, I've fixed it.

ping google.com timed at 30ms so the connection is ok, its just not going any further.  

On further investigation it turned out that the Firestarter firewall had reset itself to restrictive outbound when I upgraded from 7.04 to 7.10.

Setting firestarted policy to outgoing permissive solves the problem.
(system>administration>firestarter>policy>outbound>permissive)

QED easy peasy  (thought this might help other nubies)

---

### Post by Astrikor on 2007-12-13
> **Exdevon said:**
> OK, I've fixed it.

ping google.com timed at 30ms so the connection is ok, its just not going any further.  

On further investigation it turned out that the Firestarter firewall had reset itself to restrictive outbound when I upgraded from 7.04 to 7.10.

Setting firestarted policy to outgoing permissive solves the problem.
(system>administration>firestarter>policy>outbound>permissive)

QED easy peasy  (thought this might help other nubies)

Hi exdevon-
Looks like youv'e sorted out my problem too ( in the installation&upgrades forum)
Many thanks
Astrikor

---

### Post by Exdevon on 2007-12-15
> **Astrikor said:**
> Hi exdevon-
Looks like youv'e sorted out my problem too ( in the installation&upgrades forum)
Many thanks
Astrikor


Glad to help!

Exdevon

---

