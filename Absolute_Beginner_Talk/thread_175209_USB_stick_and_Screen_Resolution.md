---
title: "USB stick and Screen Resolution"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-05-13
I am using Breezy Badger 5.10. I cannot read a USB flash drive when I plug it; what is the way to mount a USB stick (flash drive) which I use to transfer files. I cannot figure out what needs to be done? Under "System -> Preferences -> Removable Drives and Media" I saw that all the correct options have been checked. And yet the drive is not being read when plugged.

Another thing: how do I change the resolution of the login screen? Once I login, the resolution of the screen is fine, but the login screen is creating problems. Any suggestions on this.

---

### Post by Jussi Kukkonen on 2006-05-13
[QUOTE=aam-aadmi]I am using Breezy Badger 5.10. I cannot read a USB flash drive when I plug it; what is the way to mount a USB stick (flash drive) which I use to transfer files. I cannot figure out what needs to be done? Under "System -> Preferences -> Removable Drives and Media" I saw that all the correct options have been checked. And yet the drive is not being read when plugged.
[/QUOTE]

In gnome it really should automount... You should take a look at what gets logged when you plug the stick. Open a terminal, and run:
```
sudo tail -f /var/log/messages
```
Now, plug in the stick, and see what gets logged... Paste the output here.

---

### Post by aam-aadmi on 2006-05-13
I opened a terminal and started logging with
sudo tail -f /var/log/messages

and then when I plugged in the USB stick, it was automatically mounted!

---

### Post by Jussi Kukkonen on 2006-05-13
Normally the Demo effect works against you -- be lucky it works this way too ;)

---

### Post by CameronCalver on 2006-05-17
hey i have a compact flash usb thing and i pluig it in and nothing happens what would i do in fstab to mount it

---

