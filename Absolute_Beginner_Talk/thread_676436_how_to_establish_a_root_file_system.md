---
title: "how to establish a root file system"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-23
I used wubi but its messed up twice so on to a real install I need to make a root file system I have windows and data but I have partions from a failed mandriva install and I want to use them to install linux mint so how heres what my partition situation is like 
srry bout the quality

---

### Post by PeterJS on 2008-01-23
Looks like you'd want to use sda7 as your root, I would caution you that 5 gig's is a bit small for a combined / and /home partition, and if you could shuffle some space over from sda5 that might make your life better in the long term

---

### Post by exneo002 on 2008-01-23
thanx but how do I establish it from an ubuntu installer+ I have a broken box with a 50gig drive internal that I want to put in my fam box but my parents don't want me to so how do I convince them that installing a new hd is safe

---

### Post by PeterJS on 2008-01-23
> **exneo002 said:**
> thanx but how do I establish it from an ubuntu installer+ I have a broken box with a 50gig drive internal that I want to put in my fam box but my parents don't want me to so how do I convince them that installing a new hd is safe

Just change the mount point to / and the installer will handle the rest.

As for installing a new hd, what are they afraid will happen? It's a hard drive, it sits there and has data read and written to it.

---

### Post by exneo002 on 2008-01-24
they don't want me on the inside of their box no matter how simple somthing is they are a little paranoid of everything except microsoft so I need a good argument as to how safe it is if their isn't a extra slot I just won't do it

---

### Post by PeterJS on 2008-01-24
> **exneo002 said:**
> they don't want me on the inside of their box no matter how simple somthing is they are a little paranoid of everything except microsoft so I need a good argument as to how safe it is if their isn't a extra slot I just won't do it

Well, they're kinda right that just sticking random drives in when you don't have a bay to put the drive in is a bad idea, but most cases have more bays than they have factory installed drives. Hardware and software are completely separate, except to the extent that the software makes use of the hardware, a bare blank hardrive sitting on a table is no more a mac hard drive, than it is a windows hard drive, than it is a linux hard drive. Some file systems lend themselves better to some file systems than others, but that's a software issue. The only damage you could do is change the order of devices in the BIOS, so when it goes to hand over control to the boot loader, it won't be where the BIOS expects it to be. That's not likely though as the drives are ordered first by IDE or SATA channel, and then by their role on that channel, master first then slave. I can't think of a single manufacturer that doesn't put the primary hard drive as the master of the first channel, meaning there's no way to get "in front" of it and change it's number. If the drive is formatted to a file system that windows doesn't understand it will just ignore it, so that shouldn't be an issue, and if it is going to be a shared data drive, data is data it just sits on the disk being inert and waiting to be read. Data doesn't care about the OS, and the OS only cares about data to the extent that it does or does not have the applications to read it, again if the apps don't understand it they will just ignore it, unless there's a persistent user at the helm.

---

### Post by exneo002 on 2008-01-24
k but I decided to back-up my [important] files to 3 dvds but partioning is still a bitch and I don't want to purposly over-ride my files

---

