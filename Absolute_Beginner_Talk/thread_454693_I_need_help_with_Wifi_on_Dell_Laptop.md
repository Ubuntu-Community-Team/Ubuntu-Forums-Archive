---
title: "I need help with Wifi on Dell Laptop"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by rpg36 on 2007-05-25
I just installed ubuntu on my dell inspiron 2200 laptop and have been trying to get the wifi working all day. I've read tons of tutorials but none of them seem to work. I tried using the ndiswrapper and blacklisting the one bcm43xx driver which was suggested in a few thread but none of it seems to work. In fact it has gone from showing that i have a wireless card under the network tool to showing that i now only have a wired card. I know that the card i have is a broadcom 4318 built in wireless card. If anyone could help me out that would be great.

- Ryan

---

### Post by kevdog on 2007-05-25
First I would probably check in the networking forums for more info.

Do you know the revision number on the chipset you are using??
lspci

---

### Post by rpg36 on 2007-05-25
No I don't know the revision number on the chipset, but i have browsed through the networking forum and found some tutorials but none of them seem to work.

---

### Post by jargoman on 2007-05-29
If your sure you have the Broadcom 4318 then follow my tutorial I just put up about an hour ago.

[http://freeshells.ch/~jargoman/ndiswrapper.html](http://freeshells.ch/~jargoman/ndiswrapper.html)

please leave me a post on this forum saying if it worked or not. 

I think it will because I am using that card right now

oh and to find out your chipset number use
$ lspci | grep Broadcom

Although I have seen instances where peoples cards don't show up un lspci untill the driver is installed.

---

### Post by Kobalt on 2007-05-29
Check this out as well : [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

