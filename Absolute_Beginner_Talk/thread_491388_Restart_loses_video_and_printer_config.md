---
title: "Restart loses video and printer config"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2007-07-03
Restart loses configuration for video / printer

When I shutdown Ubuntu on my dual boot p3. then restart, there are two problems and they are repeatable.

1) The video resets to 640 x 480 with no option for higher resolution. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` will bring it back. But why do I need to do this every time? Something is getting bonked. 

2) The printer stops working. A test page will show up in Printers as printing and the printer is Ready, but nothing prints. The printer is on a Windows computer and I always have a difficult time getting it to work again. New Printer / Network Printer / Windows Printer (SMB), but then what do I put in Host / Printer?

In a quite possibly related problem, it takes it a looong time to boot, like 4 minutes.

Any help appreciated, these problems are becoming showstoppers.

---

### Post by edwardLS on 2007-07-03
With respect to the video settings on your resolution being lost:
I had a similar problem at one time.  My problem was in the /etc/X11/xorg.conf file.
Check in that file and see if you can find the setting of the resolution you want.  If you can't find the resolution you want, you may have to edit that file, and add the settings.
That is what I had to do, and that solved the lost resolution on restart problem I was having.

---

### Post by Raineer on 2007-07-03
He's referring to this:
> Section "Screen"
  Identifier "Default Screen"
  Device "nVidia Corporation G71 [GeForce 7900 GS]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR] 
    depth 16
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR]
    depth 8    
    virtual 1600 1200
    modes [COLOR="Red"]"1024x768@60" "1152x864@75" "1024x768@70" "1280x1024@75"[/COLOR]
  EndSubSection
EndSection 

Make sure each of those depths show the resolution you wish to run.
This can be edited by
```
sudo nano /etc/X11/xorg.conf
```

Make a backup first!!!!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.mybackup
```

---

### Post by bobmorris on 2007-07-03
Those resolutions are in the file now, but are not there after I shutdown and restart. Something bonks them upon rebooting apparently. Weird...

---

### Post by Raineer on 2007-07-03
> **bobmorris said:**
> Those resolutions are in the file now, but are not there after I shutdown and restart. Something bonks them upon rebooting apparently. Weird...

Wow... Well I've actually had this happen on my own installation before and didn't know what made it go away. Anyone else have ideas?

---

