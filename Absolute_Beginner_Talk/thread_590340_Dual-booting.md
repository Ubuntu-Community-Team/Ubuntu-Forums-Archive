---
title: "Dual-booting"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by vx1 on 2007-10-24
Hey,
I have a few questions about installing Ubuntu 7.10 to a separate partition and dual-booting.

I currently have Vista installed, and three partitions.
One is C:
One is D: (Recovery)
One doesn't have a name.  It's just blank.  I don't seem to be able to access it and I don't know what it is, but its status says Healthy (EISA Configuration) and it takes up 55MB.  Does anyone know what this is or if I need it?

Ok, so what partition changes do I need to make to install Ubuntu, and when/where should I make them?

Also, I have dual drives.  They were in a RAID 1 configuration, but I'm not sure if it's still set up.  Is there a way I can check, and if they are, do I need to make any changes or set anything up here before installing?

I hate to be a pain, but please be specific when you can.  Sorry if these are silly questions, I just want to be completely clear on how to do this.  My last two attempts failed *very* miserably.  I've just gotten up the nerve to try again.

Thanks very much.

---

### Post by Pumalite on 2007-10-24
Use Vista partitioner to make space for Ubuntu. Then follow this Guide:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by riminicat on 2007-10-24
Hey vx1
       I'm not sure, but it is possible that the partition that you can't access is a system's diagnostics type of thing.  I have one one on my laptop that I can't access but it's configured not to even show up in windows.  If no one answers you I will ask the guys at work tomorrow.  I work for a campus tech support thing and most of my coworkers use Windows Vista and would know about this.  One question tho, what kind of computer do you have? If you don't mind sharring.

---

### Post by daimaru on 2007-10-24
this is how i do it. i use partiton magic to make 1 swap partition (2x size of RAM) format as swap, 1 root partition ( / ) formated as ext3 for the system, and 1 /home partition formated ext3 too, for my user files. this way i can reinstall ubuntu without having to move my files that are located in /home. 
when u install choose manual partition setup and right click the b4 created partitions (root, home and swap) select the mount point for them (for root --> /  ; for home  --> /home ; swap --> swap )
then install at end say yes to the question if you want to write master boot record (MBR) to your disk. 
done

hope that works , but im not using raid or vista so maybe you should check if there is any extra stuff u have to do for that.

EDIT: oh yeah your recovery partitions i never use them i formatted whole hd and then installed windows on it because i dont like the recovery stuff, but if u didnt get an orginal copy of windows, only a recovery cd or ur system was preinstalled then you have to keep it.

---

