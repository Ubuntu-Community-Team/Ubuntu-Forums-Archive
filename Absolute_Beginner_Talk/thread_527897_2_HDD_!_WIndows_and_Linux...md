---
title: "2 HDD ! WIndows and Linux.."
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-17
Hey al
My frnd has 2 Hdd or more than can't say but he has on empty .. He wants to install Ubuntu on that but unable to configure GRUB ? Is it possible o install Xp in 1 and ubuntu in 2 .. I know it is but some 1 spread some light :D
:guitar:

---

### Post by Steve1961 on 2007-08-17
Just install XP first on the first hard drive, then install Ubuntu on the second drive - grub will automatically be configured during the install.

---

### Post by taurus on 2007-08-17
Install Windows to the first harddrive first.  Then, install Ubuntu on the second harddrive and when you get to the bootloader part, install GRUB to MBR so you can boot both.

---

### Post by Sbarton on 2007-08-17
As has been mentioned install XP on one (maybe Master) and Ubuntu on Slave drive.Ubuntu grub will overwrite the MBR, and you will be given a choice of which OS you want to boot into at bootup. Should you wish to go back to XP only you will need the XP disc to reinstall the windows MBR.
regards

---

### Post by Dark Star on 2007-08-17
Thanks for the info .. WIll try today on his comp :D

---

### Post by hyper_ch on 2007-08-17
The only problem I've encountered so far is if you have IDE and SATA drives installed on your computer... Grub might be confused then...

---

### Post by Wynne G Oldman on 2007-08-17
I have 2 HDD's in my system (both SCSI). I have XP on 1 and Ubuntu on the other. I installed XP on my first HDD, took it out, and then installed Ubuntu on the other HDD. I then replaced the HDD with XP on it. I swap between the 2 operating systems by choosing which HDD to boot from in the BIOS. The advantage of this is if you mess one operating system up, you can restore it without effecting the other one, as they're totally independent of each other.

---

### Post by hyper_ch on 2007-08-17
good idea but it's not quite as confortable as having to select directly from grub what you want to start ;)

---

### Post by Dark Star on 2007-08-17
> **Wynne G Oldman said:**
> I have 2 HDD's in my system (both SCSI). I have XP on 1 and Ubuntu on the other. I installed XP on my first HDD, took it out, and then installed Ubuntu on the other HDD. I then replaced the HDD with XP on it. I swap between the 2 operating systems by choosing which HDD to boot from in the BIOS. The advantage of this is if you mess one operating system up, you can restore it without effecting the other one, as they're totally independent of each other.

Haha nice thinking will try all the methods :P As its my frnds comp :lolflag:

---

### Post by Phase1 on 2007-08-17
> **Wynne G Oldman said:**
> I have 2 HDD's in my system (both SCSI). I have XP on 1 and Ubuntu on the other. I installed XP on my first HDD, took it out, and then installed Ubuntu on the other HDD. I then replaced the HDD with XP on it. I swap between the 2 operating systems by choosing which HDD to boot from in the BIOS. The advantage of this is if you mess one operating system up, you can restore it without effecting the other one, as they're totally independent of each other.

this is actually the method that i am doing now, cause i am new and just trying ubuntu out.  it works alright, i just unplugg the power to the ubuntu IDE hard drive and plug in the windows SATA hard drive.

Grub doesnt give me a choice of which to boot from though, it will just automatically boot to ubuntu if both drives have power.  if both drives were SATA im not sure what would happen though.

---

### Post by Wynne G Oldman on 2007-08-17
> **Phase1 said:**
> this is actually the method that i am doing now, cause i am new and just trying ubuntu out.  it works alright, i just unplugg the power to the ubuntu IDE hard drive and plug in the windows SATA hard drive.

Grub doesnt give me a choice of which to boot from though, it will just automatically boot to ubuntu if both drives have power.  if both drives were SATA im not sure what would happen though.
If you install both HDD's in your PC, you should be able to choose which one to boot from in the BIOS.

---

### Post by Sbarton on 2007-08-17
Well, my experience of SCSI drives is 0 as I have IDE drives. I do not want to unplug anything to boot into a OS. I prefer to make a choice at boot up. As I have 2 OS on different drives I am offered a choice to choose from at boot. If I for some reason loose one , it is very easy to rectify. Also I would not want my friend to be experimenting with my PC so hopefully you will return it in good order.
regards

---

