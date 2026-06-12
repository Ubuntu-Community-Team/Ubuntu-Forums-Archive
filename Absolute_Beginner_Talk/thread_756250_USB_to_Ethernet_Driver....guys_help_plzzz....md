---
title: "USB to Ethernet Driver....guys help plzzz..."
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ruffshuvit on 2008-04-15
i think this is a common problem since i see many post had post the same prob...yet i cant find the answer because no one have replied the solution...

any pro user of linux...hope u guys can help me....

specifically my problem was i cant connect to internet using USB to fast internet adapter...the manufacturer give the driver only for windows..i have waiting the answer from other thread, but no one give a replies...hopefully someone will alert for my thread....plzzz guys...really need a help....

im really glad if someone can give the solution....

---

### Post by pseudo-random on 2008-04-15
If its like the one I've got there is a sticker underneath with some useful info.
Can you post all the small print, numbers etc on the underside.

---

### Post by scorp123 on 2008-04-15
> **ruffshuvit said:**
>  USB to fast internet adapter  You have a USB Ethernet adapter? Can you give more details? What brand, what model, and so on? :confused:

---

### Post by zvacet on 2008-04-15
You can start from [here.](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by ruffshuvit on 2008-04-16
owh...sory for that...i forgot to give a detail about the device

USB2.0 to Fast Ethernet Adapter
device name : network adapter
manufacturer : DAVICOM semiconductor inc
model : HY-818

mine doesn't have any brand....is this detail enough?...if not enough please state what ever i need to add...sory for my newbie....really hope any1 can help me....:(

---

### Post by scorp123 on 2008-04-16
> **ruffshuvit said:**
>  USB2.0 to Fast Ethernet Adapter
device name : network adapter
manufacturer : DAVICOM semiconductor inc  If you plugin that one into the system ... does the adapter start blinking after a few seconds or show any reactions at all?

Also what kind of output do you get if you type these commands *after* plugging the adapter into system:
```
dmesg
``` ... here you should only pay attention to the last few lines. Check if they mention detection of a new USB device or anything.

```
lsusb
``` ... here you should get a listing of all USB devices the system has detected. Can you please post the list here just to check if something can be seen?

---

### Post by ruffshuvit on 2008-04-18
> **scorp123 said:**
> If you plugin that one into the system ... does the adapter start blinking after a few seconds or show any reactions at all?

Also what kind of output do you get if you type these commands *after* plugging the adapter into system:
```
dmesg
``` ... here you should only pay attention to the last few lines. Check if they mention detection of a new USB device or anything.

```
lsusb
``` ... here you should get a listing of all USB devices the system has detected. Can you please post the list here just to check if something can be seen?

for lsusb, the output is here:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 04f3:0212 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0a46:9601 Davicom Semiconductor, Inc.
Bus 001 Device 001: ID 0000:0000

---

### Post by scorp123 on 2008-04-18
> **ruffshuvit said:**
> Bus 001 Device 004: ID **0a46:9601 Davicom** Semiconductor, Inc.  And so, if we search for the stuff marked bold above we get this thread:
[http://ubuntuforums.org/showthread.php?t=483189](http://ubuntuforums.org/showthread.php?t=483189)

---

### Post by ruffshuvit on 2008-04-18
nice....thats really help...thx a lot....i really appreciate it...:)

now i can used my linux back....:lolflag:

---

