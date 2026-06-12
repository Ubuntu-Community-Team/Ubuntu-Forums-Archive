---
title: "Scrambled graphics"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Noampod on 2008-01-22
Hi, I have a dual boot set up winxp first then ubuntu 7.10, all was working fine until recently. Now when it boots the logon screen graphics are scrambled and fuzzy. I'm running a radeon 1950 pro gfx card, thanks in advance for any help. :)

---

### Post by Thelasko on 2008-01-22
Just the logon screen?  Sounds like a setting in /etc/X11/xorg.conf.  Can you post the file?

---

### Post by Noampod on 2008-01-22
Hi, thanks for your reply. Logon screen is as far as I can go due to scrambled screen. I'm a complete novice and only had chance to tinker with ubunto before this happened, so please be patient with me.

"Sounds like a setting in /etc/X11/xorg.conf. Can you post the file"  Can you explain how to do this please?

---

### Post by jken146 on 2008-01-22
If you can boot to the login screen, try this:

Press Ctrl+Alt+F1

Use these 3 commands: ```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```

You may need to press Ctrl+Alt+F7 to get back to the GUI.

---

### Post by Noampod on 2008-01-23
I have done as you asked, though I wasn't sure of what options to choose in xorg. However I did manage to get to an unscrambled log on screen. Once I logged on it seems no matter what options I pick for screen and gfx when I reboot I'm back at the scrambled log on screen. 

Before this I was using an nvidia gfx card and all was well, now I'm on a ati x1950 pro, but I'm sure I remember booting ubuntu fine and selecting the ati card from the gfx list now that model is not in the list.

Once again thanks for your help and for any more assistance you can offer.

---

