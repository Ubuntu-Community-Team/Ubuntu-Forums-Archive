---
title: "Help please"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-14
ok have a os that is in iso form, and i cant burn it do disc?
anyway i could make it boot without disc?

---

### Post by llamakc on 2007-09-14
Fix the title on your post. You know that isn't helpful to other people searching the forum.

I don't know why you can not burn it, but you could put the files on a USB stick, and if your BIOS supports booting off of that sort of media you could boot from it.

---

### Post by PmDematagoda on 2007-09-14
I don't think you can boot from the Linux OS unless it's through the CD. What's the OS you're trying to install? And what's the CD burning software you have?

---

### Post by lisati on 2007-09-14
If it's an "ISO" file you downloaded from Ubuntu, you can burn it to CD - just remember to use the "burn disk image" option of your software,

---

### Post by Tootles on 2007-09-14
i cant burn it to cd and no usb, any other way?

---

### Post by PmDematagoda on 2007-09-14
Could you please give us the name of the OS you are trying to install and the CD burning software you are using?

---

### Post by oilchangeguy on 2007-09-14
what's with the two threads on basicly the same subject?
[http://ubuntuforums.org/showthread.php?t=551224](http://ubuntuforums.org/showthread.php?t=551224)
don't do it.

---

### Post by llamakc on 2007-09-14
> **PmDematagoda said:**
> I don't think you can boot from the Linux OS unless it's through the CD. What's the OS you're trying to install? And what's the CD burning software you have?

No, you can easily boot through any media that your BIOS supports booting from. 

Examples: Floppies, CD's, USB, Netboot for alternatives.

---

### Post by Tootles on 2007-09-14
ok nvm that, i installed Virtual box, when i try and run the os, it sais this:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 so i type /etc/init.d/vboxdrv setup, i get this
root@sergey-desktop:~# /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ ok ]
 * Recompiling VirtualBox kernel module vboxdrv
 * Look at /var/log/vbox-install.log to find out what went wrong
root@sergey-desktop:~#

---

### Post by llamakc on 2007-09-14
Search the forum for virtualbox how-to's if you have a new, different problem.

---

