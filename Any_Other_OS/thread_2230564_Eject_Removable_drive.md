---
title: "Eject Removable drive ???"
date: 2014-06-19
forum: Any Other OS
---

### Post by ramakanta on 2014-06-19
When I want to eject removable drive it shows it eject but unable to properly remove ( light glowing ) also drive image stay in computer folder . how to resolve this problem ???? 
[[img]http://s14.postimg.org/szm8q7fwd/eject.jpg[/img]](http://postimg.org/image/szm8q7fwd/)

:confused:

---

### Post by matt14 on 2014-06-19
This might sound pretty obvious, but you should first make sure nothing is open from the removable drive. If you did that, then I would recommend running "sudo umount [physical drive location]" from the command line. This might not fix the problem, but it could give you an error message that could help. If you don't know the physical drive location, you can figure it out by running "sudo fdisk -l"

Or you could physically pull the drive from the computer. Chances are you won't lose any data.

---

### Post by 3rdalbum on 2014-06-23
How long does the icon stay there? If you have copied any large files to the drive, they might still be copying in the background. When the "copy" window disappears, that just means that the data to be copied is in RAM, it doesn't necessarily mean that it has been put onto the disk yet. If you have been copying files to the drive they may still be copying, and you'll have to wait until the icon disappears and the notification bubble reports that the drive has been ejected.

---

### Post by ramakanta on 2014-06-23
> **3rdalbum said:**
> How long does the icon stay there? If you have copied any large files to the drive, they might still be copying in the background. When the "copy" window disappears, that just means that the data to be copied is in RAM, it doesn't necessarily mean that it has been put onto the disk yet. If you have been copying files to the drive they may still be copying, and you'll have to wait until the icon disappears and the notification bubble reports that the drive has been ejected.


even only insert and then eject , there is such problem faced .??

---

### Post by 3rdalbum on 2014-06-25
After you click Eject can you please go to a terminal and type 'dmesg' and then copy and paste the last 10 lines into this thread so we can see what's happening. Thanks.

---

### Post by ramakanta on 2014-06-26
> **3rdalbum said:**
> After you click Eject can you please go to a terminal and type 'dmesg' and then copy and paste the last 10 lines into this thread so we can see what's happening. Thanks.

```


[ 1146.115561] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 1146.116343] scsi13 : usb-storage 1-1:1.0
[ 1146.172938] WARNING! power/level is deprecated; use power/control instead
[ 1147.117308] scsi 13:0:0:0: Direct-Access     hp       v210w            0.00 PQ: 0 ANSI: 4
[ 1147.117838] sd 13:0:0:0: Attached scsi generic sg4 type 0
[ 1147.121193] sd 13:0:0:0: [sdc] 15773696 512-byte logical blocks: (8.07 GB/7.52 GiB)
[ 1147.123295] sd 13:0:0:0: [sdc] Write Protect is off
[ 1147.123306] sd 13:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1147.124428] sd 13:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 1147.133428]  sdc: sdc1
[ 1147.150158] sd 13:0:0:0: [sdc] Attached SCSI removable disk
[ 1408.814896] sdc: detected capacity change from 8076132352 to 0






```

what happens ???

---

### Post by mc4man on 2014-06-26
removable media is treated in different ways depending on the device
Some can be  both ejected & safely removed (powered down), some just ejected, some just safely removed. (as far as presented options..
The "Computer" location will show any attached device that is still powered

Your device was successfully ejected - 
"sdc: detected capacity change from 8076132352 to 0"

---

### Post by ramakanta on 2014-06-26
> **mc4man said:**
> removable media is treated in different ways depending on the device
Some can be  both ejected & safely removed (powered down), some just ejected, some just safely removed. (as far as presented options..
The "Computer" location will show any attached device that is still powered

Your device was successfully ejected - 
"sdc: detected capacity change from 8076132352 to 0"

then why pendrive light glow after eject ???

---

### Post by mc4man on 2014-06-27
> **ramakanta said:**
> then why pendrive light glow after eject ???
Because eject doesn't power off the device.

---

### Post by ramakanta on 2014-06-27
> **mc4man said:**
> Because eject doesn't power off the device.

is there any problem to the device , if removed it with power glow ??

---

### Post by mc4man on 2014-06-27
> **ramakanta said:**
> is there any problem to the device , if removed it with power glow ??

Not at all

---

