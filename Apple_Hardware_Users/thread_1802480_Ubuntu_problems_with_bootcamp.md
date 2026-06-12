---
title: "Ubuntu problems with bootcamp"
date: 2011-07-12
forum: Apple Hardware Users
---

### Post by dsmith890 on 2011-07-12
Hey all - I'm new here so sorry if this is an easy one. 

Basically I have a Macbook Air 3,1 and I decided to install ubuntu on it through the bootcamp partitioner. I installed Ubuntu 11.04 Natty Narwhal and got it up and running on the bootcamp partition (just Ubuntu - no windows) with a bit of help from refit. 

Here's my problem: the 2 OSs are working great but I want some integration via virtualization. I have VMWare Fusion and I think I should be able to use the physical Ubuntu installation inside a virtual machine. Near as I can tell the only problem is that I can't mount the bootcamp drive in OS X. Disk Utility sees it as a corrupt FAT32 partition and my attempts to mount it with either gui or command line are failing. 

Is it possible to use a bootcamp drive like this? if so, how can I mount it?

Thanks for any help

---

### Post by conundrumx on 2011-07-12
*(deleted)*

---

### Post by Neds Moar Salt on 2011-07-12
In virtualbox you can create a virtual hd-symbolic-link like thingy from a physical hd/partition.  If you manage to boot ubuntu from the partition without your hd's MBR, you're set.

Edit: if you want to try, look into "VirtualBox internalcommands createrawvmdk -rawdisk"

---

### Post by dsmith890 on 2011-07-14
> **Neds Moar Salt said:**
> In virtualbox you can create a virtual hd-symbolic-link like thingy from a physical hd/partition.  If you manage to boot ubuntu from the partition without your hd's MBR, you're set.

Edit: if you want to try, look into "VirtualBox internalcommands createrawvmdk -rawdisk"

Awesome advice - thanks much. Using the internal commands is a bit of a pain with a partition on your boot disk. For me I needed to run the commands with root privileges and then run virtualbox with root privileges as well to use them. All in all it worked so far as using a physical disk was concerned. That said I'm having to give up this line of investigation cause space on my SSD is scarce right now and I needed to delete the partition for other work. If anyone actually gets it fully working let me know!

---

