---
title: "Newb about to give up..."
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by relevantrhino on 2006-05-10
I am about to give up and just put windows back on my machines.  I can't figure out how to get my network devices to work.  I have been reading on this board for hours and can't find any answers.

All devices show up in device manager, but don't know how to get drivers to work with them.  on the threads that I have read people have said to run commands?  I have no idea how to do this.

Running Dapper Drake 6.06 on the following:

_Laptop_
Netgear MA401 802.11b Wireless PC Card
U.S. Robotics Cardbus 10/100 Ethernet PC Card (Model USR7901A)

_Desktop_
Netgear MA111v2 USB Adapter

Any help would be appreciated!

---

### Post by Omnios on 2006-05-10
This is a wiki page listing on Netgear hope it helps.
[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=Netgear]("https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=1&value=Netgear")

---

### Post by stansz on 2006-05-10
maybe try not using dapper? but breezy  ?

---

### Post by adssse on 2006-05-10
I used to have the Netgear MA401 (still would, but it bit the dust...). It was a really good card. I never used it on Ubuntu but used it on other linux distros by using ndiswrapper. The files that I needed to do this were NET8180.inf and rtl8180.sys. I apologize as I cant remember many specific details to give you, but the MA401 does work with linux well, so give it a try.

---

### Post by joshrobinson on 2006-05-10
[QUOTE=adssse]I used to have the Netgear MA401 (still would, but it bit the dust...). It was a really good card. I never used it on Ubuntu but used it on other linux distros by using ndiswrapper. The files that I needed to do this were NET8180.inf and rtl8180.sys. I apologize as I cant remember many specific details to give you, but the MA401 does work with linux well, so give it a try.[/QUOTE]

nidswrapper works wonders doesnt it :D

[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

---

### Post by adssse on 2006-05-11
Yup, it sure does. I am excited for the future though when detection makes wireless on linux easier. I hope things such as [this]("http://www.computerworld.com/softwaretopics/software/story/0,10801,111120,00.html") can help.

---

