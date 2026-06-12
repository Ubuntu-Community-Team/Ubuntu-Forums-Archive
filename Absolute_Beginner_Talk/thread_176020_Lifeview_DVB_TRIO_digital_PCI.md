---
title: "Lifeview DVB TRIO digital PCI"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by 5jarinko on 2006-05-14
I have a satelitte card. is there any driver on this card???
what kind of software is the best to see satelite programs,

---

### Post by kb3hkg on 2006-05-15
I believe in oreder for anyone to help you more info about the card you have is necessary.

---

### Post by easyease on 2006-05-15
try kaffeine, it works for my dvb device, you might need to get xine engine for it from  
 synaptic but its the only way i got my device working. it works very well and is very functional to, better than the windows software i got with the dvb device.
 "sudo apt-get install kaffeine-xine"  from a terminal.

---

### Post by leo_m on 2006-07-05
Compile the latest kernel 2.6.17-3, there is support for Lifeview DVB Trio in that version.  See the CARDLIST.saa7134 file as well (in the kernel source/Documentation hierarchy).

---

### Post by takymetri on 2007-06-29
> **easyease said:**
> try kaffeine, it works for my dvb device,



LifeView Trio include T- and S-receiver.

Yes i install too Kaffeine + xine + v4l-DVB in my system(Feisty) and now can see T-channel very well.
But i want see S-channel too.

How i can install both channel S+T to ubuntu/Kaffeine or what is best -> VDR?

Also Trio include remote control + IR adapter.
Can ubuntu/Kaffeine or what is best VDR use that remote control?
If how it install in my system?

---

