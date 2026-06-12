---
title: "Cant copy files to external disc"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by baysl on 2006-11-21
I have external 160GB disc which is formatted in NTFS.

Now I want to copy files from disc where linux is installed
to the external drive(it says 160GB is read-only).

What do I have to do, to be able to copy files to that 160GB disc?

---

### Post by SoggyCornflake on 2006-11-21
NTFS is Microsoft's best tool to keep people from moving to Linux in my opion.  I'm pretty sure that writing to an NTFS partition is still experimental.

You have a couple options that I can think of and they're both painful.  (Hopefully somebody has a better suggestion.)

1.  Pull all the data off the portable hard drive, and reformat it as FAT32 or, if you're only going to use Linux, EXT2.

2.  Compile a kernel that has NTFS writing support.

(This second choice is not super painful, but even if you're not shy about compiling a kernel, you still may have problems since it's experimental)

---

### Post by kartikya on 2006-11-21
create on any of your panels a "custom aplication launcher" 
 call it whatever you want but for command put: gksudo nautilus
 you can now acess your harddisk in root and can copy and edit whatever you want 
 I hope this fixes your probs....

---

### Post by 900i on 2006-11-21
Junk NTFS, solution as above.  To make disk Read/Write, "sudo chmod 777 /media/usbdisk" in a terminal.  This makes it Read/Writable by anyone not just root.

---

### Post by LLRNR on 2006-11-21
This is something I didn't test myself and it's not really recommended since it's still in a development phase, but in the worst case scenario there is [NTFS-3G](https://wiki.ubuntu.com/ntfs-3g). (I won't advise you to use it since I never tried it myself but there are some that say it works ok while others say it doesn't...) Here is a [thread](http://ubuntuforums.org/showthread.php?t=304026) on NTFS write access, too.

HTH,

LLRNR

---

### Post by SoggyCornflake on 2006-11-21
Here's the a link to 
[HOW-TO NTFS Write Access.]("http://ubuntuforums.org/showthread.php?t=217009")

It does stress that it is experimental, but apparently some people have had success.

Whatever you choose to, I suggest you start with backing up your external hard drive first.

---

