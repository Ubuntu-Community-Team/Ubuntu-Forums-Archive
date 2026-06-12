---
title: "Boot problems"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by steviecee on 2005-10-22
Can someone please help as I can no longer boot into Ubuntu.

Intsead of going to the login screen, I get a window which appears to be for remote hosting.  If I select cancel the window disappears for a few seconds and then re-appears.

I believe I am a victim of my own curiosity and must have inadvertently change a configuration somewhere along the line.

I would be grateful if someone could help as I have been force to go back into WindowsXP.

---

### Post by tehwa on 2005-10-22
I'm not familiar with this remote hosting window. Is it in text only mode, or GUI like the standard Ubuntu login screen?

You may be able to reconfigure GDM to resolve this. You will need to get boot into Ubuntu recovery mode.

Before GRUB loads, it should give you a few seconds to press 'ESC' to select from a menu. This menu should offer the option of booting into Ubuntu Recovery Mode.

This will give you a command line interface, where you can run the command:```
sudo dpkg-reconfigure gdm
```
Someone else on these forums must know this remote hosting business though.

---

### Post by steviecee on 2005-10-23
Thanks tehwa,

Its a GUI but I'll try what you suggest.  Failing this I may just re-install Ubuntu.

---

### Post by steviecee on 2005-10-23
Hey tehwa,

I have now reinstalled Ubuntu but thanks anyway.

:roll:

---

