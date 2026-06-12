---
title: "Gutsy Installation Failure Using A C2D MacBook + VirtualBox"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by FetusHunter on 2007-10-28
I'm trying to install Gutsy on my C2D MacBook using VirtualBox, but on the eighth step of install (the last step), I get this error:

     "The creation of swap space in partition #5 of SCSI1 (0,0,0) (sda) failed."

That's my whole problem, I think...

Can anyone help me out? I'm sorry if this is in the wrong forum, I'm new. Thanks!

---

### Post by ItsMitsHere on 2007-10-28
i haven't used virtual box but i know it is virtualization software like parallels and vmware. it such case we are not suppossed to partition the harddisk manually at all. first create a virtual machine with desired hard disk size and then when you install the ubuntu let the ubuntu choose the whole hard disk. here ubuntu will find that the whole harddisk is actually the one you created with virtual box. and then it will install the os automatically.

cheers!!!

---

