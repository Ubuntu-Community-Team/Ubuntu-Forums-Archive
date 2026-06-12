---
title: "screen resolution"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-08-16
I have an  ASUS F3 Series F3T-AP042C NoteBook AMD Turion 64 X2 TL-56(1.80GHz) 15.4" Wide XGA 1GB DDR2 667 120GB 5400rpm DVD Super Multi NVIDIA GeForce Go 7600 - Retail

I installed ubuntu but I cannot set the resolution any higher to 1024 by 768,  So next I ran the program envy and did the automatic install of the nvidia drivers, restarted but still cannot select a resolution higher than 1024 by 768.  I've read some posts about changing the xorg file but I also read that you can damage your monitor/lcd  panel.  Can someone help me or point me in the right direction to resolve this issue?

---

### Post by fickendichdu on 2007-08-16
```
sudo apt-get install 915resolution
```

Try running that from terminal you may need to restart X but that helped me.

---

### Post by vertex78 on 2007-08-16
I tried that and here is what it said:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 106 not upgraded.
Need to get 14.4kB of archives.
After unpacking 127kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe 915resolution 0.5.2-10ubuntu1 [14.4kB]
Fetched 14.4kB in 0s (23.9kB/s) 
Selecting previously deselected package 915resolution.
(Reading database ... 94941 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-10ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.2-10ubuntu1) ...
Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.

---

### Post by fickendichdu on 2007-08-16
You might want to look at this thread then.  [http://ubuntuforums.org/showthread.php?t=502694]("http://ubuntuforums.org/showthread.php?t=502694")

---

### Post by alienexplorers on 2007-08-16
You might try running the following lines in your monitor section of xorg.conf....
> Section "Monitor"
    Identifier     "Monitor0"
    ModeLine       "1280x1024_65.00" 119.4 1280 1368 1504 1728 1024 1025 1028 1063 -hsync +vsync
    Option         "UseEdidFreqs" "FALSE"
    Option         "UseEDID" "FALSE"
    Option         "DPMS"
EndSection


---

### Post by Hobo Joe on 2007-08-16
Run nvidia settings:
```

sudo nvidia-settings

```

---

### Post by vertex78 on 2007-08-16
thanks, that did the trick!

---

