---
title: "Dapper resolution problem"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Unknowndeepness on 2006-05-05
I have read a number of threads about this, but non of them really helps me.
While trying to change resolution from 1024x786 to 1280x1024, i changed this in xorg.conf:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
        Option "MetaModes" "1280x1024"
EndSection
  [ More stuff ]
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

```

But in [Gnome] system > preferences > Screen Resolution, i can choose between 
1280x800, 1280x786, 1152x786, 1024x786, 800x600 and 640x480.
Still, i want 1028x1024 or higher.

Anyone know a solution to this?

---

### Post by aggiechemist on 2006-05-05
Have you restarted your x server? Either reboot or press ctrl+alt+bkspc and maybe it will behave differently.

---

### Post by GaFFy on 2006-05-05
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

HotTo install NVIDIA drivers

if you have done this already then try checking out Problem Section point 6

It worked for my Geforce 3 Ti 200

---

