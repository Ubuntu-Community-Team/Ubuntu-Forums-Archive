---
title: "Mount the QEmu virtual disk/Access CD Rom"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by ireshsl on 2007-07-18
Hi,

I have installed Windows XP Under Ubuntu 7.04 ( [https://help.ubuntu.com/community/Wi...UnderQemuHowTo](https://help.ubuntu.com/community/Wi...UnderQemuHowTo) ). Now I need to install Flash MX 2004 and configure my Canon scanner inside that (because it is not supported properly by Ubuntu)

But when I insert a CD to install Flash, I can't access using My Computer. When I double click on that "CD Drive (D:)" , I get a message saying "Please insert a disk in to drive D:".

further I tried mount that QEmu virtual disk, using this command

sudo mount -o loop,offset=32256 windows.img /media/qemu

I got this result

server@server:~$ sudo mount -o loop,offset=32256 windows.img /media/qemu
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

server@server:~$

How do I access that QEmu virtual disk or access CDs ?


Thanks !

---

### Post by tim_abell on 2008-01-04
with the virtual machine active, press ctrl+alt+2 to switch to the qemu monitor console
then type:
change cdrom /dev/scd0
You can also check out the commands "help" and "info block". Using mount on the host system will tell you what /dev/scd0 should be.

Tim

---

