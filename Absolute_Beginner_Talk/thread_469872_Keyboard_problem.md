---
title: "Keyboard problem"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Tooom on 2007-06-10
I installed Ubuntu and everything seemed to go smoothly except now my keyboard isn't working. The keyboard is fine, it works right up until the login screen and then no response. I've tried changing settings in the BIOS but no change. Anybody know what's wrong?

---

### Post by Pragmatist on 2007-06-10
Post your /etc/X11/xorg.conf   If you can't log in to your system, try using a LiveCD to get the file.

---

### Post by Tooom on 2007-06-11
Can't post exact file because there's no way for me to get it off that computer as I can't get the internet to work without the use of a keyboard. I'm using the generic keyboard setting with a gateway keyboard if that helps, and it's set to that 2 (0x0f?) thing. Sorry I can't give any more information.

---

### Post by Pragmatist on 2007-06-11
You use a LiveCD like the Ubuntu LiveCD or Knoppix.  You will be running your OS of the CD not your hard drive.  This will reverse the normal state of affairs and the cd will be where the OS is, and the hard drive will be the media, like the CD usually is!  This way, you can access your hard drive, and get the file I requested.

There is no way, that I know of, to fix your system without accessing it using a boot disk, LiveCD, etc...

---

### Post by Najand on 2007-06-11
Isn't it related to this bug? [https://bugs.launchpad.net/ubuntu/+bug/110394](https://bugs.launchpad.net/ubuntu/+bug/110394)
If so, try to upgrade your Kernel to the newest version.

---

