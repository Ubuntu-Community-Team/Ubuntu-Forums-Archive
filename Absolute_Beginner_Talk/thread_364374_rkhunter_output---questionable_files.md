---
title: "rkhunter output---questionable files"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-02-18
Hi all,

Just ran rkhunter to check for rootkits and received the following warning:

> * Filesystem checks
   Checking /dev for suspicious files... -e                      [ OK ]
   Scanning for hidden files...-e                                [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

Anyone know what these directories and files are? All the other checks appeared normal. 
Thanks for any info.

Jim

---

### Post by TheWizzard on 2007-02-18
> **jamere said:**
> Hi all,

Just ran rkhunter to check for rootkits and received the following warning:



Anyone know what these directories and files are? All the other checks appeared normal. 
Thanks for any info.

Jim

[http://www.google.com/search?q=/dev/.static+ubuntu+rkhunter](http://www.google.com/search?q=/dev/.static+ubuntu+rkhunter)

---

### Post by jamere on 2007-02-18
thanks wizz

---

