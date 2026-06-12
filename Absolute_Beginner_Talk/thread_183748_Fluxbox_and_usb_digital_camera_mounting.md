---
title: "Fluxbox and usb digital camera mounting"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2006-05-28
HI all,
    I have just installed Fluxbox 0,9,14 and menumaker and mountapp and everything is ok on that side. My problem is when I plug in my Fuji Finepix A220 camera ,which under Gnome is recognised as a removeable drive and mounted  I cant get it to show up or mounted  using Fluxbox unless I do this.

Edit fstab to read

**/dev/sda   /media/usbdisk   rw user     0              0**

but then on boot up when Ubuntu is going thru the set up when it gets to 
**Mounting local filesystems **
it states **failed**

usbdisk now shows up as an option in mountapp and if I connect the camera I can mount it and see the contents in Tuxcommander. Any suggestions to improve on this quick and dirty method ?

thanks  guys and gals 

Philj:confused:

---

### Post by hw-tph on 2006-05-28
In order for the mounting script to pass when the camera is not plugged in, append the option "noauto" to the options in /etc/fstab:
```
/dev/hda    /media/usbdisk    rw,noauto   user    0 0
```


Håkan

---

### Post by PhilJ on 2006-05-28
Thank you my friend ,

much obliged .


Philj:D

---

