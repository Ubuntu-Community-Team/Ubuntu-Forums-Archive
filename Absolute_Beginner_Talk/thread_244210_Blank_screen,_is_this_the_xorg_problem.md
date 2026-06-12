---
title: "Blank screen, is this the xorg problem"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-08-26
I keep seeing references to the "xorg" problem but cant find out what it is exactly but I ve a feeling its to do with monitors? S might be related to my prob.

Anyway I installed dapper, but it wouldn't give me the option of a 1200 x 800 resolution, someone suggested using this command:
> 
sudo dpkg-reconfigure -phigh xserver-xorg

I selected the 1200 X 800 res from the menu and rebooted

now when ubuntu starts I end up with my monitor looking like its switched off.

This means I cant start ubuntu!

I have the option of starting in recovery mode but dont know what to do from the command line.

my system is:
acer aspire laptop
ATI x700 radeon 128mb
amd turion 64.

Also i intalled the fglrx driver before trying to change resoulutions.

Can any one help me?

thanks in advance!

---

### Post by bullgr on 2006-08-26
if the problem is in the xorg why you don't use the solution in the sticky post for the xorg problem?

go there [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)
and do the step-by-step solution...

if nothing change then it's not the known xorg problem

---

### Post by Paul133 on 2006-08-26
The "xorg" problem is the fact (bug?) that when the x.org x.server (or something like that) was updated to 10.3, it crashed and you essentially lost your GUI and were stuck at the commandline. It was fixed witht the 10.4 update, although at the time people were told to downgrade to 10.2. Your problem seems to be a resolution problem. I can't help you as I have no idea what the command does. Sorry, but at least you know it's not the xorg problem!

---

### Post by Tomosaur on 2006-08-26
Enter the recovery mode, login, and type:
```

sudo dpkg-reconfigure -phigh xserver-core

```

Next, type:
```

sudo nano /etx/X11/xorg.conf

```

Scroll down to where you see the various resolutions available, it will look similar to this (here's mine):
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "RM170"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Change 'DefaultDepth' to its highest possible value (ie, in my case, 24), then add your desired resolution to the subsection with your chosen depth, but PUT IT IN THE CORRECT ORDER. Do not just tack it on at the end or beginning of the resolutions. X will cycle through the resolutions until one works. Once you're ready, save the file and reboot into normal Ubuntu. Hopefully, X will start with your resolution (don't worry if the USplash is in a low resolution - this isn't X and so isn't affected by your X changes). If your chosen resolution wasn't first in the list, it's likely that you need to set it manually - in which case go to System > Preferences > Screen Resolution.

If after all this your resolution won't work properly, it may be the case that the resolution you're used to is just incompatible with your hardware and Ubuntu.

However, this little guide is not a definitive fix. Your device drivers may need upgrading, or anything really. Check all your drivers and kernel support (for example, the kernel needs to be compiled with nvidia support for nvidia cards to work properly) are up to date etc.

---

### Post by bplus on 2006-08-26
Hey thanks for that. I'll try what you suggested.

Breezy badger worked fine with the res I want so hopefully it should be ok.

---

### Post by bplus on 2006-08-26
Hey thanks for help folks.
To anyone ones who is interested here how to fix the problem:
I changed the driver bit in the xorg.conf file from "ati" to "fglrx"

---

