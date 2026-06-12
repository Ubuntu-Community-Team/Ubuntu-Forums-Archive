---
title: "Super Grub Disk 0.9667 Fixed an important BUG"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by adrian15 on 2007-10-29
Hello Ubuntu users,

    I was trying to fix a boot myself and I decided to use [Super Grub Disk]("http://supergrub.forjamari.linex.org") interface  instead of using directly the grub command line as I always do because it is quicker.

I was upset when I saw that my grub was installed to my second hard disk instead of the first hard disk because the grub files were in the second hard disk!   :oops:

  Those of you that you have tested SGD recently and have Linux installed in a second hard disk would have seen that SGD seems to work but in fact when you reboot you see no GRUB menu at all. The reason is that SGD installed Grub to your second hard disk :(.

Super Grub Disk 0.9667 addresses this problem installing grub to hd0 (the first hard disk) always.

Super Grub Disk 0.9667 in Cdrom, Floppy and Usb versions are available at the :lolflag:   [super grub disk forjamari download site. ]("http://forjamari.linex.org/frs/?group_id=61") :lolflag:

I have checked the bug and it seems that it has been there for many and many versions. 0.9590 version which it is quite old version has also this bug.

I am very sorry. ](*,)

adrian15

P.S.: If you have two hard disks and SGD 0.9667 does not work for you I am willing to help you with your problems. But do not post here about SGD general problems. You can use the [Super Grub Disk forum]("http://forjamari.linex.org/forum/forum.php?forum_id=235") for that. Just comment about configurations that are fixed with this new release or don't get fixed or something like that. One more thing: Do not reply with comments like Thank you for program and your program is wonderful and do not worry this bug SGD has always worked for me and so on. Please let's focus on the bug please. Thank you.

---

### Post by Denn1s on 2007-10-29
in a desktop i have a 80 GB hard drive just for data wich is the master art the IDE cable, and also my first hard disk, linux and ubuntu are installed at the second hard disk and in fact super grub disk fails to reestore grub, UNLESS i do reestore many many times in a row, its a preety ambiguos solution but hey, it works, ill post you the version i use, i dont have it at hand now, but its preety old, one of the firsts

---

### Post by adrian15 on 2007-10-30
> **Denn1s said:**
> in a desktop i have a 80 GB hard drive just for data wich is the master art the IDE cable, and also my first hard disk, linux and ubuntu are installed at the second hard disk and in fact super grub disk fails to reestore grub, UNLESS i do reestore many many times in a row, its a preety ambiguos solution but hey, it works, ill post you the version i use, i dont have it at hand now, but its preety old, one of the firsts

Your setup is exactly the one that addresses this fix. 

It's interesting what you say about restoring many and many times in a row. I might have some problem with variables when they are used too many times. Maybe variables loose their values? I do not know. You could run set before and after this "many times in a row" restore to see if any variable is unset, but I think it is not an important thing. So if you do not test it it does not mind.

I am awaiting your answer. SGD 0.9667 should install grub to the first hard disk with only running Fix Boot of Linux (GRUB) once. ;)

adrian15

---

