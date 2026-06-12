---
title: "Import Photos error message"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by JackS on 2007-01-11
I've installed v6.10 Edgy recently.  900MHz Pentium2, old clunker.
Having a bit of trouble with the digital camera interface via USB.

I am able to use USB with a thumb-drive.  It auto mounts when inserted
and I can read and write with it.  So the USB port seems functional.
I 'eject' the thumb-drive and remove it.  No other USB devices are
connected.  All this seems to work perfectly.

However, when I attach the USB port to my digital camera it begins
the Import Photos application and then halts with the following message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I hope that this can be cured with a simple file/directory permission
adjustment.  But I just don't have enough experience to know where
to fix the problem.  Could anyone out there supply me with a clue?

Thanks,
-Jack

---

### Post by rko618 on 2007-03-13
Try [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

if that doesn't work then check to make sure your camera is listed in /etc/udev/rules.d/45-libgphoto2.rules as described here: [http://ubuntuforums.org/showthread.php?t=286730](http://ubuntuforums.org/showthread.php?t=286730)

---

### Post by davesmith on 2007-03-13
rko618

I have a Fuji FinePix Zoom F30 and get the error message

I tried bugfix 91250, but I cant save the 45-libgphoto2.rules file. It gives an error message that it&#347; a read only file, and I dont have permission to save it.

How do I change and then save the file? Any help appreciated

Davesmith

---

### Post by FM1 on 2007-03-13
You need root privileges. Open a terminal and type:

sudo gedit /etc/udev/rules.d/45-libgphoto2.rules

Enter your password when prompted.

---

### Post by Milan SPK on 2007-03-14
i read all i could find both on forums and google, but couldnt see what am i doing wrong... i have kodak c533 camera 
```
milan@milan-desktop:~$ lsusb
Bus 001 Device 002: ID 040a:05a2 Kodak Co. 

```

i added as sugested a line in /etc/udev/rules.d/45-libgphoto2.rules at the end of list, before LABEL="libgphoto2_rules_end" :
```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"
```

i restarted udev
```
sudo /etc/init.d/udev restart
```

but still no change. i rebooted the machine to, but nothing. i would really appreciate any help, thanks.

---

### Post by cmapesjr on 2007-03-14
Worked great for me! Thanks for the help!

---

### Post by rko618 on 2007-03-15
> **Milan SPK said:**
> i read all i could find both on forums and google, but couldnt see what am i doing wrong... i have kodak c533 camera 
```
milan@milan-desktop:~$ lsusb
Bus 001 Device 002: ID 040a:05a2 Kodak Co. 

```

i added as sugested a line in /etc/udev/rules.d/45-libgphoto2.rules at the end of list, before LABEL="libgphoto2_rules_end" :
```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"
```

i restarted udev
```
sudo /etc/init.d/udev restart
```

but still no change. i rebooted the machine to, but nothing. i would really appreciate any help, thanks.

Milan SPK, did you try [bugfix 91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250")?

Basically you probably need to change the line 3 of /etc/udev/rules.d/45-libgphoto2.rules  from
 
BUS!="usb*", GOTO="libgphoto2_rules_end"

to

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

---

### Post by DavidTangye on 2007-03-17
I have started to get the same error. Everything worked fine until the last few days.

---

