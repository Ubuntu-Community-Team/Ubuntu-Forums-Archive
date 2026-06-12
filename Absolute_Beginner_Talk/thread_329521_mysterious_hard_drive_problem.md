---
title: "mysterious hard drive problem"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by kcbear on 2007-01-01
Hi, im very new to linux 

i have a 30gb maxtor hard drive partitioned 5gb for ubuntu and 25 for the rest. for some reason i have to set the jumpers to 'slave' for it to boot up. if i set it to master it stops part way through loading when its trying to access root files. 

this wouldnt be too much of a problem except that now im tying to set up a dual os, dual hard drive system, im running into problems getting the computer to recognise both hard drives and getting them both to work.

would like to solve the problem of why i need to set jumpers to slave before moving onto trying to solve dual hard drive problem

---

### Post by benerivo on 2007-01-01
Have you tried the 'cable select' option for the jumper settings to see what that does - plugging the maxtor in to the master connection on the cable?

---

### Post by halitech on 2007-01-01
is there any other device on the same channel? is this on the primary or secondary channel?

---

### Post by MkfIbK7a on 2007-01-01
try jumering both hds for "cs"

---

### Post by gn2 on 2007-01-01
The jumper must either match the connector or both set to Cable Select.

Middle connector=slave

End connector=master

Not all BIOS versions will accept cable selection.

---

### Post by smoker on 2007-01-01
are your hard drives sata or ide?

if ide, you should have two ide channels, supporting up to four devices (2 each channel).

if your ide ribbon has three connection, one end should connect to the ide socket on the motherboard, and the other end should connect to your master hard drive, with the jumper set as such, the middle connection should be for the slave, with jumper set as such. if your setup varies from this, then try changing it.

also, some motherboard/hard drive combination can be picky, and prefer the devices attached to the cable to be set to cable select. try this if the above doesn't work,

hope this helps

---

