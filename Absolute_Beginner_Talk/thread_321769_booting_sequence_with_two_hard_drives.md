---
title: "booting sequence with two hard drives"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-12-19
I have a Dell Dimension 9200 with two separate hard drives.  Windows is installed on one, and I just recently installed latest version of ubuntu on the other.  

I havent been able to find a way to select which hard drive to boot.  Default is the windows drive, as set in the Bios, but I dont have the option of changing the boot sequence to the other drive. 

Does anyone know if there's any software available that would prompt me upon each computer restart to chose which drive to boot off of?  

Thanks

---

### Post by milton1 on 2006-12-19
Did you install grub with ubuntu? If grub is installed on the MBR, you can change the default boot by editing /boot/grub/menu.lst

---

### Post by bulldog on 2006-12-19
Install GRUB on the first [boot] disk and you can choose if you want to boot windows or ubuntu.
But if you installed ubuntu already it should be there!!
Or did you disconnect the windows drive?

---

### Post by EdThaSlayer on 2006-12-19
I know it is possible to choose which hard drive to boot via the bios.
All you have to press is F2 during startup(its F2 for me, could be another button for you) and go to boot.
Under boot there should boot device priority, and choose the hard drive with ubuntu and set it to boot before your windows xp hard drive.

Hope this helps.:D

EDIT:I was a bit late, GRUB should also work for this.
EDIT1:I kind of misread. I finally read your BIOS part, you can ignore what I posted.

---

### Post by insane_alien on 2006-12-19
surely grub can handle this. if you install grub on the primary drive it should still allow you to select an OS on the secondary.

---

### Post by oscar78 on 2006-12-19
Yes, I disconnected the windows drive as I installed Ubuntu...that must be my problem.  It would probably be easiest just installing ubuntu again, with both drives connected, no?

---

### Post by bulldog on 2006-12-19
Nope just install GRUB on (hd0)

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.
Be sure to do the setup on (hd0)!!!!

---

### Post by bobpur on 2006-12-19
If you installed Windows first and Ubuntu second, you should have installed grub. Grub will give you the choice of booting into the OS you want.
If you installed Ubuntu first and Windows second, Windows overwrote grub leaving windows as the only OS you have access to.
The linux and Ubuntu Gods probably have a quick little fix for this, but I am not privy to such info:)
I would re-install both OS's doing windows first and then Ubuntu.
If this is the way you done it you might have a borked ubuntu install. Re-install ubuntu paying attention to the prompts asking about grub and where you should install it.
Good Luck.

---

### Post by oscar78 on 2006-12-19
Ok, it looks like I successfully installed the grub.  Now upon rebooting, however, I only have 3 Ubuntu OS boot options...no windows, and for each selection I have: "Error 17, cannot mount selected partition"

---

### Post by oscar78 on 2006-12-19
It looks like the grub cant mount any of the selected partitions, and now I can't get any os to boot.  Does anyone have any suggestions?  

Thanks

---

### Post by confused57 on 2006-12-19
> **oscar78 said:**
> Ok, it looks like I successfully installed the grub.  Now upon rebooting, however, I only have 3 Ubuntu OS boot options...no windows, and for each selection I have: "Error 17, cannot mount selected partition"

Boot up with the live cd, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L"

This should show your drives & partition tables and help to reconfigure grub to boot both OS.

Here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Since you've already installed grub to the Windows mbr, this wouldn't be feasible unless you repaired the Windows mbr...I think what happened in your case is that you probably installed Ubuntu with the drive connected as master, when you reconnected it as the slave drive, it changed the root partition identification...I'm not sure if that's the case or not.

You could also try modifying the boot options of grub at the grub menu, highlight the first Ubuntu entry, press "e" for edit, then try changing the root from (hd0,0) to (hd1,0) and you might also need to change the kernel line to /dev/hdb1...then try to boot.  This is only temporary, but if you're able to boot Ubuntu, you can make it permanent in your /boot/grub/menu.lst

---

