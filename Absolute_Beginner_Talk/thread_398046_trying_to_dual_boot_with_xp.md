---
title: "trying to dual boot with xp"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by mishkin on 2007-03-31
Hi I tryed installing ubuntu to dual boot with my XP a whole bunch of times with absolutly no luck... It all seems to go fine but when the machine boots it goes straight into windows

I have 4 partitions on my primary harddrive, the first one has windows

the seccond one is ext 3 10 gigs mount point: / boot flag:off (guides seem to leave this as off but maybee thats the obvious mistake since I want the damned thing to boot?)

third one is ext 3 mount point: /home flag off 15gb

fourth is 1 gb use as: swap area and it's formated to be swap

I picked lamp (installing server)

when it says "install the grub to master boot record?" I have tryed yes, and it doesn't boot when I restart... I also tryed no useing hda1, hda2, hdb1 and all said "failed, fatal error"

whats going on... help plz

---

### Post by Trab on 2007-03-31
hello.
your problem appears to be with the boot-loader.

I have never installed a system and left /boot as a seperate partion, just never found it nessicary. since you have nothing on your linux partion, i suggest you reinstall and try this instead.

leave /windows partion alone. it should be /hda1
install / (this is the root partion) to /hda2
set up /home on /hda3
set up swap on /hda4

if you tell it to install like that, and DONT MESS WITH THE FLAGS it should work fine.

remember to delete all the partions for linux before you start the install process.

good luck!
-Trab

---

### Post by mishkin on 2007-03-31
I reformated all the linux partitions and installed just like you said and it still just goes right into XP, the boot options never show up...

I'm dl-ing the destop version atm, gonna try installing that and see if I have the same difficulties, but any ideas in the mean time would be much appricated, bloody tryed installing this thing about 15x now with no result

---

### Post by Trab on 2007-03-31
hmmm.
Well, the problem is deffinately the bootloader. 
personally, i hate grub. when things go wrong with it, its a pain in the rear.
My guess is that grub was not installed to the MBR, instead to /root
does it say during the install where its going to put grub (usually the last step says hd0 or something?)
hd0 is where you want it to install.

---

### Post by mishkin on 2007-03-31
yeah it flashed hd0 quickly I remember seeing that

---

### Post by nsilva on 2007-03-31
Well first of all make sure you install Ubuntu after XP, which I'm guessing that is what you are doing. Windows will always take the MBR, suckers!

Make sure that if you have a separate partition /boot that it is mounted to /boot dirctory.

After installing GRUB (Maybe the system does it automatically)
> 
nano -w /boot/grub/grub.conf
or
vim /boot/grub/grub.conf

> 
Undestanding the GRUB.conf, from Gentoo's Handbook

Understanding GRUB's terminology

The most critical part of understanding GRUB is getting comfortable with how GRUB refers to hard drives and partitions. Your Linux partition /dev/hda1 (for IDE drives) or /dev/sda1 (for SATA/SCSI drives) will most likely be called (hd0,0) under GRUB. Notice the parentheses around the hd0,0 - they are required.

Hard drives count from zero rather than "a" and partitions start at zero rather than one. Be aware too that with the hd devices, only hard drives are counted, not atapi-ide devices such as cdrom players and burners. Also, the same construct is used with SCSI drives. (Normally they get higher numbers than IDE drives except when the BIOS is configured to boot from SCSI devices.) When you ask the BIOS to boot from a different hard disk (for instance your primary slave), that harddisk is seen as hd0.

Assuming you have a hard drive on /dev/hda, a cdrom player on /dev/hdb, a burner on /dev/hdc, a second hard drive on /dev/hdd and no SCSI hard drive, /dev/hdd7 gets translated to (hd1,6). It might sound tricky and tricky it is indeed, but as we will see, GRUB offers a tab completion mechanism that comes handy for those of you having a lot of hard drives and partitions and who are a little lost in the GRUB numbering scheme.


Probably it would look different but here is the idea
> 
# Which listing to boot as default. 0 is the first, 1 the second etc.
#you could boot Windows or Gentoo by default after the time is up
default 0
# How many seconds to wait before the default listing is booted.
#Time to wait before the default is loaded
timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
#splashimage=(hd0,0)/boot/grub/splash.xpm.gz

title=Ubuntu
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-ubuntu root=/dev/hda3

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/hda6.
title=Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1


Let me know if it helps,

---

### Post by mishkin on 2007-03-31
I got it to give me the boot options, I did 2 things not sure which one made it work

1. I set the root partition to bootable (the flag)
2. I set my other partition to /boot instead of /home (with the first as /)


edit: the desktop version, gonna try server again in a bit

---

### Post by mishkin on 2007-03-31
I just restarted to get back into ubuntu and now it's going straight into xp again

---

### Post by nsilva on 2007-04-03
> **mishkin said:**
> I just restarted to get back into ubuntu and now it's going straight into xp again
Please post your grub.conf and your partition tables, please

---

### Post by ansarimikail on 2007-04-03
Hi
I tried to boot linux from cd, but it went straight into the whole install thing.
Do you think I've lost all the data on my hard drives.
Please Help :(

---

