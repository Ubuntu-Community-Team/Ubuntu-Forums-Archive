---
title: "Wireless connection"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Dalton T on 2007-03-10
First time I try Linux,

have installed on my Desktop.

But don't have internetconnection now.. Have a wireless connection with SMC2662w.
Normally (in Windows XP) I have to install a software (Utilities) but this wont start here..

Have read trouhg other internet-problem postings and tried some tricks:

with iwconfig I find:

lo no wireless extensions.
sit0 no wireless extensions.

in Network connections I cannot configure the connection (lo)..

Could it be that my wireless device is not installed well? and how do I have to install it correctly?

many thanks,

---

### Post by Dalton T on 2007-03-10
Ok, thanks, found out how I had to install properly the connection.

It works now.

Cheers,
DT

---

### Post by Kobalt on 2007-03-10
I think the SMC cards are not supported out of the box by Linux so one way to get your wireless flyin' is to use Windows drivers in Linux. To do so, you will have to use a tool named Ndiswrapper. Here is [a page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") with all explanations/instructions on ndiswrapper. If you say you need to use a CD with windows then your drivers should be on it.

---

### Post by redsoftretro on 2007-03-10
Hi

Have a look here once you get the drivers going

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

cheers

---

