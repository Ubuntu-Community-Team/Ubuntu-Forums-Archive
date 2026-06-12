---
title: "New installation with a raid 1"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Robbyx on 2006-08-13
I am about to install Ubuntu for the first time. I have as Asus P5B which permits raid 1, but I think it is only in software. I have 2 sata drives in the machine. They are to be the raid drives. I propose to install Ubuntu on one of the drives. How do I then set up the raid 1? 


Robin

---

### Post by Robbyx on 2006-08-14
Can I please have a reply?

Robin

---

### Post by soutSA on 2006-08-14
I have never installed a software raid and would prefer to have a Hardware Raid, but here is something that might help.

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html)

or

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.6](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.6)

hope that helps;)

---

### Post by Robbyx on 2006-08-14
I think I have misunderstood what I have here in this P5B board by ASUS. This is because it talks extensively about installing drivers for raid so I assumed it was a software installation. I no longer think that is the case because it states

JMicron JMB363 Serial Rade connector (7 pin sata_raid)

This connector is for a serial ATA signal cable. This connector supports a serial ata hd that you can configuer for raid through the onboard serial ata raid controller.

So it seems  I have a hardware raid controller. 

How do I make Rade 1 work with this controller?

Robin

---

### Post by Encryptor on 2006-08-14
JMicron JMB363 is not supported in kernel version prior to 2.6.17.8 (if i remember correctly). The current solution is: Wait for ubuntu 6.10 :(

---

