---
title: "Linux works, now XP wont boot becuase no hal.dll"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Shakedown on 2007-04-19
So I partitioned my HD with GParted off the LiveCD, Ubuntu works, but when I choose to load XP it wont becuase im missing hal.dll.  I've only been able to find out how to fix this when you have the XP cd, but I dont have any XP cd or disks.   So what do i do??  HELP!!

---

### Post by oilchangeguy on 2007-04-19
read this:
[http://support.microsoft.com/kb/314477/en-us](http://support.microsoft.com/kb/314477/en-us)

---

### Post by Shakedown on 2007-04-19
I only see how to fix the problem from within XP or with an XP boot disc.  I need to fix this some other way

---

### Post by oilchangeguy on 2007-04-19
can you use a friends disc?

---

### Post by Shakedown on 2007-04-19
I dont know anybody with a disc.  If I found one would that work? Wouldn't I need the disc that was used to install my XP?

---

### Post by oilchangeguy on 2007-04-19
an xp disc is an xp disc. the unique thing is the product key which is located on a sticker afixed to your computer.
try this:
[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)

---

### Post by Shakedown on 2007-04-19
I looked into my system32 file from Linux and I do have the hal.dll file, so this means that something is wrong with my boot file?  Now what!?

---

### Post by Shakedown on 2007-04-19
Bump Help!

---

### Post by Shakedown on 2007-04-19
my roommate has a burned Windows XP Home Edition 64-bit cd, would that work?

---

### Post by DreamcastJack on 2007-04-19
this is why i would never duel-boot w/ windows, it may get screwed up and your out 100 bucks at times, Vista duel-boot not a chance.  but w/ Linux and Linux duel-booting I think is safer.  but can be annoying.

---

### Post by Comzee on 2007-04-19
> **DreamcastJack said:**
> this is why i would never duel-boot w/ windows, it may get screwed up and your out 100 bucks at times, Vista duel-boot not a chance.  but w/ Linux and Linux duel-booting I think is safer.  but can be annoying.

Dual boot does not screw up anything. But there is a process to it.

Partition an NTFS chunk for windows. Leave at least 2gb free for Ubuntu. Do not partition the space.
After XP is installed, boot from the Ubuntu CD. Select the manual partition setup. With the unpartitioned space set at least 512mb for Linux-swap. Set the rest for EXT3. Proceed to install Ubuntu.

Ta-da, Your done.

---

### Post by fokuslee on 2007-04-20
you can install windows before or after the Linux Partition if you install linux infront of windows windows boot.ini will be corrupt cuasing the hal.dll error b/c ini is no longer pointing to the write parition to locate ntldr and all the other good stuff 
so you just edit the boot.ini and u should be good to go 
but first you have to get ntfs write support
just follow this guide i use to have the same problem before
[http://ubuntuforums.org/showthread.php?t=327386&highlight=hal.dll+missing](http://ubuntuforums.org/showthread.php?t=327386&highlight=hal.dll+missing)

---

