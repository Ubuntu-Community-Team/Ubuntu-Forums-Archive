---
title: "Sharing Files"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by amyfan on 2007-08-06
i have looked but cant find anywhere how do i share files from one comp to another with a regular ethernet cable  hooked up from one to another both laptops and one has xp and the other has ubuntu fiesty i have tried everything the only thing i found works takes forever at least two weeks to transfer one 93 mb file through msn messanger any ideas tips hints would help alot thanks all who do help

---

### Post by Grovers on 2007-08-06
You might take a look at [Samba]("http://us1.samba.org/samba/"), it should work for what you need.

---

### Post by wjp.reg on 2007-08-06
> **amyfan said:**
> i have looked but cant find anywhere how do i share files from one comp to another with a regular ethernet cable  hooked up from one to another both laptops and one has xp and the other has ubuntu fiesty i have tried everything the only thing i found works takes forever at least two weeks to transfer one 93 mb file through msn messanger any ideas tips hints would help alot thanks all who do help

Here&#347; a HOWTO: [HOWTO:Sharing folder for windows(Samba)]("http://forums.debian.net/viewtopic.php?t=12199")

---

### Post by overdrank on 2007-08-06
> **amyfan said:**
> i have looked but cant find anywhere how do i share files from one comp to another with a regular ethernet cable  hooked up from one to another both laptops and one has xp and the other has ubuntu fiesty i have tried everything the only thing i found works takes forever at least two weeks to transfer one 93 mb file through msn messanger any ideas tips hints would help alot thanks all who do help

HI, Do you use a router between the systems? Or are you strictly using a ether net cable from one system directly to the other?

---

### Post by amyfan on 2007-08-06
ah im directed them no router

---

### Post by lgambett on 2007-08-06
Well, you should configure the IP addresses of both PCs in a way that both reside on the same subnet, e.g. 192.168.1.1 and 192.168.1.2. On Ubuntu this is quite easy to do, using Manual Configuration within Network Manager. Once the two PCs are on the same subnet the Ubuntu machine will browse every shared folder on the Windows machine (SMB client is installed by default). To browse the Linux machine from the Windows one you have to install and configure Samba Server, as other people suggested you.
If you have access to a router with DHCP capabilities (almost every cheap router do) the two PCs will obtain automatically the IP addresses.

---

### Post by expatCM on 2007-08-06
You say that you are using "a regular Ethernet cable" and no router.

Are you sure that this will work?   Do you not need to use an Ethernet Crossover cable instead?

---

### Post by morequarky on 2007-08-08
> **lgambett said:**
> Well, you should configure the IP addresses of both PCs in a way that both reside on the same subnet, e.g. 192.168.1.1 and 192.168.1.2. On Ubuntu this is quite easy to do, using Manual Configuration within Network Manager. Once the two PCs are on the same subnet the Ubuntu machine will browse every shared folder on the Windows machine (SMB client is installed by default). To browse the Linux machine from the Windows one you have to install and configure Samba Server, as other people suggested you.
If you have access to a router with DHCP capabilities (almost every cheap router do) the two PCs will obtain automatically the IP addresses.

Hi, 

I am using Dapper on a PC and would like to get some files off of my wife's old PowerBook G4 that isn't working too well because I deleted some important files.

How would I set this up?

---

### Post by Austin_KW on 2007-08-08
To just network 2 computers together you will need an ethernet crossover cable. Many ethernet cables will just be patch cables. Crossover cables swap the receive and transmit lines so you can directly connect 2 computers. You will then need to configure the networking (IP addresses) on both computers.

If this is a one off, you should consider the old fashioned "SneakerNet". Copy the data onto a CD/DVD or an USB thumb drive and "walk" the data over to the other computer. Sometimes the simplest solutions are best.

---

