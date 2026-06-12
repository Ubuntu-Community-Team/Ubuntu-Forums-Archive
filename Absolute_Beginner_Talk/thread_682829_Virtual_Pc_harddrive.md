---
title: "Virtual Pc harddrive"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by mindstormmaster1 on 2008-01-30
So i think i know how to install ubuntu in a virtual pc.  But im wondering.

1. does creating a virtual hardrive in virtual pc partition my hd or just make like a fack hd?

2. when i tell ubuntu to use my whole hd will it just use my whole virtual harddrive(thats what i want right) or my real hardrive(i dont want that)?

3. is there really any way i can mess my computer up using virtual pc?

---

### Post by emarkd on 2008-01-30
1.  The virtualization software will "fake" a hard disk by making one large file on your real hard disk somewhere.  You tell it how large of a "disk" to make.  After your virtual disk is created and you boot Ubuntu in the virtualization software, you can tell it to use the entire disk because Ubuntu doesn't know it's running in a virtual computer and that the disk is really just a file.  Does that make sense?

---

### Post by Atomic Dog on 2008-01-30
To amswer number 3:  I cannot see how you can mess up your host operating system by using a virtual machine.  At least I never have, and I have used VM's a lot.

---

### Post by emarkd on 2008-01-30
For most uses, there's no way you could mess up your host with VM software.  That being said, some VM software will let you boot real disks and partitions.  I know VMWare allows this because I use it for that purpose.  If you were to accidentally use VMWare to boot the same live drive/partition that you're currently running on, I can see where some very bad things could happen.  Running Ubuntu on your real hardware, starting VMWare and then booting that same Ubuntu installation in a virtual machine just sounds dangerous.  Of course, using virtual disks and installing your OS's on those through your VM software prevents that from ever happening.

---

### Post by mindstormmaster1 on 2008-01-30
4.  what is better/easyer to use Virtual PC or VMWare Workstation?


Thanks a ton for all your help.

Ya running ubuntu in a virtual pc on ubuntu just sounds wierd :)

---

### Post by emarkd on 2008-01-30
Well, I've used VMWare for years and still do, but you have to edit the config files by hand.  Lots of people like VirtualBox.  I've never tried it but it's supposed to be very good.  Virtual PC is (I think) Microsoft's answer to virtualization and so it probably won't run on Ubuntu.

---

