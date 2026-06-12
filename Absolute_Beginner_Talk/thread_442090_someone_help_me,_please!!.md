---
title: "someone help me, please!!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by mattyb1123 on 2007-05-13
I recently received an older computer from a friend of mine, and I wanted to install Ubuntu on to it. 

I requested a CD from Ubuntu and recieved it in a few weeks. I Currently have WINXP running on a drive and I wanted to install LINUX Ubuntu to another drive, Not the duel Boot Type install. 

I went into WINXP and formated the drive to FAT32, and then switched the new drive to the master, and ran the live CD. I then Went in to install and went through almost all the steps, But when It came to the part where Linux would install on the hard drive, it pauses searching for the drive and wont continue.  I looked in the Drives area and it cant find any information on the drive. I'm not sure how to mount the harddrive or anything like that. I know a lot about windows, but when it comes to LINUX i know very little. 

I hope some one can help me. Anything would be appreciated 

~Mattyb

---

### Post by smoker on 2007-05-13
is your new drive showing ok in the bios? and did you change your xp drive to slave when you made the new drive a master? also, position on the ide cable counts (if ide drives), the master should be at the end of the cable, slave in the middle if both connected to the same ide channel.

---

### Post by Tux Aubrey on 2007-05-13
More importantly, why are you doing it this way?

Ubuntu is quite happy on a slave drive and will dual boot that way with XP.  If you think at some time you might want to revert to a windows-only system you will just need your windows installation disk to fix the MBR and remove Grub.

I have seen a lot of posts here from people who seem determined to have totally separate installations and then complaining that they have to enter the bios configuration every time they boot.  I just don't understand why you would want to complicate things like this.  That said, I'm sure it can be done.

Good Luck

---

### Post by mattyb1123 on 2007-05-13
I'm enabling a switch between my jumpers, so i can switch a slave to a master disk. I wanted to have the option to switch to linux boot without a boot manager. In other words, switch one way - Linux switch the other way - XP. 


I'm trying a few different things on it right now.

---

### Post by mattyb1123 on 2007-05-13
i feel like a dumb ***!! I didn't have my jumpers set right. 

I seems to be installing right now...

But what if i wanted to install a second linux distro on that drive would i have to partition the drive in half?

---

### Post by skwishybug on 2007-05-13
Either in half, or at least create space for it. Similarly to how you cannot install XP and Vista on the same drive on the same partition, you cannot install two different distributions on the same partition. Remember that each distribution, while based off the Linux kernel, is a totally different OS.

That said, if you want to play with some other distributions and not go through the joys and tribulations of partitioning and installing all the time, try a virtual machine. VMWare and VirtualBox are two good options that allow you to run one OS inside another one.

---

