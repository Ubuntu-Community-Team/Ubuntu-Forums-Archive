---
title: "resizing partition on macbook"
date: 2008-06-04
forum: Apple Hardware Users
---

### Post by andrewbossie on 2008-06-04
hello, i wave my macbook partitioned approx 200 for osx and 50 for ubuntu, i was wondering if there was a way to resize the partitions, without destroying existing data, so that i have more space for ubuntu.

thanks!


-andrew

---

### Post by Kobalt on 2008-06-04
Hello,

Have you ried booting from the Leopard install DVD, opening the Disk Utility to see if you can resize partitions from here?
I know BootCamp can resize HFS+ partitions for Windows, but once you use it to resize your partition and install Linux, it cannot see the partition he created and doens't allow you to resize it...

---

### Post by cyberdork33 on 2008-06-04
> **andrewbossie said:**
> hello, i wave my macbook partitioned approx 200 for osx and 50 for ubuntu, i was wondering if there was a way to resize the partitions, without destroying existing data, so that i have more space for ubuntu. All the installation guides show you how to do this.

Basically you want to use BootCamp or DiskUtility (in Leopard) to "add" a partition to the drive.

After that, boot into the Ubuntu LiveCD, use gparted to delete the new partition, then after starting the Ubuntu installer, choose to install to the largest free space.

---

### Post by Halsnalle on 2008-06-25
But will this keep the data on the Ubuntu partition? I'm in the same situation, wishing to increase Ubuntu's share of my MacBook Pro's harddrive (as well as adding more swap, since suspend is complaining), but I'd prefer not having to reinstall Ubuntu. As I understand your suggestion, it implies reinstalling Ubuntu rather than growing its partition.

---

### Post by flaggh on 2008-06-25
You can resize your HFS+ partition with disk utility and the resize your ext3 partition with gparted without destroying any data.

---

### Post by Patraman on 2008-07-02
Hey, If you don't have Leaopard you can do it via the terminal

diskutil resizeVolume (put your drives name here) (size you wish to change it to here)G

For example:
diskutil resizeVolume disk0s2 60G

---

### Post by Halsnalle on 2009-01-11
> **Patraman said:**
> Hey, If you don't have Leaopard you can do it via the terminal

diskutil resizeVolume (put your drives name here) (size you wish to change it to here)G

For example:
diskutil resizeVolume disk0s2 60G

I just tried this, but I get an error:
> 
Resizing encountered error No space left on device (28) on disk disk0s2 Macintosh HD

And yes, I have checked that there is enough space to shrink the partition. 

The best solution to this problem that I have found suggests doing it from the Disk Utility in Leopard.

But I run 10.4.11, and one of my reasons for switching to Ubuntu is that I don't want to upgrade to Leopard...

Any suggestions?

---

### Post by dank28 on 2009-01-11
I'm interested in finding a solution to this as well.  I was considering cloning my 10.4.11 install to a firewire drive I already have set up as a boot disk, and then starting new with my internal drive to set up dual booting OSX and ubuntu.

But if it's possible to shrink my OS X partition and then install ubuntu, I'm all for it!

---

### Post by Halsnalle on 2009-01-12
Okay, I found the solution to my "no space left on device" problem:

Following [these instructions]("http://installingcats.com/2007/11/22/no-space-left-on-device-error/"), I located some large files (mostly Parallels and VMWare VMs I never use anyway) and deleted them. (I.e., I didn't even have to delete the 2GB safe sleep memory image file, as suggested in the linked post.)

After that, resizeVolume worked like a charm. Now I'll dig into Gparted to add the freed up space to my Ubuntu install...

---

### Post by Halsnalle on 2009-01-12
> **Halsnalle said:**
> Now I'll dig into Gparted to add the freed up space to my Ubuntu install...

Hm. After having used Gparted Live CD to expand the Ubuntu partition and swap, I restarted my computer, but rEFIt now only gives me one option: to boot Mac OS X. Ubuntu seems to be gone...

Any idea what I did wrong?

---

### Post by cyberdork33 on 2009-01-12
> **Halsnalle said:**
> Hm. After having used Gparted Live CD to expand the Ubuntu partition and swap, I restarted my computer, but rEFIt now only gives me one option: to boot Mac OS X. Ubuntu seems to be gone...

Any idea what I did wrong?
you need to resync the partition tables with rEFIt and likely reinstall grub.

---

