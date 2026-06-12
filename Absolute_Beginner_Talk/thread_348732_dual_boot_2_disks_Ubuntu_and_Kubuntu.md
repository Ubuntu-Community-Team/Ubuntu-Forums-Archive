---
title: "dual boot 2 disks Ubuntu and Kubuntu"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by VanDerLiviu on 2007-01-29
Hello! Is there any way for me to join to my SATA harddisk that has Ubuntu, another SATA disk onto which I want to install Kubuntu, and then to have a choice of which one to boot into?
Thanks a lot for help!

---

### Post by ieee488 on 2007-01-29
Yes.  It doesn't matter if it is Kubuntu or any other OS on the second hard drive.

---

### Post by VanDerLiviu on 2007-01-29
Hey, thanks for replying! So, all I have to do is put the other SATA disk into the PC, put the Kubuntu LiveCD, boot from it, install on the new disk, and after installation, reboot and have the GRUB ask me which OS to boot into?

---

### Post by photomaster106 on 2007-01-29
I tried that and it scrambled my first disk,so if their is a procedure I would like to know it

---

### Post by ieee488 on 2007-01-29
> **VanDerLiviu said:**
> Hey, thanks for replying! So, all I have to do is put the other SATA disk into the PC, put the Kubuntu LiveCD, boot from it, install on the new disk, and after installation, reboot and have the GRUB ask me which OS to boot into?
Theoretically yes.

I have two PATA disks on my PC. One had Windows 2000 and the other had some data files and was formatted NTFS.

I put in my Ubuntu 5.10 CD1 and installed it in the 2nd hard drive. During that install, I resized the NTFS partition to a smaller size since I wanted to keep those data files and gave Ubuntu about 15GB.

After Ubuntu 5.10, I installed OpenSUSE 10.1. Then I installed - not upgraded - Ubuntu 6.06 over Ubuntu 5.10.
Now, I have a PC that let's me triple-boot into Windows2000, Ubuntu 6.06, and OpenSUSE 10.1.

Nothing's broken; nothing is scrambled.

---

### Post by VanDerLiviu on 2007-01-29
Many thanks ieee488! I shall try to do as I said about installing another Ubuntu on a second SATA disk, and we shall see how that'll go...My only concern is whether or not GRUB will be capable of dealing with 2 distros on 2 different SATA disk, without any intervention from my side...

---

### Post by ieee488 on 2007-01-29
It should work.
Good luck. :D

---

### Post by VanDerLiviu on 2007-01-30
Actually, the istallation went all right, but now the problem is that I can not boot into Edgy anymore! I think I have to edit the menu.lst, but that is going to be rather difficult for me...any ideas? :(

---

### Post by carverj on 2007-01-30
What you could do is what you originally said and have an OS on each drive.
I have two OS's on each drive. Windows on first part. of each disk and Ubuntu over the rest.
It is a great way to backup data.
So what happened? You ended up placing two Linux distro's on the same drive but different partitions? Then when you boot, the grub boot list only gives you the kUbuntu partition to choose from?

---

### Post by VanDerLiviu on 2007-01-30
> **carverj said:**
> What you could do is what you originally said and have an OS on each drive.
I have two OS's on each drive. Windows on first part. of each disk and Ubuntu over the rest.
It is a great way to backup data.
So what happened? You ended up placing two Linux distro's on the same drive but different partitions? Then when you boot, the grub boot list only gives you the kUbuntu partition to choose from?

Hi **carverj**! Actually, what I did was I installed the second Linux distro on the second SATA disk; therefore, I ended up with two Linuxes on two different disks. I can boot into the second all right, but I can not but into my original Ubuntu, which is installed on my first, original SATA disk. I assumed that GRUB will give me a choice when I reboot after installation, but that was not the case. So now I have to figure out how to do this... because I want my beloved Edgy back ... :mad: 
Any ideas?

---

### Post by teaker1s on 2007-01-30
why not just ubuntu install then install kubuntu-desktop? this way you choose either at session login!

---

### Post by VanDerLiviu on 2007-01-30
> **teaker1s said:**
> why not just ubuntu install then install kubuntu-desktop? this way you choose either at session login!

Right, that is exactly what I should have done...Yet again, for the sake of the argument, I would still like to know whether is possible or not to reclaim both installs...as a mere experiment...:frown:

---

### Post by carverj on 2007-01-31
> Hi carverj! Actually, what I did was I installed the second Linux distro on the second SATA disk; therefore, I ended up with two Linuxes on two different disks. I can boot into the second all right, but I can not but into my original Ubuntu, which is installed on my first, original SATA disk. I assumed that GRUB will give me a choice when I reboot after installation, but that was not the case. So now I have to figure out how to do this... because I want my beloved Edgy back ...
Any ideas?

Ah, you may need to mount the slave Linux partition in /etc/fstab first.
Strange though. I thought the slave Linux should automatically be picked up by grub!!?
Did you try editing this entry into grub menu list?
You'll be fine with some persistence!

---

