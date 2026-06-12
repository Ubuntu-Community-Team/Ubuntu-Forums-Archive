---
title: "Ack! xorg.conf/opengl problem, beryl related (possibly)"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by clantoncs on 2007-01-11
I'm still quite new at ubuntu, so go easy on me since I'm sure this problem is easy to fix! 

I made a pledge never to go back to windows, and I plan on keeping it!  Everything was going great for a couple of months until I tried to install beryl.  I think my problem is that I installed the non-beta nvidia drivers when I first started.  I had had a couple of problems getting nvidia installed in the first place (living in China and having a slow-*** net connection), so the beta seemed a bit frightening after my initial struggles. 

So I installed the supported nvidia (non-beta) drivers and tried to install beryl via the instructions on ubuntuguide [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29").

Luckily i backed up my xorg.conf file as per the instructions, and of course beryl-manager would not run.  It would just restart my GDM.  But here's the rub:  now my GDM will restart anytime ANY opengl action runs-- including my screensaver! 

I was pretty definite that the problem was with my xorg.conf file, so I reverted back to my original xorg.conf file via
```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

but my GDM still restarts anytime an opengl operation runs. Screensavers are a great test for this.

I'm using edgy and here is my xorg.conf file:

```
Section "Monitor"
    Identifier     "LXH-WG769F"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "LXH-WG769F"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Am I missing something obvious (probably)?

thanks for the help.

chris

-ps on a side note, the support I've gotten at this website has been excellent.  I always get a straight answer even when the questions I ask are a mile past retarded.  Thanks everyone for helping us newbies along as we learn a new operating system.  It's easy for linux folk to be patronizing towards others who haven't caught on to everything yet, but I find everyone here to be most helpful and really acting towards making linux the OS of the future without treating us like we're just obstacles.

--pps when I say GDM, I mean the Gnome desktop manager. Is this the right acronym or am I confused?  I just noticed that the ubuntuguide refers to this as "X" (as in "restart X with ctrl-alt-backspace")

---

