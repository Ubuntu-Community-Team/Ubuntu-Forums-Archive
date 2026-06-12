---
title: "Virtualbox - shared folders, etc"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-08-29
Just set up Virtualbox in 7.04.  It works very well... but it seems to be hermetically sealed.  Despite installing Guest Additions, I cannot create a shared folder that works.  I mean, I have created a shared folder, but as far as I can see it doesn't do anything.  And I can't enable the USB ports on the guest system - in spite of ticking the box on the USB option.  Any ideas, that are comprehensible to a newbie?  Thanks!

---

### Post by felicity on 2007-08-29
For USB try editing this file:
/etc/udev/rules.d/40-permissions.rules
and change the line for usb devices from 0664 into 0666

for the share you should do something within the windows host from command line like:

x: \\vboxsvr\NameOfSharedFolder

---

### Post by getmeoutofhere on 2007-08-29
Thanks for replying.

For the USB, I tried doing what you suggested, but it didn't do anything.

As far as your second suggestion is concerned, I'm afraid I' m a newbie, and I don't understand its context.  I'm still at the level of cutting and pasting command lines rather than working them out for myself!

---

### Post by felicity on 2007-08-29
Regarding the USB, what exactly are you trying to do? What USB device do you want to use? What box did you refer to checking? In the settings dialog box? Did you also add the device itself? (in the Settings dialog box of VirtualBox for your virtual machine)

Referring to shared folders, that command you enter on your windows host. Go to start menu in windows, click Run, type cmd, click OK, then at the prompt type that command, press enter. Check My Computer to see if the shared network folder is there.(provided you already added it in virtual box settings dialog of course)

---

### Post by getmeoutofhere on 2007-08-29
Felicity,

Thanks very much, got the USB working, so at least the isolation is over!  Now just just a question of dealing with the shared folder.   But at least my Windows programs are now functional.

---

### Post by felicity on 2007-08-29
Awesome!

Just post if the shared folder doesn't work, if I can't help someone else might be able to. It takes a bit to get used to it but it's gotten better on newer virtualbox versions at least

---

### Post by tshearman on 2008-03-01
NM - I got it

---

