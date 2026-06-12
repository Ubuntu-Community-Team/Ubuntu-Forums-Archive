---
title: "Install questions, partitioning, dual monitors, webcam etc."
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Mischief on 2007-01-05
Hi!

After repeatedly failing to boot the Live CD on my laptop I popped it into my stationary and it booted up right away. I must say that I'm impressed! Just the look and feel of Ubuntu was a totally new experience and I decided within a minute to install it. Ubuntu looks "fresh" in comparison with XP and there seems to be so many advantages compared to XP. I still need to keep an XP install since I need it for a couple of pieces of Windows software though.

1. If the Live CD booted up perfectly, except for my CRT monitor crapping out, does it mean that the complete install will go just as smooth? I'm used to dual monitors in XP and like to keep it that way but I get a GNOME error on the CRT, the TFT worked perfectly when booting. Is this due to Ubuntu only recognizing one monitor or did it try to boot in clone mode but failed on the CRT?  

2. Even though this has been asked so many times before, I'd like some help with partitioning layout.

These are my two SATA hard drives and I've planned them after the great guide from
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Does the following layout look ok to you?

**SATA 160 gb (primary)**
XP (NTFS) 			- 30 gb
Ubuntu (EXT3) 		- 20 gb
Ubuntu Home (EXT3)	                - 5 gb
Swap 			- 3 gb
Shared (FAT 32)		- 100+ gb

**SATA 160 gb (secondary)**
Shared (FAT 32)		- 160 gb

I've backed-up everything I need to save to an external drive. Would the "right" procedure be to completely erase the two disks, partition 30 gb on primary and then start by Installing XP to that partition? After that, will it work to start the Ubuntu installer and take care of the rest of the partitioning from the Ubuntu installer? 
Also, should I assign more space for the "Ubuntu (EXT3)" partition?

3. Since I'm in a long distance relationship, I talk a lot to the GF via webcam in MSN (Logitech Notebook Pro Webcam). Is there an application available that will be able to communicate with MSN via webcam and will the webcam work at all in Ubuntu? I did a search for webcam support and some people were able to install Logitech webcams, couldn’t find anything regarding the webcam I have,

Thanks for your help!

---

### Post by CroEragon on 2007-01-05
If you have everything backed up and need no data from discs best procedure would be to delete your whole disc and all partitions. Then you first install Win XP and with qtparted make rest of partitions except ext3 and swap and run Ubuntu installer and give all unallocated space to ubuntu main partition i home partition (but i dont se point of such home partition, it is obvious that you will keep your data on fat32 partitions).
20gb is more than enough for Ubuntu. It is not Vista it can run fine with as much as 4gb.

I dont know about dual-monitor but there is great HOWTO about it in HOWTO section you should check it out.

I have Logitech desktop webcam( i dunno what type) and i didn't test it yet but i can see it is automatically installed. Also im sure there is MSN program that can handle MSN video protocol. Search in synapatic.

---

### Post by Mischief on 2007-01-05
I was just thinking that FAT32 is unable to handle files larger than 4gb.
Should I increase the size of the "home"-partition to keep large files there and decrease the size of the "Ubuntu"-install directory? I read at the guide that the "home"-partition is similar to Windows "My Documents".
How much space did you guys allocate for the Ubuntu install partition? 

Do I run "QTParted" after the Install is complete? I don't really follow your partition explanation.

---

