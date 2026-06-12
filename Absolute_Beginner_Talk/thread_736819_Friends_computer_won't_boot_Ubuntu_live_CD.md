---
title: "Friends computer won't boot Ubuntu live CD"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2008-03-27
I'm trying to boot to the Live CD so I can hook my external HDD up to it and get his movies off his harddrive.  His Windows installation is basically dead and we're gonna format it soon.  The problem is that it never reaches GDM.  It goes to the flashing cursor, then the cursor disappears and it just sits there.  If I press ctrl-alt-bckspc, it appears to kill an X server but even when X restarts it does no good.  This is with the auto-detected video drivers and VESA drivers.  Also, I can access the command line, so I know the CD is booting.

Any ideas?

---

### Post by kesman on 2008-03-27
Try safe graphics mode, and if it fails, try with Knoppix LiveCD, it's famous of its hardware-detection.

---

### Post by TheOrangePeanut on 2008-03-27
I tried safe graphics mode and it did the same thing.  I also tried the latest Knoppix and, once again, same thing.

Specs of the computer:

1.5ghz P4
768MB Ram
Nvidia 5200 video card

---

### Post by kesman on 2008-03-27
What happens if you run in terminal
```

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

```
?

---

### Post by oedha on 2008-03-27
what if you edit the booting line  ( press F6 on boot menu )
remove quiet splash
if still failed
edit again...add all_generic_ide
and also make sure your BIOS setup is default....especially for power management.....

---

