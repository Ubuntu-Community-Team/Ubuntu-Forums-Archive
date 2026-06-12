---
title: "Camera Question. Worked on Dapper but not on Edgy"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by harerama on 2007-01-02
Hi there!

My digital camera worked completely fine on Dapper. However when I plugged it in to Edgy I got message like this. I am only able  to click cancel.:( 

Please help. How can I fix this?

Sincerely.

---

### Post by MkfIbK7a on 2007-01-02
not sure whats happening but you could download digikam and use that it works for me:?

---

### Post by harerama on 2007-01-02
The message I got is an attached file.

Thanks

---

### Post by MkfIbK7a on 2007-01-02
i saw but  i still dont know what the problem is you could try changing the permission of the camera, also what program is that a screenshot of?

---

### Post by harerama on 2007-01-02
How can I change the permission of the camera?
The program is that when I plugged the camera into computer it automatically pops up on screen. 
 I actually don't know what it is.

---

### Post by MkfIbK7a on 2007-01-02
what kind of camera do you have?

---

### Post by bluenova on 2007-01-02
System > Preferences > Removeable drives and media
Cameras tab
Change the command to the command you want the computer to run when it detects your camera. I use:
digikam --download-from /media/EOS_DIGITAL

---

### Post by harerama on 2007-01-02
Cheers,
> what kind of camera do you have?
My camera is Canon PowerShot A710IS

> Change the command to the command you want the computer to run when it detects your camera. I use:
digikam --download-from /media/EOS_DIGITAL

Please take a look at the attachment. Is this what I should do?

Thanks

---

### Post by harerama on 2007-01-02
Or should I go back to Dapper? :rolleyes: 

Cheers,

---

### Post by harerama on 2007-01-02
Anyone? :( 

It worked fine on Dapper.

---

### Post by melon2006 on 2007-01-04
Canon PowerShot A710IS on Edgy Eft  (works on 64-bit Edgy, but should also work on other platforms)

1. connect the camera (by usb cable, set camera in "playback" mode)

2. to check your camera's ID run terminal and enter following command:
```
 lsusb | grep -i canon
```
This should give something like:
```
Bus 001 Device 008: ID 04a9:3138 Canon, Inc.
```

3. edit  file 45-libgphoto2.rules file, i.e. enter following command:
```
sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
```

4. find last line ```
LABEL="libgphoto2_rules_end"
``` and add line BEFORE it:
```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3138", MODE="0660", GROUP="plugdev"
```
This adds A710is to known devices.
Save changes, leave editor.

5. run
```
 sudo invoke-rc.d udev restart
```
(or reboot computer)

Camera should work, after pluggin it and switching on, import message should appear. You can use standard gThumb of Fspot to import.

I still don't know if it's possible to use A710is as common usb disk drive (so far it's not listed in "Computer" window.

I hope you'll find it useful.

---

### Post by harerama on 2007-01-05
To melon2006,

Thanks. However still nothing happens. ](*,) 

By the way when I plug my camera into my computer the Device Manager apparently recognize it.

Also my camera worked perfectly fine on Dapper. But now when I reinstalled Dapper it doesn't work any more.

Thanks anyway.

---

### Post by melon2006 on 2007-01-06
Are you sure that after 
```
 lsusb | grep -i canon
```
you get IDs which are listed in  /etc/udev/rules.d/45-libgphoto2.rules ?

Adding those two numbers was the only thing I've done and camera started to work.

Oh, one more thing. I've added line
```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3138", MODE="0660", GROUP="plugdev"
``` ** TWICE** so it looks like
```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3138", MODE="0660", GROUP="plugdev"
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3138", MODE="0660", GROUP="plugdev"
```
but I'm not sure why and if it's important (only thing I've done was searching some forums for similar problems and try their solutions).

---

### Post by iitywygms on 2007-01-08
> **harerama said:**
> To melon2006,

Thanks. However still nothing happens. ](*,) 

By the way when I plug my camera into my computer the Device Manager apparently recognize it.

Also my camera worked perfectly fine on Dapper. But now when I reinstalled Dapper it doesn't work any more.

Thanks anyway.

Harerama
You and I both have the same problem.  You posted on another thread that I started.  
Run this command as melon2006 states.
 lsusb | grep -i canon
Pay attention to the output.  I copy and pasted what melon2006 said but had to change some things in it. (My id was 3136 and not 3138.)
After I followed his advice my camera works great now.
Thank you melon2006!

---

### Post by harerama on 2007-01-08
Hello there,

It sounds really good.
> After I followed his advice my camera works great now

However before I saw melon2006's and iitywygms's posts I've erased Edgy and replaced it with Dapper!  Then my camera works fine now. Nevertheless next time I decide to upgrade Dapper to Edgy. I will try your advices.

Thank you. I appreciate your kindness.

---

### Post by MkfIbK7a on 2007-01-08
try this

grep "usb_device" /etc/udev/rules.d/*

post the output

---

### Post by nekr0z on 2007-03-10
Got the very same problem with Canon PowerShot A80. The solution by Melon2006 doesn't work: those lines have already been in that file, but the error remains.


**grep "usb_device" /etc/udev/rules.d/*** gives:
```
/etc/udev/rules.d/20-names.rules:SUBSYSTEM!="usb_device", GOTO="usb_device_end"
/etc/udev/rules.d/20-names.rules:IMPORT{program}="usb_device_name --export %k"
/etc/udev/rules.d/20-names.rules:LABEL="usb_device_end"
/etc/udev/rules.d/40-permissions.rules:SUBSYSTEM=="usb_device",         MODE="0664"
/etc/udev/rules.d/45-hplip.rules:SUBSYSTEM!="usb_device", GOTO="hplip_rules_end"
/etc/udev/rules.d/45-libnjb.rules:SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libnjb_rules_end"
/etc/udev/rules.d/45-libsane.rules:SUBSYSTEM!="usb_device", GOTO="libsane_rules_end"
```

Any ideas?

---

