---
title: "Installing on an Old World Mac"
date: 2006-02-22
forum: Apple PPC Users
---

### Post by smileyme on 2006-02-22
First I want to make clear I'm absolutely new to Linux. I've managed to put Breezy on a PC with minimal problems, and have read many pages on installing Linux on Macs.

I am trying to put Breezy PPC on an AIO, Rev 1, 333 MHz. As instructed, I partitioned the drive with a minimal partition for OS9, leaving the rest of the 4 GB ATA drive unallocated. The install goes fine through the formatting of the unallocated space, providing me with HFS on /dev/hdc6, Ext 3 on /dev/hdc7, and swap on /dev/hdc8. When I get to the point of working in the CLI, which I get to via option + F2, and having created "target" and "mkdir", etc. according to the directions, I get stuck trying to copy boot/vmlinux to the System Folder on hfs (/dev/hdc6) the message says "Unable to open hfs System Folder/Linux Kernels/vmlinux" no such file or directory.

Is there anyone who has the patience to help a CLI impaired noob,

Rick :)

---

### Post by linear on 2006-02-22
Double and triple check the syntax of your command. According to [this]("https://wiki.ubuntu.com/Installation/OldWorldMacs"), it should look like:
 
```
cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux
```
 
Make sure all the slashes are leaning in the correct directions!
 
Afterthought: was BootX installed in OS9 first?

---

### Post by smileyme on 2006-02-22
Thanx for the reply.

Unfortunately the command was entered exact, double checked many times.:cry: 

What I did:

Option + F2
Results: Choose enter to activate shell; or something to that effect: (enter)
Results: ~ #
Typed; df (enter)
Results: (location and info on files) ~ #
Typed; cd /target (enter)
Results: Target #
Typed; mkdir hfs (enter)
Results: Target #
Typed; mount /dev/hdc6 hfs -t hfs (enter)
Results: Target #
Typed; echo '/dev/hdc6 /hfs hfs defaults' >> etc/fstab (enter)
Results: Target #
Typed cp boot/vmlinux hfs/System\ Folder/Linux\ Kernels/vmlinux (enter)
Results: Could not open 'hfs/System Folder/Linux Kernels/vmlinux' no such file or directory

I'm not always sure of where spaces are suposed to be and am wondering, now, if I have spaces where I shouldn't.

Rick :)

> was BootX installed in OS9 first?

Missed this earlier, but yes I did set it up in OS 9 first.

---

### Post by smileyme on 2006-02-24
This issue solved, but have more

---

