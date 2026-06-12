---
title: "Root wont mount?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by romUdog on 2006-10-21
I need help with installing Kubuntu 6.06 Dapper Drake. I install it and everytime i do it installs fine and finds the hard drive within the LiveCD but when i boot it after it installs it just goes to "Waiting for Root Filesystem" I need help with this as this is very annoying and i cannot get it to install ive tried both the standard LiveCD and the Alternative Install CD as well with Ubuntu and Kubuntu. Can someone help me out?

Ive installed it just fine on my other computer yet this one wont work. I have WinXP installed and im doing a Dual Boot. 

The machine Specs are as Follows:
nVIDIA GeForce 7600 GT OC
Asus P5LD2 Motherboard
Asus Quiet track DVD ROM 16x
Lite-On CD+/- RW / DVD ROM 16x
Western Digital 80GB IDE
Western Digital 320GB IDE
2GB RAM
Intel Pentium 4 Slot 775 3.2Ghz Processor
Hauppage WinTV-PVR-150
Netgear 10/100 Ethernet
Creative Sound Blaster Audigy SE

Id like help ASAP, Thanks so much in Advance!

---

### Post by Albi on 2006-10-21
Did you pick WHERE you want to install the root filesystem?

---

### Post by DaveBorealis on 2006-10-21
Hello romUdog,

When you formatted the hard-drive partition(s) during the install, did you actually assign one to '/'?  You should have formatted at minimum a 3 Gig or bigger ext3 (or whatever) partition mounted at '/', and a swap partition.

Best regards,
Dave

---

### Post by romUdog on 2006-10-21
It did it all automatically i used the resize and it did all the rest by itself. it created i believe 3 or 4 partitions

---

