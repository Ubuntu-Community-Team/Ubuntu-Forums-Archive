---
title: "toshiba U205-S5057 lost 1280 800 after LCD pannel change"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jsr on 2007-07-24
hello,
I lost my existing 1280 800 resolution after an LCD replace from Toshiba, (I had to change because the LCD display was gone (Red line on the display)

Now this is the strangest problem that I have seen, I cant get to 1280x800, even If i change the resolution, the display is panning out side the screen.
Tried this too [http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647) but no clue!

I just cant think what could be wrong? did they put in a different LCD panel? I just cant understand.. 

$lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

need your help! to get this fixed. I hate 1024 780 on a wide screen :(

---

### Post by Al3xK3aton on 2007-07-24
Have you tried reinstalling the drivers? I'm certain it's a driver problem.

---

### Post by jsr on 2007-07-24
> **Al3xK3aton said:**
> Have you tried reinstalling the drivers? I'm certain it's a driver problem.

yeah looks like it is not serious problem, but which driver are you referring to? 
I just tried to boot from the Ubuntu CD and guess what the res is 1024 780 and not 1280 800, wonder what has this to do with the LCD pannel :confused: 
I always had an impression that it is the display card issue, but the display card is just the same... 

any clues?

---

### Post by whorton on 2007-07-24
When the replace the LCD panel they may have used a different brand panel.  I would try reinstalling the display drivers on it. When you do that it should be able to pickup the correct resolution for the new panel in your notebook.

---

### Post by jsr on 2007-07-24
> **whorton said:**
> When the replace the LCD panel they may have used a different brand panel.  I would try reinstalling the display drivers on it. When you do that it should be able to pickup the correct resolution for the new panel in your notebook.

hmm.. well the display drivers is xserver-xorg-video-i810, I did try to remove and reinstall, I knew it would not work, but tried it.. didn't work.

I have both edgy and fiesty installed, on edgy when i select 1280x800 what happens is my screen is larger than the monitor and it pans

this is my xorg.conf

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection

lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

does that help in figuring out what is going on? 

thanks

---

### Post by jsr on 2007-07-25
well, it did not work with Edgy :( 
but got the resolution back to 1280x800 on FC 7, I think I will stick with that until the next release of ubuntu. hope it gets fixed, needed a completely working GNU/Linux thats all.. will wait for the next release. 
Or may be if some one has a better idea

BTW the FC 7 xorg.conf shows a different driver.. intel? is that a different one?

Section "Device"
        Identifier  "Videocard0"
        Driver      "intel"
EndSection

adios
--
jsr

---

