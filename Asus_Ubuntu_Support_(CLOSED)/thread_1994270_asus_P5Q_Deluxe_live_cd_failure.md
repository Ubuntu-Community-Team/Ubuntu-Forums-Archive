---
title: "asus P5Q Deluxe live cd failure"
date: 2012-06-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pelgrim on 2012-06-02
I tried to install ubuntu 10.04, 12.04 and the 12.04 alternative iso
on a second hand pc with an asus P5Q deluxe motherboard.

Extensive reading on the internet and trial&error got me nowhere:
ubuntu will at best ask me the language and show the initial menu.
An operation that has anything to do with hd dectection will end up
in the message
kernel_thread_helper+0x6/0x10
or
kernel_thread_helper+0x7/0x10

Cd's are checked, one is a cd sent from ubuntu,
the 12.04 versions are downloads and boot normally on other pc's.
BIOS settings are tried on in any reasonable combination.

So I understood ubuntu has a bad history with asus motherbords that
support both ide and sata.
Is that the right conclusion ?
Is the Ubuntu team going to solve that problem ?
Any solution with Ubuntu or another lunix distro ?
(I downloaded/tried vectorlinux as well, same problem)

The situation now: after using linux since release 6.04,
I'm thrown back "in the dark ages" with a windows on the metal
and vmware to run my ubuntu machines virtual.
Painfull ...

---

### Post by pelgrim on 2012-06-03
someone gave me a hint to try the 64bit version.
That works, I can run the live cd.
BUT
when running the install, I get an empty partition table
for my harddisk, and all buttons to manipulate the partitions
are disabled.
Strange enough, in the "try ubuntu" mode I can run gparted
and manipulate the partitions.
Again, when running the install, an empty partition table
is all I get.
Anyone have any experience with that ?

the harddisk is still sata by the way.

---

