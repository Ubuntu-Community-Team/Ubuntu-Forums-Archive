---
title: "USB devices are not recognized"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by gadean on 2006-07-17
I know it's been discussed in other posts but nobody seems to have the same problem.  I cannot mount any USB devices. (mp3 players, memory sticks, hard drives, etc)  In fact, the only ways I know a USB device has been plugged in is by lsusb or the system log.  No matter what I do I cannot get the device to mount.  (the only explaination for this is unrecognized hardware.  Device Manager reports 2 unknown devices but only is manufactured by ATI (my video works.  strange?) and the other, I believe, is my modem.  (which I don't use)

I am new to Linux.  Maybe I am doing something wrong? :-k 
Is there a may to mount a device using the information reported by lsusb?

---

### Post by Bagnaj97 on 2006-07-17
are you using a USB hub or plugging the devices into the back of your computer? If you are using an unpowered USB hub then it's possible that the devices dont have enough power. Assuming you are using an unpowered USB hub try plugging directly into your computer or get a powered hub.

---

### Post by dannytherocker on 2006-07-17
I have the same trouble: my dapper (2.6.15-26) does not recognize external usb devices (hd, dvd burner, nokia 6630)! This happens with AND without my POWERED hub!
Any trouble with this kernel version ?

e-Maj

---

### Post by gadean on 2006-07-17
> **Bagnaj97 said:**
> are you using a USB hub or plugging the devices into the back of your computer? If you are using an unpowered USB hub then it's possible that the devices dont have enough power. Assuming you are using an unpowered USB hub try plugging directly into your computer or get a powered hub.

I am plugging the devices directly into the computer.   All of them were recognized when WinXP was installed so I know it's not a hardware issue.  (broken, not getting enough power, etc)

---

### Post by secallen on 2006-07-17
This won't fix your system, I just want to give you some hope. 

I installed Dapper Drake as a dual boot with XP on an Acer Aspire and its plug and play facility is amazing. I plugged in a wireless mouse and it worked immediately, none of the contemplation and baloons you get in windows. Then I plugged in a scanner and the following happened: 1) scanning software loaded automatically 2) I clicked the "Scan" buton, 3) I had a scanned picture ready for use!

---

