---
title: "Can I enter a terminal or commandline from the grub screen and use it to fix"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-01-26
The "Input Not Supported" problem I have. Is their a file I can edit or something like that?

Thanks

---

### Post by taurus on 2008-01-26
Press e at the GRUB menu and edit the entry for your kernel.  You probably have included a video mode that is not supported.

Otherwise, boot into recovery mode from GRUB menu and edit /boot/grub/menu.lst if that is where the problem is.

```
nano -Bw /boot/grub/menu.lst
```
You can save the changes with <Ctrl>o and exit with <Ctrl>x.  

Then, reboot with

```
shutdown -r now
```

---

### Post by rpkehoe on 2008-01-26
You can edit /boot/grub/menu.lst  You can also edit the commands grub is using at boot time, but follow the options at the bottom of the screen and press b when ready to boot.

What is the problem you are having in grub?

---

### Post by psam3 on 2008-01-26
> **rpkehoe said:**
> You can edit /boot/grub/menu.lst  You can also edit the commands grub is using at boot time, but follow the options at the bottom of the screen and press b when ready to boot.

What is the problem you are having in grub?

Once I get past the grub screen it goes directly to a black screen with the Input not Supported box. Can I simply just change the resolution without booting Ubuntu?

---

### Post by taurus on 2008-01-26
In that case, boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by psam3 on 2008-01-26
> **taurus said:**
> In that case, boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

Booting into recovery mode gives me the same thing?

---

### Post by taurus on 2008-01-26
You get the same error message, Input not Supported, while booting into recovery mode from GRUB menu?  Are you sure you did pick the recovery mode?

---

### Post by rpkehoe on 2008-01-26
If you cannot get it into recovery mode, just let it sit when it comes to Input not supported, give it enough time to get to login screen (my makes the ubuntu drum beat) and press ctrl+alt+F1 and log into the system.  The follow the dpkg instructions from taurus.

---

