---
title: "Where Did My Windows Go?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by signal99 on 2007-12-29
I hope I didn't do something to wish I never even attempted to use Linux!

On my HP desktop which was running Windows XP, I attempted to load Ubuntu 7.10 just like I did on my laptop. The software offered me to partition the hard drive keeping Windows XP in place and adding Ubuntu. No problems with my laptop, but now on my desktop, the install went fine but I can't find anything about my Windows XP? It won't even show up in the boot menu?

Did Linux erase all of my Windows XP and everything else that was on my hard drive? Music, photos, etc? I don't even want to think about the chance of loosing everything?

---

### Post by overdrank on 2007-12-29
> **signal99 said:**
> I hope I didn't do something to wish I never even attempted to use Linux!

On my HP desktop which was running Windows XP, I attempted to load Ubuntu 7.10 just like I did on my laptop. The software offered me to partition the hard drive keeping Windows XP in place and adding Ubuntu. No problems with my laptop, but now on my desktop, the install went fine but I can't find anything about my Windows XP? It won't even show up in the boot menu?

Did Linux erase all of my Windows XP and everything else that was on my hard drive? Music, photos, etc? I don't even want to think about the chance of loosing everything?

Hi and one sure way to know is post the output of  this command in the terminal
```
sudo fdisk -l
``` that is a lower case L

---

### Post by microcronz on 2007-12-29
I was wrong.  :P

---

### Post by signal99 on 2007-12-30
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24136   193872388+  83  Linux
/dev/sda2           24137       24321     1486012+   5  Extended
/dev/sda5           24137       24321     1485981   82  Linux swap / Solaris

---

### Post by The_Dud on 2007-12-30
After doing "sudo fdisk -l" myself to see what someone who only has Ubuntu on they're HD, and getting close to the same output. (different HD size more or less)

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005a55f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris


So unforturnatly, yes, most likely you did unknowingly reformat over Windows.

You can try reading [this article here.]("http://www.ubuntu-rescue-remix.org/node/31") And you can also try what it says about foremost, to get the files back if you need anything really bad off that drive. I'm not exactly sure how reformating affects files, but if it's like "deleting" them, then there's a good chance that you'll get some of the stuff off of there. Just remember, if you're gonna try to get a file, try not to put it on the drive that you're getting it from. There's so much more the chance that you'll write over the data for a different file that you may want.

Found another better link: [Ubuntu Documentation]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Sef on 2007-12-30
check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or [System Rescue]("http://sysresccd.org/Main_Page") to recover your lost partition.

If you do want to try Ubuntu, read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

