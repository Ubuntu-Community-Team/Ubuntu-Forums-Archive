---
title: "Uninstalling Ubuntu"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by arielb_86 on 2007-06-08
Due to some lack of space and such in one computer i need to uninstall Ubuntu.

I have one physical hard drive with the partitions. I can delete the ubuntu partitions but how will i fix the master boot?

i dont have the actual XP CDs since i bought this from hp and all i have are HP recovery disks

---

### Post by Bohlio on 2007-06-08
I think you just delete the partitions. Then to fix the MBR, can you get grub on a floppy in order to boot into windows?

---

### Post by arielb_86 on 2007-06-08
its a laptop(stupid technolgy) i dont have a floppy drive.

i do have a WXP SP1 CD but its not an SP2...will that work??? Can you explain a little bit more on how to do the fdisk?

---

### Post by tahuya_rat on 2007-06-08
I believe all you need to do is boot to the recovery cd, choose "Restore", or some such, and you're golden.  This, of course, assumes that you have backed up all critical data, so if not, then let us know what you would miss if it all went away...:popcorn:

---

### Post by yurimxpxman on 2007-06-08
> **arielb_86 said:**
> Due to some lack of space and such in one computer i need to uninstall Ubuntu.

I have one physical hard drive with the partitions. I can delete the ubuntu partitions but how will i fix the master boot?

i dont have the actual XP CDs since i bought this from hp and all i have are HP recovery disks

It's been a very long time since I've booted a Windows disk, but if my memory serves me right, it goes like this:
[LIST]
[*]Boot XP disk
[*]Press R for the recovery console
[*]Logon to your installation
[*]Type **fixboot**
[*]Type **fixmbr**[/LIST]

---

### Post by RedRover1 on 2007-06-08
Try taking a look at these links for possible options.  Since you don't have a floppy you could burn to a CD and boot that if you want to try the second link.

[http://answers.google.com/answers/threadview?id=215902]("http://answers.google.com/answers/threadview?id=215902")

[http://www.softwaretipsandtricks.com/forum/windows-xp/3423-windows-xp-wont-boot-mbr-problem.html]("http://www.softwaretipsandtricks.com/forum/windows-xp/3423-windows-xp-wont-boot-mbr-problem.html")

---

