---
title: "Importing Pictures ?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-11-29
Ya,just trying to import some pictures from a digital camera, I get this:

---

### Post by komaroveli on 2006-11-29
check your destination folder...its mnt,
try folder in your home directory (make folder "pictures" or what ever and select it for destination)

---

### Post by yabbadabbadont on 2006-11-29
What is the output of "ls -lR /dev/bus/usb"?

---

### Post by Drakkor on 2006-11-29
Yeah,get the same thing with the home folder 
here is the output:
drakkor@Ubuntu-Edgy:~$ ls -lR /dev/bus/usb
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 80 2006-11-29 18:42 001
drwxr-xr-x 2 root root 60 2006-11-29 10:34 002
drwxr-xr-x 2 root root 80 2006-11-29 10:34 003
drwxr-xr-x 2 root root 60 2006-11-29 10:34 004
drwxr-xr-x 2 root root 60 2006-11-29 10:34 005
lrwxrwxrwx 1 root root 14 2006-11-29 18:35 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2006-11-29 10:34 001
crw-rw-r-- 1 root root 189, 3 2006-11-29 18:42 004

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2006-11-29 10:34 001

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root    189, 256 2006-11-29 10:34 001
crw-rw-r-- 1 root scanner 189, 257 2006-11-29 10:34 002

---

### Post by yabbadabbadont on 2006-11-29
What is the output of "grep usb_device /etc/udev/rules.d/40-permissions.rules"?

---

### Post by Drakkor on 2006-11-29
drakkor@Ubuntu-Edgy:~$ grep usb_device /etc/udev/rules.d/40-permissions.rules
SUBSYSTEM=="usb_device",                MODE="0664"
drakkor@Ubuntu-Edgy:~$

---

### Post by johnnymac on 2006-11-29
Hey is this camera a ptp camera?  If so, the udev rules are screwed up in edgy for this.  There's a work-around I threw together..

[http://www.ubuntuforums.org/showthread.php?t=290205](http://www.ubuntuforums.org/showthread.php?t=290205)

I'm not sure if it's the same issue but hope it helps...

---

### Post by Drakkor on 2006-11-29
Great,but only seemingly attributes is that it is a 5 megapixel/3X zoom,and it's a Kodak EasyShare C533.

---

### Post by Drakkor on 2006-11-30
I am having problems with:
> I am having problems with:
Quote:
2. Add the following check_ptp_camer script to /lib/udev (make it executable): [http://librarian.launchpad.net/4933902/check_ptp_camera](http://librarian.launchpad.net/4933902/check_ptp_camera)

Please enlighten me ! ](*,)

---

### Post by johnnymac on 2006-11-30
Basically you need to do the following:

```

sudo gedit /lib/udev/check_ptp_camera

open the link provided and copy|paste the contents into the check_ptp_camera file

then make it exectuable

sudo chmod +x /lib/udev/check_ptp_camera

```

That should do it.

---

### Post by yabbadabbadont on 2006-11-30
> **Drakkor said:**
> drakkor@Ubuntu-Edgy:~$ grep usb_device /etc/udev/rules.d/40-permissions.rules
SUBSYSTEM=="usb_device",                MODE="0664"
drakkor@Ubuntu-Edgy:~$

You need to add a GROUP option to that line so that the group gets set to plugdev (like it should be...)  Here is mine as an example:
```
/home/bubba $ grep usb_device /etc/udev/rules.d/40-permissions.rules
SUBSYSTEM=="usb_device",                GROUP="plugdev", MODE="0664"

```

You will need to reboot for it to take affect.

---

### Post by fatcomet on 2007-01-16
fyi i was getting the same error while trying to import pics off my canon elura 80 into 6.10. jonnymac's procedure fixed the problem:mrgreen: 

thanks!

---

