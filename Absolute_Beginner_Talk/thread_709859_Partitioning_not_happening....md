---
title: "Partitioning not happening..."
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Avsfan60 on 2008-02-27
Ok, Im new here, and I read the guides and i didnt see this in there...

I have Ubuntu instilled on an older computer and dual booted with XP and runs fine. However, im trying to install Ubuntu on my machine that has 4GB of RAM and Vista Home Premium. I get to the partition the hard drive screen and i try to partition it, but it always says failed. I know I have enough room for Ubuntu to install, but it wont partition the hard drive. Is there anything I can do to override this without getting rid of Vista or any components of Vista?

Also i have the Logitech MX5000 Bluetooth desktop and when i run the Live disc, the screen goes into sleep mode but when i plug in the wireless adapter to another USB port the screen pops up but i cannot see my cursor. However, if i do not have my bluetooth adapter in, and a regular USB mouse in, the screen loads normally and the monitor doesnt go into sleep mode and i can actually see my cursor.

Thanks

---

### Post by kool_kat_os on 2008-02-27
be sure to BACKUP your vista files!!!

---

### Post by Avsfan60 on 2008-02-27
I do have all my Vista files backed up..

---

### Post by Moop on 2008-02-27
I've never used Vista but I've heard that using Vista's partitioner to create the free space for ubuntu works better than the live cd. At least some of the time anyway.

---

### Post by incen on 2008-02-27
I think that could probably be because you only have one single partition which is now occupied by Windows?! Am I right? I think it is better that you can make sure you have all Windows files in one partition and then install Ubuntu on the rest. You can either:
1. Try to partition in Windows and make sure you have all files in one part. Well... this is risky.
2. The easier/safer way to do it may be formatting all the disk and install your Windows since you already have all your files backed up. While installing Win, partition it into two part. Then, Ubuntu can be installed onto the rest of the disk.

---

### Post by Avsfan60 on 2008-02-27
I actually dont really understand the partitioning... What am I supposed to do here on the Vista partition?

[IMG]http://i28.tinypic.com/2lo6vqs.jpg[/IMG]

---

### Post by incen on 2008-02-27
So it seems to me that you already have your 60GB hard drive partitioned: 30GB for C and 30GB for D. I'll suggest you backup those files in D and release it in Windows. I don't have Vista so I don't know exactly how to do it. Try to right click on it and see the option.
Then, just put your Ubuntu CD in and try to partition on that D drive (well... you may not see it says D though). Make sure at least you have:
/           for root folder
swap     for swap  (there will be a suggested sapce size while you do partition, I think)

---

### Post by incen on 2008-02-27
Wait... wait... I think I was wrong. You have a way huge C partition... \\:D/

Yeah~ probably shrick it. :)

---

### Post by Avsfan60 on 2008-02-27
What should I reduce it too?

---

### Post by halitech on 2008-02-27
shrink it 1/3 of your drive space (is it a 300gig like I think I'm seeing?) then create a FAT32 partition for sharing of 100 gig and give Ubuntu 100 gig to use

---

### Post by incen on 2008-02-27
> **halitech said:**
> shrink it 1/3 of your drive space (is it a 300gig like I think I'm seeing?) then create a FAT32 partition for sharing of 100 gig and give Ubuntu 100 gig to use

Yeah~ this is a good idea. And you really have a big drive. The one on my laptop is only 40 GB and have to be shared by Win and Xubuntu. :p

---

### Post by bobpur on 2008-02-27
Whew! I'm glad I caught this post!
It makes me more eager to swap my brand new Vista Ultimate for my Old OEM WinXP setup. Yep! Take that Vista and put it on the shelf where I was ready to consign my XP disk and reinstall XP for another go-around. :) :)

Thanks guys!

(Well, not really, but I guess I'd better stock up on beer and nonbreakables, huh.)

---

### Post by Avsfan60 on 2008-02-27
> **kool_kat_os said:**
> be sure to BACKUP your vista files!!!

haha no problem. lol.... im thinking about deleting everything on my hard drive and just putting Ubuntu on it and say up yours Windows!

---

### Post by incen on 2008-02-27
Ha, then it becomes really easy. :p

Well... but as you showed. You already put a lot of stuff in your system drive, C. Then, I think you can just follow what Vista said. Shrink it and get the rest 54 GB space. Be sure you back up the important files. Although MS says it's safe, I'm not totally sure... :p And do it with your own risk.

---

