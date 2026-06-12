---
title: "Can GRUB be installed on its own?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by John E on 2006-12-06
Yesterday, I came to boot my PC and it halted, displaying **Grub Error 17**. As far as I can tell, there's no way around this problem so I ended up having to use Windows to 'repair' my boot partition. Now I can boot into Windows but not into Ubuntu.

Is ir possible to download GRUB and install it separately from a CD or floppy disk?

---

### Post by CoolHand on 2006-12-06
Grub has changed a bit since I had to do this sort of thing but you used to be able to make a grub boot disk.  I don't think most people do that anymore but I think you can use your install disk to boot up and repair grub.  I am on vacation and don't have mine available to give you instructions.  I think in the boot screen there is a repair option on ubuntu.  I would try that first.  If that doesn't do it you can always boot the live cd do a change root and then rerun grub to reinstall it to the mbr that way.  Do a google on grub and you should be able to track down a full manual on it to get help.  Hopefully someone else here will have access to the info to give you better instructions but maybe I have given you a place to start.

---

### Post by John E on 2006-12-07
Thanks for interrupting your vacation... I didn't expect that...! The live CD doesn't seem to offer a repair option but I can press F6 which seems to let me enter an alternative boot option. I assume that this might allow me to boot up from the Ubuntu installation on my hard drive and from there, I could re-install Grub.

Does anyone know if that's possible? What would I need to enter in order to boot from my hard drive?

---

### Post by bernied on 2006-12-07
This is not so hard. You need to know which drive and partition your ubuntu installation is on. Then you use a terminal on linux to enter the grub console. Then you need two commands, BUT do not try these commands until you are sure that you know you have got this bit right, because you will lose your option to boot to windows as well:
```
$ grub
```
this enters the grub console
```
> root hd(0,2)        # BUT THIS IS PROBABLY NOT THE RIGHT PARTITION FOR YOU
> setup (hd0)
```
so the root command tells grub console where the rest of grub (grub stages 1_5 and stage 2) and your boot configuration file (menu.lst) are, and setup creates a new master boot record (also known as grub stage 1), on your first hard drive, which points to the partition where ubuntu is installed.

Note that grub's notation is different and seems a bit odd at first, numbering for both disks and partitions starts at 0, so hda1 is (hd0,0), and hdb5 would be (hd1,4).

You can use your live cd to get a terminal up (either through the GUI desktop, or Ctrl-Alt-F1 or Ctrl-Alt-F2 etc). 

Also within the grub console you can use tab completion and the cat command, so if you are not sure whether you have the right partition, you can do something like:
```
grub
```
this will give you a grub console
```
root (hd0,     # then hit the TAB key to get a list of partitions on the first drive
root (hd0,0)
cat /       #then hit TAB again to get a list of files in the root directory
```you can mess about like this without fear of messing things up, then once you find your ubuntu partition, try:
```
cat /boot/grub/menu.lst
```to see what's in the file.

See how this goes, but remember don't use grub's setup command until you are sure, or have some other easy access to the internet to get more help.

---

### Post by bernied on 2006-12-07
And to get out of the grub console use the command 'quit'

---

### Post by Sef on 2006-12-07
Read [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub).

---

### Post by Duck2006 on 2006-12-07
You can use wingrub that way you don't use the MBR of the boot drive

---

### Post by John E on 2006-12-07
Thanks to everyone who's helped on this. :)

Bernied - I printed out your instructions and they worked perfectly!

I might investigate WinGrub though - because I'd prefer something that doesn't use the MBR, if possible.

Thanks again, guys.... :D

---

### Post by bernied on 2006-12-07
Hooray!

I have a machine where I didn't want to mess with the MBR. So I put grub on a usb stick. When I want to boot linux, I put the usb stick in, then turn the power on. Once booted, the stick is no longer needed and it comes out.

You can also chainload grub from the windows bootloader - apparently.

---

### Post by Duck2006 on 2006-12-07
> You can also chainload grub from the windows bootloader

That is what Wingrub does

---

