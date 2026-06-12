---
title: "how to change screen resolution"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by suresh_ktnv on 2006-11-09
Hi,
  Just now I have received Free CDs of Ubuntu6.06.I am sucessfulyy installed the ubuntu. But I couldn't change the screen resolution. So that I am unable to view the full screen.
In "Propeties" it will fixed to 800x600. It will not change. Can anybody help me?

---

### Post by localuser on 2006-11-09
Do you happen to know what graphics card you have installed?

---

### Post by 3rdalbum on 2006-11-09
Time for you to earn your command-line stripes. Do the following:

```

sudo nano /etc/X11/xorg.conf

```
That's a capital X in X11, and a lower-case one in xorg.conf.

Press Page Down until you see something like the following:

```
Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
        Monitor    "COMPAQ 7540"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

```

Etc, etc, etc. Yours will read a little differently, I'm sure. You notice how mine has larger resolutions listed for each Depth? You've got to change your xorg.conf to include those higher resolutions, in every SubSection "Display" listed in your file under Section "Screen".

Now press Control-X to tell Nano to quit, then press Y to confirm that you want to save the file, then press Return to actually save it. When you reboot, you should have access to higher resolutions.

---

### Post by figo2476 on 2006-11-30
Previously, the driver for my ATI card is vesa. Then I change it ATI. After reboot, all the icons become huge.

I have a look at the xorg.conf. I found that:
 
Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
  Monitor "Generic Monitor"
  DefaultDepth	24 
  SubSection "Display"
    depth 24 
    virtual 640 480
    modes "640x480@60"
  EndSubSection
EndSection

It misses some lines. How could I fix this, since I don't have the original xorg.conf in this situation.

---

