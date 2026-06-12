---
title: "VMware Partition Table change"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by yj09 on 2007-05-29
I got error while trying to run windows xp in physical disk. I am using Kubuntu 7.04. It running good in my previus laptop. Anybody face this problem, can share how to solve this problem. Below is the message:

"The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again".

---

### Post by TylerMD on 2007-09-10
Googling seems that the problem is that grub modifies the partition. A possible solution is to install grub on a floppy disk instead of the WinXp partition. I haven't tried.

---

### Post by Mariano Oliveto on 2007-11-13
I have the exact same problem in my laptop. I was able to make this work on my desktop computer but I have a different configuration there, I have Windows XP installed in a HDD and grub and Ubuntu in another HDD.

Here I have 

sda1: Windows XP
sda2: "/" mount point
sda5: "/home" mount point
sda6: "swap"

I will investigate further and if I come to any solutions I will post here (I was going to create a new thread but it makes sense to continue this one).

I really don't know which information is relevant to this problem so if anyone needs more info for troubleshooting please tell me.

Any help is appreciated! :D

---

### Post by Mariano Oliveto on 2007-11-13
Eureka! OK, choosing entire disk instead of individual partitions did the trick for me so now I can boot my Win XP partition from VMWare in Ubuntu.

I'm guessing the difference could be because grub installed in the MBR?

Either way, maybe this will help someone else. Hope it does :P

---

### Post by MaindotC on 2008-02-12
I had to run it as ```
 gksudo vmware
``` and then per your suggestion it DID get past the "The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again" error, but that error message box still appeared.  I clicked "ok" on that error message box and then I stared the vm.

I did get into the boot loader which I believe is on the MBR (and not the first sector of the first boot partition), but when selected my XP partition the vm froze :(  Still googling...

---

