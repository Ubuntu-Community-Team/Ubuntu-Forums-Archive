---
title: "[How-to] Fix Vista boot using Ubuntu Live CD"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by DaHiA on 2008-03-15
Hello,
My Toshiba laptop HDD is divided into 2 partitions 
One for Vista 110GB and other for backup and restore 1.5GB

Recently, i tried to get into linux world through ubuntu sweet gateway
I installed unbuntu 7.10 using Live CD onto my 4GB USB flash drive -Not my HDD as i was afraid to mess with my data-

Later on, i sold that USB flash memory and i was shocked when i found that my laptop can't boot Vista  from first hard drive giving GRBU error 21

I plan to use WUBI for dual boot but i can't do that until i get fix Vista boot and access it.
Any idea how to fix Vista boot while using ubuntu live CD with no installed ubnutu ?

All hints will be highly appreciated.
Thank you in advance

---

### Post by reyhan on 2008-03-15
maybe you must use recovery console, does Vista have recovery console on its DVD?
if Vista had, use the recovery console and type this ```
fixmbr
```
i hope thats work:)

---

### Post by gfg on 2008-03-15
I know you can install grub from the livecd. What i'm not sure of is if it will detect the Vista install. Anyways here is a link explaining how to install grub from the live cd [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by louieb on 2008-03-15
The Ubuntu live CD does not have the software to put Vista's bootloader code back in the MBR. However the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") can and heres a few other ways to do it too [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by PinkFloyd102489 on 2008-03-15
If you google Vista Recovery CD, there's hundreds of boot CDs to where you can boot from the disc and recover the MBR.

---

### Post by forrestcupp on 2008-03-15
> **louieb said:**
> The Ubuntu live CD does not have the software to put Vista's bootloader code back in the MBR. However the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") can and heres a few other ways to do it too [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

+1 for Super Grub.

I went through this a while back and Super Grub is the **only** thing I found that got it to work.  Just make the CD, boot to it, and find the option to restore the Windows boot loader.

---

### Post by DaHiA on 2008-03-16
Thank you everybody :)

> **PinkFloyd102489 said:**
> If you google Vista Recovery CD, there's hundreds of boot CDs to where you can boot from the disc and recover the MBR.
I figured out to solve my problem by using Vista recovery DVD and i'll explain how to for any users might have/will have the same issue.

-Boot from your Vista recovery CD/DVD
-follow instrauctions till you reach repair windows option
-Select command prompt 
-goto the Vista partition , say c:
-run the following commands
bootrec/ fixboot
bootrec/ fixmbr

-and you are done :)

---

