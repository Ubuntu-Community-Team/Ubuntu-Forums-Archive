---
title: "lost gui and cant restore to open drivers"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ironcladlad on 2007-02-05
Hello
I recently tried using the "envy" script for the nvidia drivers so that I had full hardware excelleration. My card is an Nvidia GeForce440 mx, but after I ran that i lost everything i tried the ```
sudo dpkg-reconfigure xserver-xorg
``` and ```
sudo dpkg-reconfigure xserver-xorg -phigh
``` to try and get back to the nv open driver but it didnt work. I have also tried ```
sudo nvidia-xconfig
``` to try to get the nvidia driver to work. 

So right now I just want my gui back.. really dont want to lose everything in a reinstall..
have about 30 gigs of music on the drive..
not to mention all my programs..

any suggestions?

---

### Post by Mba7eth on 2007-02-05
I had once the same problem .... Nvidia has missed everything :( or better to say i just didn't follow the guide 100% . 
before jumping to my solution can you please post this command 
```

$ls /etc/X11/
```

---

### Post by ironcladlad on 2007-02-05
sorry..i am really new to this.. how would i go about doing that?

---

### Post by ironcladlad on 2007-02-06
bump.

---

### Post by ^rooker on 2007-02-06
type "ls /etc/X11", at the commandline you get when you open a new terminal (Somewhere in "Applications/Utlities")

Something else I could suggest is to edit /etc/X11/xorg.conf and look for the block loading the display driver. Here's copy of my file:

> Section "Device"
        Identifier      "S3 Inc. 86C270-294 Savage/IX-MV"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "BusType" "PCI"
        Option          "DmaMode" "None"
EndSection

The line ```
Driver "savage"
``` tells X to use the savage driver for my device. Changing this to ```
Driver "vesa"
``` usually allows to get the graphical back again.

---

