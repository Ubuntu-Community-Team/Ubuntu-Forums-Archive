---
title: "Ubuntu on new computer"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by denbeau on 2006-11-08
I am building a new computer. 
I intend to install Vista, but till it's released I thought I'd run  Ubuntu. Maybe I will never get to Vista if I like it! 
I was wondering how I should setup partitions and if I want to have a dual boot computer, is there anything I need to do with my  installation of Ubuntu? Does Ubuntu setup partitions and format and does Vista or XP see these partitions?
I did send for the Ubuntu 64 setup disc. 
Thanks 
Denbeau


Intel Core 2 Duo E6400 
Asus P5B Socket T 
Mushkin PC2-6400 DDR2 2gb
 eVGA 256-P2-N615-TX GeForce 7600GT 256MB 128-bit GDDR3 PCI Express x16	
Antec Nine Hundred		
Antec Neo he 550w		
WD Raptor X  150gb		
MITSUMI card reader Floppy Drive			
LITE-ON LH-18A1P-185		
LITE-ON sata combo SHC-52S7K-05

---

### Post by rlozano on 2006-11-08
if you plan to install Vista later on, you will definitely have to re-install your ubuntu since windows overwrite the MBR. if you want to dual boot with linux, you have to install windows first, always.

---

### Post by Zeerak on 2006-11-08
I believe that they recommend installing windows first because when installing windows, the windows grub overwrites (not sure about if it overwrites or sets it to ignore) the ubuntu grub. But other than that I don't believe that there are any further complications with installing windows after installing ubuntu. It should recognize any previously made partitions by itself.
There is a way to regain the Ubuntu grub though, I don't know how and I don't remember what the

By what i've read from other posts and such this is what I've learned, but being new to ubuntu and linux I may very well be wrong somewhere, if so and anyone sees it, please correct whatever mistakes there may be.

---

### Post by indytim on 2006-11-08
Why don't you just set up your first partition as NTFS now.  Leave it empty (make sure it's got ooogles of space for all of the Windows stuffola).  Then set up your ext3 partitions for Ubuntu.  Install Ubuntu through the live CD.  If/when you go the Vista route, install Vista in the NTFS partition and run GParted Live to re-build your GRUB. 

IndyTim

---

### Post by jd65pl on 2006-11-08
> **rlozano said:**
> if you plan to install Vista later on, you will definitely have to re-install your ubuntu since windows overwrite the MBR. if you want to dual boot with linux, you have to install windows first, always.

Not true with all versions of windows see this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Not sure what is it like with vista though

---

### Post by drtvasudevan on 2006-11-08
> **denbeau said:**
> I am building a new computer. 


Intel Core 2 Duo E6400 
Asus P5B Socket T 
		
LITE-ON LH-18A1P-185		
LITE-ON sata combo SHC-52S7K-05

is that a SATA CD ROM/DVD ROM?
you might want to see this page
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by denbeau on 2006-11-08
Thanks guys
Denbeau

---

