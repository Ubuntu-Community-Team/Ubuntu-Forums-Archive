---
title: "I Need A Way To Install On Low Memory Machine Without Using Alternate"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-26
I have low memory computers (256 mb and a 94 mb). I don't have access to a alternate cd, just a live cd. What can I do to install?


I am actually trying to install Linux Mint. If you have a problem with that remember that come here every day to answer questions for others.

---

### Post by spiderbatdad on 2007-11-26
Why not burn an Xubuntu cd? I think minimum 512 is recommended for Gutsy Ubuntu, so if you were trying to do Daryna 4.0, I would think it would be the same.

---

### Post by -grubby on 2007-11-26
installing on a 94MB computer won't work btw

---

### Post by tdrusk on 2007-11-26
[http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html)
> Method 2:
This is quiet similar to Method 1 but the unwanted wait for Ubuntu to get loaded can be avoided , also if for some reason ubuntu freezes after loading the graphical enviornment or is just way too slow even to load the graphical enviornment . Put the Ubuntu CD in the drive boot the computer now when the Grub Boot menu is show press F6 to edit the boot options and **add line single at the end of the boot parameters .**

Now boot the edited menu item , this would boot the ubuntu system into the console quiet quickly now do the following steps : -

Now if you have swap partition on a drive say /dev/hda5 type this sudo swapon /dev/hda5

This would activated the swap partition which then could be used by the Live CD .

To see if the partition turned up correctly issue command
sudo swapon -s

Also if you donnullt have a swap partition i would recommend that you create one by launching the fdisk utility also try having some unpartitioned space for use during the installer since the manual editing of the partition table in ubuntu during installation tends to crash the installer over 80% of times i had numerous hang up during installation of ubuntu.

now at the console type : startx

this would take you to the graphical Gnome enviornment and if all went fine it should work at a usable speed. Now go to System - > Administration -> Install and follow the instructions to install the Ubuntu System on to the hard drive .

Now after installation is complete remove the CD from the drive re-boot the computer now at the grub menu press e and remove single from the boot parameter boot the ubuntu system.

After ubuntu is loaded type sudo gedit /boot/grub/grub.conf and remove all reference to single from the configuration file. and reboot the computer your ubuntu should be configured to be used on this computer now.


When following this, what does he mean by whats in bold?


ALSO..

I have other computers. Is there any way I can install with them, move the hard drive to the other, and configure it for the new computer?

---

### Post by Joe Dinmore on 2007-11-26
> **tdrusk said:**
> I have low memory computers (256 mb and a 94 mb). I don't have access to a alternate cd, just a live cd. What can I do to install?

I run Feisty with 256MB RAM. It's pretty good.
For the smaller box ... maybe DSL or Puppy?

---

### Post by tdrusk on 2007-11-26
> **Joe Dinmore said:**
> I run Feisty with 256MB RAM. It's pretty good.
For the smaller box ... maybe DSL or Puppy?

Yeah just forget about the smaller box. I think the motherboard is done for.

---

### Post by master_kernel on 2007-11-26
> **nathangrubb said:**
> installing on a 94MB computer won't work btw
I installed Ubuntu on an old 32MB machine and it worked fine (but I was using alternate). Try Xubuntu. I think the min memory for that is pretty low.

---

### Post by tdrusk on 2007-11-26
any more ideas?

---

### Post by -grubby on 2007-11-26
> **master_kernel said:**
> I installed Ubuntu on an old 32MB machine and it worked fine (but I was using alternate). Try Xubuntu. I think the min memory for that is pretty low.

I don't believe you can run GNOME with 32megs of RAM

---

### Post by FuturePilot on 2007-11-26
There's a way you can launch only the installer on the Live CD. When you first boot it, press More Options (F6?) and add 
```
ubiquity-only
``` 
to the end of the line.

---

### Post by Dr Small on 2007-11-26
> **tdrusk said:**
> [http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html)



When following this, what does he mean by whats in bold?


ALSO..

I have other computers. Is there any way I can install with them, move the hard drive to the other, and configure it for the new computer?
Yes, you should be able to install it on another system with more RAM (if you have one), and move the hard drive over to the other system (with low RAM) and reconfigure X to work for that one.

I would try that. But personally, I would use IceWM as it is even lighter than Xfce.

Dr Small

---

### Post by tdrusk on 2007-11-27
> **FuturePilot said:**
> There's a way you can launch only the installer on the Live CD. When you first boot it, press More Options (F6?) and add 
```
ubiquity-only
``` 
to the end of the line.

ooo I gotta try that. Thanks!

---

