---
title: "Problem booting into Ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by NNG on 2008-04-04
I recently had to completely wipe all of my hard drives and reinstall the operating systems. Before I reformatted, I had Vista Ultimate X86 and Feisty. Now, I have Vista Ultimate X64 SP1 and I have tried to install both Feisty and Hardy. 

I have been having a problem with booting into Ubuntu once I install it. I have installed Hardy twice and Feisty once and every time, the installation appears to be successful. It tells me it's successful, GRUB is aparently installed correctly and everything. However, the problem seems to be that Grub isn't overwriting the Vista MBR at all. When restarting after installation, the Vista loader boots right up and Grub doesn't even seem to exist. 

I have [tried repairing/reinstalling/whatever it is]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")grub from live CD and while it appeared to be successful in the console, it didn't do anything on restart.I have installed Ubuntu nearly a dozen times and this is the first time I've had such a problem.

So yeah, I'm stumped and I need some help :P

---

### Post by The Titan on 2008-04-04
> **NNG said:**
> I recently had to completely wipe all of my hard drives and reinstall the operating systems. Before I reformatted, I had Vista Ultimate X86 and Feisty. Now, I have Vista Ultimate X64 SP1 and I have tried to install both Feisty and Hardy. 

I have been having a problem with booting into Ubuntu once I install it. I have installed Hardy twice and Feisty once and every time, the installation appears to be successful. It tells me it's successful, GRUB is aparently installed correctly and everything. However, the problem seems to be that Grub isn't overwriting the Vista MBR at all. When restarting after installation, the Vista loader boots right up and Grub doesn't even seem to exist. 

I have [tried repairing/reinstalling/whatever it is]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")grub from live CD and while it appeared to be successful in the console, it didn't do anything on restart.I have installed Ubuntu nearly a dozen times and this is the first time I've had such a problem.

So yeah, I'm stumped and I need some help :P
I don't know anything about this but a google search brought me here  [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) Maybe it will help

---

### Post by mikewhatever on 2008-04-04
Are there more then one HDDs?

---

### Post by NNG on 2008-04-04
Yeah, 4 hard drives. I tried installing Ubuntu to two different hard drives.

Oh and, to my knowledge, BCD adds grub to the Vista bootloader and not the actual operating system so I doubt that BCD could solve the problem as GRUB is my problem. Also, I dislike BCD immensely so I just don't want to use it if it can be avoided :P

---

### Post by bt224 on 2008-04-04
You might try installing on the same HDD as Windows. Some have this same trouble and this has solved it.

---

### Post by NNG on 2008-04-04
> **bt224 said:**
> You might try installing on the same HDD as Windows. Some have this same trouble and this has solved it.

Installing it on the same HDD as Vista was my first choice and, during two of my attempts, I did install ubuntu on the Vista HDD.

---

### Post by mikewhatever on 2008-04-05
It seems the problem is that GRUB gets installed to the MBR of the wrong HDD, in other words, not the one you boot from. Grub does get confused sometimes, but there are several ways to deal with it.
--You could simply try to boot from another hdd, by changing boot order in the BIOS to see if anything other then Vista loads.
-- Another option is to disconnect all but one hdd, install Ubuntu there and then add the rest.
--Yet another option is to use a Live cd to troubleshoot config files on Ubuntu partition.

---

### Post by NNG on 2008-04-05
Thanks, I just fixed GRUB to write to HD2 and it ended up attempting to boot and then I had to fix the boot order in order to get GRUB to work properly for some reason.

But yeah, it's working now.

---

