---
title: "Mtp device problem"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by maebe on 2007-06-10
Can not get my Samsung Yh-J70J to be recognized. I have run the following and do not know what I should do.

mtp-detect
Autodetected device with VID=04e8 and PID=5033 is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
usb_claim_interface(): Device or resource busy
Connection error.
No devices.

Any help would be appreciated

---

### Post by ntetreau on 2007-06-12
Hi,
rename the attached file from libmtp.rules.txt to libmtp.rules and copy it to /etc/udev/rules.d/ folder.  Alternativeley, you can copy and paste the following code in a terminal running in the same directory where you saved the attached file:

```
sudo cp libmtp.rules.txt /etc/udev/rules.d/libmtp.rules
```

Your device is not yet in the list of MTP device taken care of my libmtp, I am forwarding the info you posted to the developer, it will probably be taken care of by the next ubuntu release.

Nic

---

### Post by maebe on 2007-06-13
I did a search for libmtp.rules.txt and it does not exist.??

Mark

---

### Post by zyth on 2007-07-27
I have this YH-J70J device, and I got it to work in Ubuntu Feisty...

The trick is, it doesn't have to be mounted in MTP mode.  It has an undocumented UMS mode, which means it can be mounted as a normal drive, and used as a regular old USB drive.  Copy music over, and away you go.

To do this, you turn ON the HOLD button, and press and hold the record button for a few seconds while you plug in the USB cable.  You'll see the screen say 'USB Connecting' (as opposed to the normal MTP connecting), and then the disk will mount as a FAT32 USB Volume on your desktop.  From there, you can copy/move/modify/etc.

Hope this helps someone, this drove me crazy for several hours!

---

### Post by ntetreau on 2007-07-30
Sorry but I could upload the file with its original name : libmtp.rules so I had to add the .txt extension.  Remove the extension and copy it over you original libmtp.rules file.  You can do this by copy/pasting the command I wrote in my previous post.

Nic

---

### Post by maebe on 2007-08-09
Yes that works very well. However I am interested to know how you ever found it out.




> **zyth said:**
> I have this YH-J70J device, and I got it to work in Ubuntu Feisty...

The trick is, it doesn't have to be mounted in MTP mode.  It has an undocumented UMS mode, which means it can be mounted as a normal drive, and used as a regular old USB drive.  Copy music over, and away you go.

To do this, you turn ON the HOLD button, and press and hold the record button for a few seconds while you plug in the USB cable.  You'll see the screen say 'USB Connecting' (as opposed to the normal MTP connecting), and then the disk will mount as a FAT32 USB Volume on your desktop.  From there, you can copy/move/modify/etc.

Hope this helps someone, this drove me crazy for several hours!

---

### Post by zyth on 2007-08-23
A random google hit on a little blog from some fellow in france, to be honest.  I just got lucky I guess.  ;)

---

