---
title: "Ubuntu partition not bootable"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by organicanagram on 2008-12-04
Hi everyone, I've just installed Ubuntu on my macbook, but it seems that the ext3 partition (15 GB) isn't bootable (i'm dual-booting). I looked around and it seems that I need Lilo, but that getting Lilo could erase the boot loader for OSX. Does this mean I wouldn't be able to boot into OSX?

Another person said something to this effect for ubuntu/windows vista:

"Thus I can't just replace my boot loader with Ubuntu's boot loader. But according to the descriptions I've found, at least one Linux boot loader doesn't need to reside in the MBR, and can instead be in the Linux root partition, where it can be invoked by my boot loader."

What should I do to be able to boot into linux and OSX?

---

### Post by Kellemora on 2008-12-04
Hi OA

I don't know much about lilo, I've been using Grub.

But no matter what you use there has to be a STAGE ONE bootloader in the MBR so your computer knows WHAT to boot up.  The default is the first item on the list.

You CAN keep your bootloader on the Ubuntu partition, that's no problem because stage one points to where the bootloaders are located.  I keep my Grub bootloader on my Ubuntu partition for all distro's on my machines.  One place makes them all easy to find.

Ubuntu/Grub is about the friendliest bootloader around, it never ignores other OS's on your system!

But here are the steps to fix your problem:
Use a LIVE CD that can get you into a Root Terminal.
in the terminal type:
Sudo grub
then type in:
find/boot/grub/stage1
use this info to set your root device below:
device may be different on your machine, ???? is stage1:
type (with proper figures):
root (hd0,1) ???? 
setup (hd0)
quit
When you reboot you should see Grub, hit your space bar to stop it from continuing to boot until you select which OS you want to boot up to.

TTUL
Gary

---

### Post by linux_tech on 2008-12-04
Here is a good guide to installing ubuntu on a macbook  
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by linux_tech on 2008-12-04
Installing Ubuntu after Mac OS X

If you get an error message during boot such as HFS+error in the bootloader. The Super Grub Disk is a useful tool for recovering Linux GRUB and the Windows MBR(Master Boot Record).

instructions here:[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installing_Ubuntu_after_Mac_OS_X](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Installing_Ubuntu_after_Mac_OS_X)
supergrubdisk here:  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by organicanagram on 2008-12-04
Okay, so I pressed CTRL+ALT+F7 to get into the terminal, then sudo su to get root access, then sudo grub to (page with "Minimal BASH like line editing is supported"). find/boot/grub/stage1 yields an unrecognized command. 

I haven't tried super grub disk yet, maybe tomorrow.

---

### Post by bapoumba on 2008-12-05
Moved to Apple Users.

---

### Post by cyberdork33 on 2008-12-06
This is a known problem. You do not need to replace the bootloader, grub is already installed.

See here to fix the booting issue:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

To find specific documentation for your Macbook version, see the "Before you post" link in my signature.

---

### Post by organicanagram on 2008-12-11
Okay, thanks a lot guys. It now opens on startup. 
But I edited something incorrectly, and now it says that
"could not load /lib/modules/2.6.29-9-generic/modules.dep" which is a fatal error, when it runs the startup check.

I think that was the thing i edited, now i need to open it so I can fix it. I think what i entered in terminal was
sudo gedit /boot/grub/menu.lst to get that file. 

Since it's a fatal error, I can't login to ubuntu with from startup or if i boot from the CD and select boot from first hard disk, which i guess is the same thing. "Try Ubuntu with no change to your computer" is another option, but opening menu.lst yields a blank window with the trial user.

I can't sudo gedit /boot/grub/menu.lst with CTRL+OPTION+F6 (terminal?) either when I'm trying to boot from the hard disk after it shows the error. From where can I open it? It seems all my options are used up.

---

### Post by pxwpxw on 2008-12-11
> **organicanagram said:**
> Okay, thanks a lot guys. It now opens on startup. 
But I edited something incorrectly, and now it says that
"could not load /lib/modules/2.6.29-9-generic/modules.dep" which is a fatal error, when it runs the startup check.

I think that was the thing i edited, now i need to open it so I can fix it. I think what i entered in terminal was
sudo gedit /boot/grub/menu.lst to get that file. 

Since it's a fatal error, I can't login to ubuntu with from startup or if i boot from the CD and select boot from first hard disk, which i guess is the same thing. "Try Ubuntu with no change to your computer" is another option, but opening menu.lst yields a blank window with the trial user.

I can't sudo gedit /boot/grub/menu.lst with CTRL+OPTION+F6 (terminal?) either when I'm trying to boot from the hard disk after it shows the error. From where can I open it? It seems all my options are used up.

The intrepid kernel version would be 2.6.27-7 so unless you have jaunty there or have upgraded the kernel, the 2.6.29-9 might be the error in the grub boot menu.
But you can choose other entries from the grub boot menu, might be one that works unless you edited them all.
If you dont see the menu, you need to hit escape key to get into it.
Then you can also edit the menu  with 'e'  and see what the other entries say,  and correct the error and login to fix the menu.lst.

---

### Post by cyberdork33 on 2008-12-12
> **organicanagram said:**
> "Try Ubuntu with no change to your computer" is another option, but opening menu.lst yields a blank window with the trial user.
You can boot from the livecd, mount your Linux partition, and edit the menu.lst there. The menu.lst doesn't exist on the LiveCD which is why you get a blank (new) file.

---

