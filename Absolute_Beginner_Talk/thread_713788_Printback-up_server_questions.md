---
title: "Print/back-up server questions"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Dj Dutchman on 2008-03-03
I have an old PC back at home which I want to use as a print server and a back-up server (to back up the other PS's in our home, automatically and at regular intervals). Which would you recommend, using Ubuntu Server or will the desktop be fine? Will I notice a difference (speed, etc) between the two? Which apps would be the best to use?

Thanks…

---

### Post by lswest on 2008-03-03
Well, it depends on the specs of the machine, if they're low, i'd go for the ubuntu server, and, if you need a GUI, go with fluxbox of XFCE, otherwise you could install XUbuntu on it if you wanted to use a desktop OS.  It doesn't really matter which version you use, desktop or server, because packages are available for both.  However, the server versions do pre-install things such as apache and mysql and samba i believe.  Maybe you could post the specs of your machine?  (my printserver is an ancient compaq with an AMD3D cpu XD)

*EDIT* also, i used [this guide]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876") to get the cups server pushing (aka auto-installing) the drivers needed for it to be used.  I don't know about the backups, not really my area of expertise.

---

### Post by Dj Dutchman on 2008-03-03
Its not that old, a 1.8Ghz AMD Sempron and 512mb RAM. Its been giving us real problems (LOTS of freezes under XP) but I suspect its a software thing (not a virus tho - already checked that). I think the thing it needs is a reformat and UBUNTU!! Just a thought is it possible to get Linux drivers for Canon printers?

---

### Post by lswest on 2008-03-03
i believe CUPS (Common Unix Printing System i think it stands for) has a driver for canon printers, but i'm not 100%, in any case, the problem will probably be getting the windows drivers on the cups system.  and yeah, on that system you can run Ubuntu or any other Linux OS you want

---

### Post by rug77 on 2008-03-03
There is a walkthrough [here](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1) which I used to set up a file server a week or so ago.  It talks through an installation using Xubuntu, and is simple enough to allow me with zero server knowledge and minute Linux knowledge to build a working server, and manage it remotely.

Recommended reading unless you already know what you're up to.

Hope this helps.

Matt

---

### Post by Dj Dutchman on 2008-03-04
Thanx rug77, I will deff help when I get down to it.  I didn't really look at the guide in depth but I didn't see anything about backing up other PC, anybody with any knowledge in this area, it would be appreciated...

---

