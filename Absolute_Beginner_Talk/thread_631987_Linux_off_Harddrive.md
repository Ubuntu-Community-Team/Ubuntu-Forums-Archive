---
title: "Linux off Harddrive??"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by animal00043 on 2007-12-05
How do i delete linux and get windows XP back onto my harddrive.. AH!!!


I tried to set my BIOS boot up settings to boot off my CDROM first and have the windows XP disc in, but when i get to the screen that says booting off CDROM, press any button to continue, i pound on my keyboard at all the buttons and nothing registers, and grub starts up.. I have tried a different keyboard too. I built this computer so know it inside and out but i can not erase this stuff.. please help me.. god help me, and my computer:mad:

---

### Post by Aseld on 2007-12-05
Does the keyboard work any other time - e.g., in Ubuntu?

---

### Post by animal00043 on 2007-12-05
yes, thats the thing.. I am trying this GParted thing to see if i cant just delete the partition.. Im not to into the computer commands, i put it together but dont know the language of computers, i just want windows back.. please help me.

---

### Post by Aseld on 2007-12-05
Deleting the partition won't help if you can't boot up to your Windows install CD. It seems to me like the computer isn't recognising the keyboard - is it USB or PS2?

---

### Post by animal00043 on 2007-12-05
USB and how do i get rid of Grub then? i have tried both

---

### Post by Aseld on 2007-12-05
Getting rid of GRUB isn't the problem. The problem is getting your Windows CD to boot. The only thing I can suggest is to try using a PS2 keyboard to do the installation - it seems to me like the USB keyboard would need a driver to work.

---

### Post by bodhi.zazen on 2007-12-05
To remove Ubuntu you need to restore the window boot program and then just delete or reformat the Ubuntu partition.

For the MBR : 

From the Ubunt Live CD:

	1. Boot live CD, open a terminal.

	2. Enable The Universe repositories (System->Administation->Software Sources : tic "Community maintained Open Source software (universe)"

	3. Install  ms-sys
		```
sudo apt-get update && sudo apt-get install ms-sys
```

	4. Restore MBR
		```
ms-sys -w /dev/<drive>
```
		<drive> = your windows hard drive (/dev/hda)

	* you might need to ms-sys -p or ms-sys -w /dev/<partition>

	How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
	man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

----------

From Knoppix :  sudo install-mbr /dev/hda

----------
See also Windows Boot Disk:
	[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)


See this link : [http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by animal00043 on 2007-12-05
whn you say <drive> is my drive, how do i know what my drive's name is called? i tried /dev/hda and it says it does not exist..

---

### Post by bodhi.zazen on 2007-12-05
Open a terminal and enter :

```
sudo fdisk -l
```

This will list your drives. If not /dev/hda then probably /dev/sda

Make sure you understand partitioning terminology, see if this helps :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by thelatinist on 2007-12-05
None of the above will help you if you can't boot from your Windows XP CD.  Try going into bios settings and set the first boot device to your CD-Rom drive.  You could even disable boot from hard drive.  Just remember that after you reinstall windows you will need to change your bios settings back, so write them down.

---

