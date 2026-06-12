---
title: "Display corrupted after screen resolution change"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by crazydruid on 2007-04-28
Hi,im running Ubuntu Feisty on my pc.I attempted to change the screen resolution by editing the xorg file after trying to follow online instructions.Alas,when i now boot into Ubuntu,the desktop display is garbled and all messed up and its not possible to view or access any folders,files etc.I can log in ok but then the display goes haywire and its not useable.I'm therefore unable to try and edit it from there. 

I am able to access Ubuntu via another installation on a seperate hard drive,installed on the same pc.Is there anyway i can use this to repair the problem on the other drive or is there a way of editing the screen resolution via GRUB? Many thanks for any help.

---

### Post by GMachine_24 on 2007-04-28
Hi:

I had this same problem. If I remember correctly, I had to boot to a command line; log in from there and then maneuver via command line to the xorg configuration file and change/reset the resolution settings - sounds as if you need to at least change your 'default' settings... pick something you know will work (obviously).

You can also try one of the 'live' boot disks, such as Knoppix, and attempt to change the xorg file settings by accessing your Ubuntu hard drive that way.

Hope this helps.

A note: you can always restart xorg once you have logged in by typing

ctrl+alt+backspace

But unless you change the xorg file you will just end up back with the same mess.

What kind of video card are you using?

--GM

---

### Post by crazydruid on 2007-04-28
Ok my friend,i will try the Knoppix cd option first.Thanks for that.Not really sure what the video card is as i'm a bit clueless on that.I'll post more later.Cheers once again

---

### Post by crazydruid on 2007-04-28
I've managed to get back my old display so thats a relief.Still stuck with the wrong refresh rate though (too low) .Not too confident of changing it now after the chaos of the last attempt.Daft thing is i got it working ok in Ubuntu Edgy but cant seem to resolve the problem in Feisty !

---

### Post by Josey on 2007-04-28
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

