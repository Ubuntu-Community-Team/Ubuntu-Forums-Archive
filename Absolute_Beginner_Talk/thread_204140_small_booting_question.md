---
title: "small booting question"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-26
I have winxp and ubuntu 6.06 duble boot.
before I installed ubuntu I changed my winxp "booting name" to MAXDDARK
it did it modifing the file "boot.ini"
like this :
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=**"MAXDDARK"** /noexecute=optin /fastdetect

but now that I have ubuntu it would be easier for me that "winxp" instead of "maxddark" would be displayed at boot start.
so I have changed it back like this :
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=**"windows xp"** /noexecute=optin /fastdetect

but for some reason the boot still displays "maxddark" and not "winxp" as it is in the boot.ini file.
why ?
should I change somthing on ubuntu too ?

---

### Post by tonyr on 2006-06-26
When you installed Ubuntu, the name **maxddark** was probably copied from the
Windows boot information into the GRUB boot file.  Edit /boot/grub/menu.lst
and look for **maxddark**.  If it is there you can simply change it to 
**windows xp**.  You must be **root** to edit that file, and you usually
do it in a terminal (Applications->Accessories->Terminal) using **sudo** like this:
```

sudo vi /boot/grub/menu.lst

```

You can use an editor you are familiar with.  I'm a **vi** kind of guy.

---

### Post by MaximB on 2006-06-26
thanx..I thought I should edit somthing on ubuntu   :)

---

