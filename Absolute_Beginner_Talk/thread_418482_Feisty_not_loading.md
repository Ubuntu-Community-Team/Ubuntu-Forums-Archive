---
title: "Feisty not loading"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-04-22
I attempted to install my ATI driver manually using the instructions given here: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

After rebooting, it goes through the boot process completely but all I get is a blank screen. I have no idea what to do, any help would be appreciated.

---

### Post by taurus on 2007-04-22
Did you backup /etc/X11/xorg.conf before you installed that ATI driver?  If you do, you can just copy the old one, working one, back and you should be back where you were before the ATI.  Otherwise, reboot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

### Post by hrolfp on 2007-04-22
> **taurus said:**
> Did you backup /etc/X11/xorg.conf before you installed that ATI driver?  If you do, you can just copy the old one, working one, back and you should be back where you were before the ATI.  Otherwise, reboot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

I think I backed it up. How do I copy the old one back?

---

### Post by taurus on 2007-04-22
```
cd /etc/X11
sudo cp oldfile xorg.conf
```
Then, reboot.

---

