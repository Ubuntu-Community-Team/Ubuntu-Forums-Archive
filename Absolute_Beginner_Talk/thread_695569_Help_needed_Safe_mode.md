---
title: "Help needed Safe mode"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by sunseeker888 on 2008-02-13
HI GUys

HOw do i boot in safe mode? I need to edit  because of the ati restrcited drivers, blank screen a,d <alt> <ctrl> f2 does not work, so i reboot, now in recovery mode. I need safe mode, how do i get safe mode



need to edit this
sudo gedit /etc/X11/xorg.conf



cheers

---

### Post by p_quarles on 2008-02-13
Display the boot menu by pressing the escape key directly after the BIOS finishes loading. You will then see the option for recovery mode.

You won't need "sudo" with this, and it's command line only, so you can't use Gedit. Try this instead:
```
nano /etc/X11/xorg.conf
```
Be careful when editing that file, though. Make sure you have good instructions, and follow them exactly. Getting something wrong there can make matters worse.

---

