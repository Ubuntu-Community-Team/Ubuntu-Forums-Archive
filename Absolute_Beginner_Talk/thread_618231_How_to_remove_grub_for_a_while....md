---
title: "How to remove grub for a while...?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by joanaomgod on 2007-11-20
Hello!
I have one problem. I am using Ubuntu 7.10 and i like it, but i have and Windows XP, i dont use it, but my parents use it. however, i have to reinstall windows xp(the worst os!!!) because there are a lot of problem with it... but, i put my windows xp cd, restart my pc, and on start up, when start to boot from cd, there is only black screen. My friend told me that this is because grub dont like windows xp cd :D If it so, is there a way to uninstall grub, but after i resinstall windows, to turn on grub again, the most important is my ubuntu do not go to hell... I am sorry for my english, but i am from bulgaria and i dont speak eblgish well.

---

### Post by bumanie on 2007-11-20
As far as I know, what your friend has told you is not correct. Windows normally will still install whether grub is there or not. In fact, it is a common problem for people to have 'lost' grub after a windows install. This is because windows is programmed to think it is the only thing that's important and it overwrites the mbr, hence making grub no longer function. Why you are getting a black screen with the windows cd - I have no idea. Give it another go. Hopefully it was a one off glitch.

---

### Post by joanaomgod on 2007-11-20
i tried a hundert times... nothig... please, any body knows? :(

---

### Post by Skefflock on 2007-11-20
Hi, there's shoudn't be any problem installing WinXP this way. The only one - you'll lost grub after that, so read this also [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351"). It's how to restore grub.

---

### Post by Skefflock on 2007-11-20
Do you have an original CD with XP? Or have you ever installed XP on this machine and(or) from this CD?

---

### Post by joanaomgod on 2007-11-20
nope :confused: but my installed copy is not the original, and i have installed it with the same disk, i tryed with another... but only black screen

---

### Post by joanaomgod on 2007-11-20
on the last reinstall, i haven't ubuntu...

---

### Post by Skefflock on 2007-11-20
There's a way to install XP, but you still have to boot into DOS-like system from any media. It could be flash or floppy. You can also download someking of booting-only tools, like Hiren's Boot - this one is my favorite.
So what would I do if I were you:
- I would create a separate partition which is windows only (NTFS, but fat32 is better, cause it is not easy to use NTFS from DOS) and copy the i386 folder from installation CD to that partition.
- then start the machine from anything you want but to got a dos command line. There's a variety of disk images that are only 1 Mb long. You can easily got one from net.
- Go to that folder and run "winnt". That will start the installation.

---

### Post by natehatewindows on 2007-11-20
are you sure the disk is good?

---

### Post by Skefflock on 2007-11-20
If you have another PC with Windows on it, than [http://www.bootdisk.com/bootdisk.htm/]("http://www.bootdisk.com/bootdisk.htm/")here's alot of floppy images, you can create on that PC. Just insert a floppy and start the .exe file.

---

### Post by Skefflock on 2007-11-20
> **natehatewindows said:**
> are you sure the disk is good?
If there's working system that was installed from this CD, then probably it is OK.

---

### Post by natehatewindows on 2007-11-20
yeah, i mean is it really sctatched or something,,,,i would just o the boot disk thing,

---

### Post by natehatewindows on 2007-11-20
adn maybe check the bios settings? just a thought....its where i would start.

---

### Post by dnns123 on 2007-11-20
You can do it the long way... It needs a fairly large harddrive
Back-up your data and nuke your harddrive and use the Live CD and use GParted (partitioner) and make 3 partitions.
1 for Ubuntu (Empty for now)
1 for your data (NTFS or FAT32)
1 for Windoze Ekspee (NTFS)

You should know which partition is for which by the size of the partitions. Exit the Live CD and insert the windoze CD. Enter the DOS installtion until the part where you choose the partition for installtion. You should know where now by just the size of the partition. Install windoze after choosing and just install everything your parents need. (antivirus, office, drivers, etc.) After that exit windoze and insert the Ubuntu CD. Just go through the installtion steps until you reach the page where you choose the Boot Partition (where you Filesystem will be installed) Sinse one of the spaces of your harddrive is blank, just choose the option where you install it to the blank part. After installation, use NTFS-config and mount the partition where your data should be put. (not the windoze partition please. Put all your data there.

The thing with this set-up is that Ubuntu will only be able to use the data partition and Windoze can only detect the other NTFS partition, not the ext3 partition. You can use your data and your parents can use the same partition in Windoze. Both OS will not disturb the other.

Windoze should be installed first because Ubuntu was build to be able to dual-boot.

I'm not sure if you did this already, but I plan to do this once my new harddrive arrives.

---

### Post by gupta_sumesh63 on 2007-11-20
Check your Bios. That'll solve your problem I think.
After Switching on the PC press delete. You'll be taken to your Bios.
Change your values to default.
Check if your first booting device is CD/ROM/DVD-ROM.
If not, then change it to CD-ROM drive as first booting device.
Save and quit BIOS screen.
Put your Windows CD and boot.
I hope it works.
All the best.

---

### Post by joanaomgod on 2007-11-20
> **gupta_sumesh63 said:**
> Check your Bios. That'll solve your problem I think.
After Switching on the PC press delete. You'll be taken to your Bios.
Change your values to default.
Check if your first booting device is CD/ROM/DVD-ROM.
If not, then change it to CD-ROM drive as first booting device.
Save and quit BIOS screen.
Put your Windows CD and boot.
I hope it works.
All the best.
I was sure that the problem is not from this, i tried and nothing happens, only the same black screen... i forgot to tell that when i press any key to continues when it ask me(in the boot), on the top of the screen, above the other standart chars, it types  "Setup is configuring your pc configuration" and after a 2 seconds the screen go to hell, black screen...

@dnns123 - you dont understand me... i cant get to the windows setup :(

---

### Post by Skefflock on 2007-11-20
That's weird. I've never seen anything like that, though have installed XP on a couple hundred different systems I think. That's strange. So whether the CD is corrupted or you have some hardware issue (from the XP point of view). The thing that is come to my mind, that you may have a conflict at hardware level. Between CDrom and HDD for example. By the way, what's you specs? Do you have anything unusual for a desktop computer like raids or SCSI drives?

---

### Post by joanaomgod on 2007-11-20
> **Skefflock said:**
> That's weird. I've never seen anything like that, though have installed XP on a couple hundred different systems I think. That's strange. So whether the CD is corrupted or you have some hardware issue (from the XP point of view). The thing that is come to my mind, that you may have a conflict at hardware level. Between CDrom and HDD for example. By the way, what's you specs? Do you have anything unusual for a desktop computer like raids or SCSI drives?btw, a have changed my mother board before 3 mounts, and yesterday a new cd/dvd drive, on my old cd/dvd drive the problem was the same(it has a lot of problems), i told that if i change it, the problem will no more... the last reinstall was when i put my new mother board... i dont know what to think... :( New hardware, many problems :( I use windows only for Adobe Fireworks CS 3, for my staff, but my parents have a work on this creature...

---

### Post by Skefflock on 2007-11-20
Ok, it did work with previous MB. But does not now. Am I right? Have you changed memory or CPU? Do you know if the MB bus speed is the same as you memory's one? Or does you MB officially supports you memory type?

---

### Post by joanaomgod on 2007-11-20
No, when i put new MB, i have to reinstall windows the changes to take effect(this must do if you move your mouse in windows :) ) and then i reinstall it correctly when i put linux, i cant reinstall windows... My sweet Ubu, don't be jealous...

---

### Post by Skefflock on 2007-11-20
So did it ever work on new motherboard? Couse it seems like a hardware issue. Ubuntu has nothing to do with it, no does grub.

---

### Post by joanaomgod on 2007-11-20
> **Skefflock said:**
> So did it ever work on new motherboard? Couse it seems like a hardware issue. Ubuntu has nothing to do with it, no does grub.It cant be that... ou... please tell me that uhbuntu is, please, because i install one windows xp on this mother board, if it is broken, this will be my second mb for 3 months, i don't think that in the firm, from where i buy this pc gonna like something like this: 2 years: 2 mother boards, one cd/dvd+rw drive - broken down... if there is an other solution... :(

---

### Post by Skefflock on 2007-11-20
That got to be somekind of a conflict. Check MB bus's and memory speeds. And make sore they are equal or at least that MB does support you type of mem.

---

### Post by joanaomgod on 2007-11-20
> **Skefflock said:**
> That got to be somekind of a conflict. Check MB bus's and memory speeds. And make sore they are equal or at least that MB does support you type of mem.but this is not logical... 2 months before with the same pc, absolute the same, after the change of MB, i install a fresh copy of windows, now i am trying, and it's go to hell... it's just not logical...

---

### Post by joanaomgod on 2007-11-20
from another forum told me that if i reset bios, can fix this, how to reset bios? what is the risk of reseting  bios? is there i little bit of truth in this?

---

### Post by gupta_sumesh63 on 2007-11-20
I dont find any risk in changing Bios.
Change all the values to default and then try to install XP.
By the way check your partitions with gparted. Gparted is self booting. Check if the NTFS partition exists or not. Maybe it does not exist.
Create one using Gparted and then boot with XP CD.
However it is advisable to first check threads for partitioning before going for it.
Best of luck.

---

