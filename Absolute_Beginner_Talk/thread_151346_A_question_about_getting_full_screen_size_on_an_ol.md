---
title: "A question about getting full screen size on an old monitor."
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by holomate on 2006-03-27
One of my problems with getting into other operating systems has always been that I don't have enough monitors. Strangely I can get older, decent working computers on the cheap, but screens never come down in price and so my computers actually outnumber what I have to view them with.

Anyway, in order to play with Ubuntu Breezy, I grabbed my zaniest monitor to use with it. What this is is a Relisys RE2058... basically a 21" professional CAD monitor from 1995. At 21" it's pretty big, but it's also pretty limited and doesn't support too many resolutions or frequencies. It's not supported natively by Windows 9x drivers or by anything in linux.

My question is two-parts, which are somewhat related. First, how am I able to set custom monitor values to run under X? I know these settings are stored somewhere, as I've seen them on FreeBSD's wizard installation. But I've been unable to find a command or config file to do this in Ubuntu (which prettymuch shows how newbieish I am).

Second part is a bit stranger. A long time ago, in Windows98, I had a software application that would create a custom driver for Windows using the monitor values (I *think* it was called PowerBar, but that's unimportant right now). Anyway, I was also fiddling with it to get the maximum screen size under DOS. As a result, I've actually got the image looking a little wonky when in a DOS mode or a linux command line or POST text display. The image appears "curved" and squished together near the horizontal edges. I assume it's stayed like this because the monitor has a "memory" or something. If anyone is aware of how to clear this and get it back to normal. Please let me know.

On a related note, I'd *love* to be able to use full horizontal and vertical space of the monitor (running right now, I lose about 2 inches horizontally), so if someone knows how to setup Ubuntu or my hardware so that I'm always using the full display area... that would be great.

Thanks in advance, I know these questions are probably a bit strange, but hopefully if someone solves this for me, google will remember it for others. :)

---

### Post by davidmoore83 on 2006-03-27
/etc/X11/xorg.conf

off the top of my head though i know i prob got it wrong and someone will correct me! hey let me off its 2am here :)

---

### Post by IYY on 2006-03-27
Yes, /etc/X11/xorg.conf is the file you'll need to edit. Make sure you're editing it as superuser (sudo nano /etc/X11/xorg.conf).

---

### Post by avelldiroll on 2006-03-27
You will have to edit /etc/X11/xorg.conf
But first make a backup copy :
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_`date +%F_%R`
```

Then edit the xorg.conf file as suggested by davidmoore83 and IYY :
```
sudo nano /etc/X11/xorg.conf
```

The first interesting part is here :
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection
```

And should be set this way (using the correct specs for your monitor) :
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-75
        VertRefresh     50-85
EndSection
```

The other part of interest is here :
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Name of your Graphic Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
  .....................................................
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
You can set the different modes you need here (notice that the one used by default will be the first Mode listed in the 24 depth display subsection, 1600x1200 in exemple above).

For your 2nd question, I won't be of much help because I never saw a  Relisys branded monitor. However it's quite common to find a "hardware" way to restore factory settings (for exemple :  contrast and brightness buttons + voodoo black magic).

---

