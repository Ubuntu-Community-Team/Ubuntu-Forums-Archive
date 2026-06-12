---
title: "Compaq Presario R4000 AMD64"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by ddw1959 on 2007-05-30
Well I am new at Linux and installing it on my Compaq.  Besides just figuring out how to access stuff (Is there a UBUNTU 7.04 User Manual?) I cannot figure out how to activate my wifi.  Any help on that would be great.  Also, any clues on where to find other cool software would be welcome.

Thanks.
David

---

### Post by TheMono on 2007-05-30
OK, go into a terminal (programs -> accessories -> terminal) and paste in

lspci

That will give you a list of all the different parts in your computer. Find the one that is your wireless card, and copy that back into here so we know what brand we are dealing with.

---

### Post by Cedfelix on 2007-06-03
I have the same comp as you do and am also working on getting my wifi card up and running. I has worked in the past with Badger and Edgy. 
Unfortunately, these computers come with a Broadcom BCM4318, which is notoriously fickle to set up. Others can explain it better than me...
[URL="http://ubuntuforums.org/showthread.php?t=197102"]
http://ubuntuforums.org/showthread.php?t=197102[/URL]

This is the route I am going at the moment. I will post more if I get mine up and going.

---

### Post by Cedfelix on 2007-06-03
From the link in the previous post:
"You have two options (I'll try and outline them for you):

   1. Use the native bcm43xx driver. This driver is open source and included with the kernel. It can not run at any speed higher then 11mbps, is some what flaky, and supports promiscuous mode. Requires user to be somewhat close to the access point. Is easier to install.
   2. Use ndiswrapper. ndiswrapper is open source, however the driver is not. It can run at 54mbps, is stable, and does not support promiscuous mode. I have had some trouble with it and hidden networks. Supports a large distance from the access point."

I ended up trying the bcm4300 driver first and it worked. In the past I have always set up ndiswrapper, and that worked for Breezy and Edgy. Good luck!

---

