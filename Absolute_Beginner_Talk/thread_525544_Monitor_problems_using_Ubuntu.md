---
title: "Monitor problems using Ubuntu"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by J_Leno on 2007-08-14
The word problem is not the most accurate in this case but here's my problem.

I'm using Samsung SyncMaster 755 DFX (17'' CRT) and i know and have used it till now on 1152x864 on 85 Hz but my Ubuntu doesn't give me other options than 61-62 Hz.

Where can i seek for other drivers (maybe) or a way to set it up manually because i don't like the flickering of my monitor.

Thank you in advance.

---

### Post by w4ett on 2007-08-14
You will have to reconfigure your xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

Your monitor section should look something like this:

> Section "Monitor"
        Identifier      "Samsung SyncMaster 755 DFX "
        Option          "DPMS"
        HorizSync       30-85
        VertRefresh    50-160
EndSection


I got your monitor specs from:

[http://monitory.eactive.pl/monitor,Samsung,SyncMaster%20755DFX](http://monitory.eactive.pl/monitor,Samsung,SyncMaster%20755DFX)

---

### Post by Hospadar on 2007-08-14
What you'll want to do I think, is in a terminal run ```
sudo dpkg-reconfigure xserver-xorg
```This is a script to monkey with your xserver configurations, you will  be able to just skip through most of it, but there is one screen in there that let's you select the refresh rates.

---

