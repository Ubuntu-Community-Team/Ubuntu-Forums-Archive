---
title: "17&quot; PowerBook G4 Problems"
date: 2010-01-14
forum: Apple Hardware Users
---

### Post by #2! on 2010-01-14
I used a live CD burned onto a DVD-RW and it booted up and worked great. So I installed it using the entire hard drive, Ran Update manager, enabled the driver for the wifi card. Before I was using 10.5 with all recent updates done.
 
A few things don't work. It fails whenever I try to connect my Bluetooth mouse and keyboard, CD drive doesn't mount anything, I thought it would bring up the restricted nvidia driver but it doesn't so the video is slow and sketchy.

---

### Post by linuxopjemac on 2010-01-15
you can install "bluetooth manager" or "blueman" for your Bluetooth device. The CD drive is a known bug (see this [thread]("http://ubuntuforums.org/showthread.php?t=1323153"). There are no nvidia drivers for PPC. you have to live with the nouveau driver. What is your exact Mac Model or even better, what model nvidia card do you have ?

---

### Post by linuxopjemac on 2010-01-15
I checked, the only 17'' PowerBook G4 with nVidia card was the 17'' introduced in January 2003. 
Screen: 17" active matrix TFT
Monitor: 24 bit 1440x900
GPU: NVIDIA GeForce4 440 Go 4x AGP

try this in Xorg.conf:

```
Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:0:16:0"
    Driver          "nouveau"
EndSection
```

The BusID is probably not correct, you will have to find it yourself with
```
lspci | grep VGA
```

output for example:
```

01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4
MX 4000 AGP 8x] (rev c1)
```

where 01:00.0 is the BusID, which would translate into:
PCI:1:0:0

another way is to
```
Xorg -scanpci

```

Instead of the "nouveau" driver, you might also want to try the "nv" driver, don't know if that makes a difference.

---

### Post by linuxopjemac on 2010-01-15
to find the corrsponding modelines for your monitor, you should read this:
[http://mac.linux.be/content/black-screen-or-missing-gui](http://mac.linux.be/content/black-screen-or-missing-gui)

and read the part about fbset

---

### Post by linuxopjemac on 2010-01-15
if you find a working Xorg.conf, please post it here.

---

### Post by linuxopjemac on 2010-01-15
here you find a working xorg.conf for a powerbook g4 with ati. I would just copy and paste the monitor section from there and change ati into "Configured Video Device"

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       60-60
        VertRefresh     43-117
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection


```

---

### Post by linuxopjemac on 2010-01-15
This would then add up to the following Xorg.conf file:
```

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:0:16:0"
    Driver          "nouveau"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       60-60
        VertRefresh     43-117
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection
```

The modelines may be wrong...see post above

---

### Post by linuxopjemac on 2010-01-15
This would then add up to the following Xorg.conf file:
```

Section "Device"
    Identifier    "Configured Video Device"
    BusID        "PCI:0:16:0"
    Driver          "nouveau"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       60-60
        VertRefresh     43-117
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection
```

The refresh rates of your monitor might be wrong, see post above

---

