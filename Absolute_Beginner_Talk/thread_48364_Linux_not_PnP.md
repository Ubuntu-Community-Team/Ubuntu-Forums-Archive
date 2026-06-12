---
title: "Linux not PnP?"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by sooqing on 2005-07-12
From what I read, its totally possible for users to plug out their USB devices like mouses, modems, etc.. when I am in the working environment.. however, if I were to plug out any USB devices I have, the system hangs immediately.. even if I am in the single user mode (init 1)

Is this common?

Been suffering from this problem for a long time, I note that it affects the latest Ubuntu, Fedora Core 1, 2, 3, Slackware 10.

Never experienced this when using Windows XP and x86 Solaris.

---

### Post by roblubbers on 2005-07-12
you would have to umount attached usb-drives etc.

Also if a device is in use, for example a sub-mouse, you'd have to stop the device before removing it.
Which is basically the same as in windows

---

### Post by Jussi Kukkonen on 2005-07-12
*Is this common?*

I've never seen behaviour like that. I've used multiple different desktop and laptop machines with varying usb devices (wireless keyboard, mouse, hard disk, memory stick, wlan card, digital camera) and plugged all of those in and out without problems.

If you've already tried with different devices on linux (and different operating systems on the same machine), I'd say your usb hub and linux don't get along... Anything in the system logs after a hang?

---

### Post by sooqing on 2005-07-12
hi!

do u mind telling me how to umount a device like a cdrom drive (using laptop), usb mouse, modem (speedtouch 330)? never knew u can actually umount them..

for windows xp, i can just plug the 3 devices out without 'stopping' them and xp just carry on fine..

---

### Post by Mr. Electric Wizard on 2005-07-12
Under Places -->Computer, Right Click, Unmount

---

### Post by az on 2005-07-12
In a console, type 
sudo tail -f /var/log/messages

and unplug a device

What is displayed as it crashed.

also, file a bug report

bugzilla.ubuntu.com

---

