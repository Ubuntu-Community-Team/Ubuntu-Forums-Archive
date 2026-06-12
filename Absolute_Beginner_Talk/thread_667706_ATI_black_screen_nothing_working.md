---
title: "ATI black screen nothing working"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Swako on 2008-01-14
Usual story, Enabled the restricted ATI drivers and then after reboot I get a black screen.
Ctrl+Alt+F1 doesn't work. I'm pretty stuck, what to do?

System specs: AMD 64 athlon, 3800+, ATI Radeon X1900 512mb.

Please help, Thanks!

---

### Post by bwallum on 2008-01-14
When you say black screen, can you get past grub?

---

### Post by Swako on 2008-01-14
It loads, shows the ubuntu status bar and then just before its supposed to prompt for login it goes black. My screen is still active (i.e. it doesn't go to standby mode.)

---

### Post by Swako on 2008-01-15
Or is there at least a way I could disable the ATI driver before booting so I could just use my pc until I can sort this out?

---

### Post by bwallum on 2008-01-15
You need to get into rescue mode with just the command line prompt. If you watch when grub loads it should offer you a rescue mode.

When you get to the prompt you should be at root. Be careful here because you have the power of doing anything to your system without much in the way of further prompting.

You need to edit your xorg.conf file.

At the command line prompt type 

```
nano /etc/X11/xorg.conf
```

Note that the command is case sensitive and that X11 is not x11.

When in this simple editor scroll down until you find Section "Device"

Then look for the Driver entry. It will probably have your ATI driver shown. Change this to "vesa" Make sure any other graphics driver is changed to vesa (you might have a failsafe setting)

Then save the file with Ctrl X.

Reboot.

Good luck,
Bob

---

### Post by Swako on 2008-01-16
Got it back to Vesa by using: sudo dpkg-reconfigure xserver-xorg
But my ATI card still not working...

---

### Post by bwallum on 2008-01-16
ATI cards are still a bit tricky in Ubuntu. I use the 'radeon' driver in a second machine and it works most times.

I suggest you start a new thread at

[http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)

and say you have your card running but want to get the best out of it. I know there are some guys that have done just that but it is a black art to me. 

I have gone down the nVidia route for anything that requires intensive graphics and find it a better experience than ATI in Ubuntu.

Let me know how you get on, i would like to learn more about getting the best out of ATI cards.

Regards
Bob

---

### Post by drascus on 2008-01-16
There is always issues in my experience with ATI cards. I don't tend to enable them to avoid issues. you could try pressing going to the grub menu and disabling the splash screen so that you can see if there is any error messages during the boot process.

---

