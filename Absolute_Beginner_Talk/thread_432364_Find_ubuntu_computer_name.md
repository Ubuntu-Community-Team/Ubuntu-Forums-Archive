---
title: "Find ubuntu computer name"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jlambeth1 on 2007-05-03
I want to use remote desktop on my XP laptop to connect to my ubuntu box, but have no idea where to find the computer name of my ubuntu box.  I am sure it is easy to find but I must be having a blonde moment!

---

### Post by Gmbrdilos on 2007-05-03
didn't you set it durning the install?

---

### Post by starcraft.man on 2007-05-03
Easy, go System > Administration > Network, go to General tab, it should be the Host Name, I believe.

By default I think its ubuntu.

---

### Post by jimrz on 2007-05-03
> **jlambeth1 said:**
> I want to use remote desktop on my XP laptop to connect to my ubuntu box, but have no idea where to find the computer name of my ubuntu box.  I am sure it is easy to find but I must be having a blonde moment!

quick and easy way ... open your terminal ... the first line will start with <your user name>@<computer name>

you may find that connecting by ip address rather than computer name seems to work better

---

### Post by starcraft.man on 2007-05-03
> **jimrz said:**
> quick and easy way ... open your terminal ... the first line will start with <your user name>@<computer name>


I coulda given that answer too, I just wanted him to work a bit :p

---

### Post by jlambeth1 on 2007-05-03
Thanks for the quick replies everyone.  If it is easier to connect by th IP address, my other question would be where do I find that?

---

### Post by bobplano on 2007-05-03
well you don't find it on ubuntu. the router assigns your computer one or you choose one of the ip's from your router and set it so it is always that ip. you need to log in to your router to figure out the ips if you don't know them

---

### Post by starcraft.man on 2007-05-03
You can find out several ways what your IP is without logging into the router (logging into the router is one option though, your computer is obviously in the tables).

If you have network-manager installed like in feisty, right click on it and select connection details. Your IP is staring you in the face :)

If you don't have that, takes a bit more work. Go to System > Administration > Network Tools, in the network device section, make sure your ethernet card is selected, your IP should be first entry, probably next to the IPv4 entry.

Have fun!

---

### Post by nanotube on 2007-05-04
ehrm, if you are looking for it in the windows network through XP, don't you need to have samba installed and configured? 

i don't run feisty, so maybe it comes with samba configured by default (unlike dapper), but i wouldn't bet on it.

---

### Post by JAPrufrock on 2007-05-04
If you don't have network manager installed, open a terminal and run the command  "  ifconfig ".  The IP address should be the first one listed.

---

### Post by JAPrufrock on 2007-05-04
> **nanotube said:**
> ehrm, if you are looking for it in the windows network through XP, don't you need to have samba installed and configured? 

i don't run feisty, so maybe it comes with samba configured by default (unlike dapper), but i wouldn't bet on it.

Actually it is installed by default.  Surprised me, that! Of course it still has to be configured.

---

### Post by jimrz on 2007-05-05
> **JAPrufrock said:**
> If you don't have network manager installed, open a terminal and run the command  "  ifconfig ".  The IP address should be the first one listed.

or right click on the network icon on your panel > properties > the "support" tab and it is listed there

---

