---
title: "trouble with corrupted boot partition"
date: 2006-12-20
forum: Apple PPC Users
---

### Post by namluc on 2006-12-20
In the past few weeks for unknown reasons 2 things have happened:
 - my boot menu dissapeared, both graphical and text, to select the OS I want, I blindly press either x or l on hearing the chime.
 -  dapper drake stopped recognizing my keyboard input, rendering it useless!

I have downloaded the edgy iso. after a bit of jiggery pokery with gparted it started to install; but on coming across my corrupted boot partition, which shows up as black and half open in gparted, it asked me to sort it out before it could continue.

My question is, if I delete it, will the edgy install create a new one for me that will allow me to access both osx and ubuntu? will osx recognize the linux created partition? what if for some reason the edgy install quits half way through, what could i do to access osx?

also, why would dapper drake stop recognizing the letters of my keyboard, but still be able to see the numerals?

thanks for the help in advance!

---

### Post by ingo on 2006-12-22
Greetings to the moors! No idea what happened to your boot partition or why your keyboard started going funny. But here is a link for dual booting osx and linux

[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html](http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html)

HTH

PS.: I'd trust GRUB and simply install over your dapper. But not having dual booted for a while I wouldn't ask anybody else to take the plunge...

---

### Post by namluc on 2006-12-22
Thanks for your help there ingo!

Thats given me the confidence to try to delete my corrupted boot partition from within gparted. Unfortunately gparted won't let me do it, so I can't currently get as far as a dual boot config!

If there is any info that I could provide that would make diagnosis and treatment easier please tell me, as I'm dying to get this sorted out.

---

### Post by bernied on 2006-12-22
You can't alter partitions on a disk that is in use - so if your operating system is on the disk you want to change, you need to do this stuff from a live-cd. Many live-cds mount all disks on startup (because this is generally useful), so you need to check to see if it's mounted, then umount any on disks that you want to alter
```
mount
```tells you what's mounted
```
umount /dev/hda*
```will unmount any partitions in hda, you'll get some errors like '/dev/hda not mounted' because the disk as a whole was not mounted, but be sure you don't get any '/dev/hda2 busy' type errors, as you'll have to make sure the partition is not 'busy' before you can umount it. Just try 'mount' again to see what is still mounted.

---

### Post by namluc on 2006-12-22
Thanks bernied

I've been using gparted from within the live cd.

now, before I unmount all volumes on the hard drive, how will that impact the data, are there any problems that could arise from this procedure? And how will mounting/unmounting affect the corrupt boot partition. After my first post I tried to delete it, but with no success. I will try and do it again to get the error report

---

### Post by bernied on 2006-12-23
Mounting and unmounting a device has no effect on the data within a partition, it just allows/disallows you access to the filesystem.

You will need to mount them again in order to access them again, and if you have changed the order/usage/filesystems on a partition you need to update /etc/fstab before you can 'easily' mount them. In a live-cd, just restart the live-cd as it writes its own fstab at startup.

I'm a little concerned about what is the purpose of the boot partition as far as OS-X is concerned. I have no experience with OS-X so don't know how it boots. Do you know whether OS-X uses the boot partition? Is its kernel stored there, for instance?

---

### Post by ingo on 2006-12-23
> I have no experience with OS-X so don't know how it boots.
my sentiments exactly. I could probably get windows booting from grub (with some difficulty, granted), got about 4 different linux distros on my box at the mo which grub handles fluffily, but OSX? I know for a fact that it is possible... hang on, just read that it needs to be chainloaded same as windows! 

In that case

[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

explains things nicely.

---

