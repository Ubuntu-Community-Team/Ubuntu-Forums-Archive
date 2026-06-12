---
title: "Can't boot Kubuntu after installation"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Groubi on 2006-02-05
Hi,

I have two HDD. Hda contains a Windows OS. I don't want to alter this disk.
Hdb may be used for Kubuntu. 
I installed Kubuntu on hdb. I choose to install grub on /dev/hdb.

The problem is : grub cannot boot Kubuntu neither Windows.

For Kubuntu, the message is :

root(hd1,0)
Filesystem type unknown, partition type 0x7
kernel /wmlinuz-2.6.12-9-386
root = /dev/mapper/Ubuntu-root ro quiet splash
error 17 : cannot mount selected partition.

What's wrong with my installation ? Does anyone can help me to solve this problem ? Is problem tied to my hardware or tied to my installation I I don't understand because this partition is an ext3 partition.

I check the m5 cheksum of downloaded iso file and all is correct.

Thanks !

---

### Post by Groubi on 2006-02-07
OK,

I found the problem with help of a grub file menu.lst generated with another distro.

The problem is Ubuntu's file menu.lst for grub is wrong.

My HDD configuration is :
  - Master HDD contains Windows Installation,
  - Slave HDD contains Ubuntu installation,
  - Grub is installed in Slave HDD boot sector,
  - My computer boots on Slave HDD.

Ubuntu installer generates these grub commands :
[I]root(hd1,0)
Filesystem type unknown, partition type 0x7
kernel /wmlinuz-2.6.12-9-386
root = /dev/mapper/Ubuntu-root ro quiet splash
error 17 : cannot mount selected partition.[/I]

I modify theses commands :
[I]root(hd**0**,0)
Filesystem type unknown, partition type 0x7
kernel /wmlinuz-2.6.12-9-386
root = /dev/mapper/Ubuntu-root ro quiet splash
[/I]

It seems that for grub my slave HDD is referenced as hd0 because my computer boots on it.

---

