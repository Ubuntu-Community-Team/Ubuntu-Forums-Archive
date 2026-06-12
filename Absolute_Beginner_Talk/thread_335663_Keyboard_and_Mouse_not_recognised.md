---
title: "Keyboard and Mouse not recognised"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by iansl2000 on 2007-01-10
I have downloaded the Live CD and loaded on my PC.

The keyboard works ok when first selecting the boot option but when ubuntu has finished loading the mouse and keyboard do not work.

I have tried a usb, a serial and a ps2 mouse but none seem to work.

The PC does not have windows loaded on it and I really wanted to install ubuntu straight to the hard disk.

Does anyone have any ideas what I can try next.

May thanks in advance for any help

ian

---

### Post by XtremeSki2001 on 2007-01-10
> **iansl2000 said:**
> I have downloaded the Live CD and loaded on my PC.

The keyboard works ok when first selecting the boot option but when ubuntu has finished loading the mouse and keyboard do not work.

I have tried a usb, a serial and a ps2 mouse but none seem to work.

The PC does not have windows loaded on it and I really wanted to install ubuntu straight to the hard disk.

Does anyone have any ideas what I can try next.

May thanks in advance for any help

ian

It might help if you shared what brand/type of mouse and keyboard you are using.

---

### Post by mykalreborn on 2007-01-10
:-k hmmm
it sound like an xserver error.
try to boot into recovery mode and type 
```
sudo dpkg-reconfigure xserver-xorg
```
it will show you a bunch of options. read carefuly and try to leave the default settings in the non-keyboard and non-mouse sections. when it gets to the mouse and keyboard settings check out what it says. you should use an normal ps/2 mouse and a normal "microsoft natural keyboard", without any extra buttons. at the mouse section it should say ps/2 mouse and at the keyboard should say pc-104.
if not... well.. i don't know

---

### Post by iansl2000 on 2007-01-11
Thanks for the replies.


The keyboard came alive long enough to install Ubuntu onto the hard disk but is then dead on some boots and alive on others. 
It is a Hewlett Packard Model 9203 so I set the keyboard type to 'Hewlett Packard Internet keyboard' 'uk' in System-Preferences.

I have got the preferred mouse (serial version) working now by setting
Device to "dev/ttyS0"
Protocol to "Auto"

Any more ideas on the keyboard would be gratefully recieved.

Thanks again

---

### Post by iansl2000 on 2007-01-11
Sorry for Hewlett Packard read Packard Bell

ian

---

### Post by ricci on 2007-01-20
Can I share something about this case?
I used to have problems with my keyboard and mouse when booting on Ubuntu- but i have a simple solution, by removing all attached devices (USB/Firewire) and disks on the drives. The Ubuntu would work fine. 

But if the keyboard and mouse did not work even on XP, the keyboard / mouse is defective and needs to be replaced.

:-) I hope I helped everyone on my little discovery.

---

### Post by gcai on 2007-01-31
Unbelievable.... I had same problem: mouse & keyboard recognized sometimes and not others.  I did what ricci did: just unplugged mouse and keyboard, plugged them in again; and removed a floppy that was in the drive ... which wasn't even inside all the way through!  Boot up again and stopped having problems.  I did this three days ago and both have been recognized all times.
I think it's amazing Ubuntu would have such a bug.

---

### Post by jmcts on 2007-02-05
That just happened to me too.  I installed a new internal card reader and then my mouse and keyboard were fritzy.  I tried a new USB mouse, instead of PS2, and it worked.  Weird. . . .

---

### Post by gcai on 2007-06-02
It looks like the issue is solved in Feisty :)

---

### Post by acetone on 2007-06-07
Hi,

Similar problem here. It was all working on V6.1 of ubuntu. But I decided to load 7.04 the PS2 mouse isn't recognised any more. so I plugged in a USB mouse (std microsoft OPtical), which is recognised but works like a rock on the end of a piece of elastic and is therefore virtually unusable. The system is an old PII 333 dual processor. It works with windows and the previous version of ubuntu, Help Please

---

