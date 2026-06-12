---
title: "Screensaver not working."
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by boudreaujr on 2007-03-30
After my load of ubuntu 6.1 on my desktop workstation the setup only allowed me to use a resolution of 1024x768.  I needed at least 1280x1024 so I changed my xorg.conf file.  Since the changes I now have my 1280x1024 resolution which I wanted but none of the screen savers work any more, just a blank screen.   No errors that I can find in the /var/log/X11 logs.  Anyone with any ideas?  Below is my updated conf file.

Section "Monitor"
        Identifier      "Viewsonic E90f"
        Option          "DPMS"
        HorizSync       30-86
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43GL [Quadro FX 540]"
        Monitor         "Viewsonic E90f"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Thanks,
Denis

---

### Post by Zuuswa on 2007-03-30
well, some screensavers use Opengl acceleration, so do you have 3d acceleration working on your video card?

---

### Post by boudreaujr on 2007-03-30
I honestly don't know.  But things worked when I was running the system on 1024x768 with the default xorg.conf file.  How could I test for correct opengl?

Denis

---

### Post by Michl on 2007-03-30
I have the same problem on two different computers running Edgy.
On both you can preview the screensaver and all that, but usually
they do not come on after the idle time.  Instead the screen goes
dark.  I say usually, because occasionally, the screensaver does
come on instead of the dark screen, but I can't find a pattern.

Both monitors are Viewsonics, one 510 and the other 710, so
one is at 1080x768 and the other at the higher resolution.
Also none of the screensavers (except blank screen, of course)
work, gl ones or simple.

Michael

---

### Post by Zuuswa on 2007-03-30
to see if you have direct rendering, use the command

```
glxinfo
```

into a console and there should be a line Direct Rendering: Yes

---

### Post by boudreaujr on 2007-03-30
Zuuswa:  Thanks for the tip to at least check into the opengl.  I will have to check into it on Monday as my ubuntu desktop is at work.

Michl:  I can preview the screensaver as well but it never comes up.  Just blank screen, which in itself isn't a big problem but I like the linux screensavers.  People that come into my office and see the Linux screensavers, are always impressed.  

Denis

---

### Post by imasickboy on 2007-03-30
Add the following to the bottom of your xorg.conf, save and restart X.

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection

---

### Post by Michl on 2007-03-30
> **imasickboy said:**
> Add the following to the bottom of your xorg.conf, save and restart X.

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection



What does that do?  

By the way, I have Direct Rendering:  No.

However, I have this problem with all screensavers.  And as I said, occasionally
some of them work.

Also, running Feisty live on one of the computers and the screensaver
comes on perfectly. 

Michael

---

### Post by boudreaujr on 2007-04-02
glxinfo reported the following.

denis@drb-desktop:/etc/X11$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:


Direct Rendering: No  <-- Does this mean that I don't have a proper NVidia driver installed for my Quatro FX 540 graphics card?  If the answer is yes, I would love a pointer to the correct graphics driver to install.  I have been confused as to which driver I should be hunting down for my FX540.

Thanks,
Denis

---

### Post by boudreaujr on 2007-04-03
All fixed.  Installed nvidia drivers and edited xorg.conf file to specify nvidia driver and restarted X.  Still learning all this.

Denis

---

### Post by bcrom on 2007-04-03
I just had the same problem with screensavers for the last couple months.  Surpisingly going into screensaver settings, disabling, exiting, then reenabling fixed it for me.

---

### Post by jpongin on 2007-06-24
> **boudreaujr said:**
> All fixed.  Installed nvidia drivers and edited xorg.conf file to specify nvidia driver and restarted X.  Still learning all this.

Denis

I've been having this problem since Dapper Drake (6.06), and I have the exact same card.  Can you please point me to the right direction to do a clean Nvidia driver install for this card?

I've since upgraded to Feisty Fawn (7.04).

Your help is greatly appreciated.

Also, on a side note, have you had any issues with slow remote desktop?  I'm using RealVNC on my windows box to remote into my Ubuntu box.

Thanks man.

========================================

UPDATE:

I've since fixed the problem.  After my upgrade to Feisty was complete, I enabled the new Nvidia drivers, and everything is well.

As for the remote desktop performance, that also improved with Fiesty.  Performance also improved when using a blank background, and not a photo.  Thanks in advance.

---

