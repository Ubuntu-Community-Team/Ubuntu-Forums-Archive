---
title: "Install Ubuntu on vmware"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by maestro234 on 2007-11-07
I am trying to install ubunto on a vmware serve.

I get to step four. How do you want to configure the disk? My only option is manual.  I then have to prepare partitions, but have no options to do anything in this screen.

Can anyone tell me what I am doing wrong?

Thanks.

---

### Post by P4man on 2007-11-07
This might be a question better asked in VMware forum. Im not familiar with VMware, but did you create a virtual harddisk for Ubuntu to install on to ? is ubuntu partition manager showing any disks at all ?

Sounds to me you only gave the VM a Cd drive, and ubuntu livecd boots from that, but has no harddisk to install to. Your virtual machine must also provide harddisk(s) to the guest OS or you can not install.

---

### Post by KingWilliam on 2007-11-07
If you look to the specs of the virtual machine in VMWare, are you sure you created a good disk? 

I suppose you mean the partition editor during the installation?  You should be able to click something. Just create one ext3 partition and one Swap partition. That's all :)

---

### Post by maestro234 on 2007-11-07
I started over and created a new virtual machine.  It is working fine now.  Something must have gone wrong with the initial setup.  Thanks for your help.

---

### Post by P4man on 2007-11-07
Glad we could help. Please don't forget to mark the thread as "solved" (thread tools, somehwere top right)

---

