---
title: "iMac g3 with Rage 128 gives frame buffer error"
date: 2009-03-14
forum: Apple Hardware Users
---

### Post by nkayhan on 2009-03-14
Hi all.  I've been trying to install a spartan Openbox system on an old iMac G3.  I've installed a base command line system, and can log in fine.  Upon installing x.org however, I began to run into problems.  Here are the errors I got:
```

(EE) Unable to find a valid framebuffer device
(EE) R128(0): Failed to open framebuffer device,  consult warnings and/or errors above for possible reasons
(EE) Screen(s) found, but none have a usable configuration

```
And here is my xorg.conf:
```

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync     58-62
    VertRefresh   75-117
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth  24
    SubSection
        Depth     24
        modes     "1024x768" "800x600"
    EndSubSection
EndSection

Section "Module"
    Disable "glx"
    Disable "dri"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver "r128"
EndSection

```

Thanks guys,
NK

---

### Post by nkayhan on 2009-03-15
Please guys, I told a friend I would get this system up soon, and I already formated the drive, so I don't want to be stuck with a text only setup.  Thanks!

---

### Post by tiresia on 2009-03-15
I don't have an iMac G3, but from what I remember, I would try with "DefaultDepth 16"
You may find these threads interesting:
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)
[http://ubuntuforums.org/showthread.php?t=1058232](http://ubuntuforums.org/showthread.php?t=1058232)

Are you trying to install Intrepid or Hardy?

---

### Post by nkayhan on 2009-03-15
Thanks for the reply.  Unfortunately, even after changing the color depth to 16 bits I get the same errors.  I am trying to install Intrepid simply for the up to date packages.  And believe me I've poured over those two threads.  Is it necessary to have frame buffering or can I turn it off as that seems to be the base of the problem?

---

### Post by tiresia on 2009-03-15
I find, that for so old Hardware is a good idea to install an old version of Ubuntu (even better Debian). I used often Debian Etch (4). Even after such Installation X may not work, but at least you get a starting point to work.
After getting a woking X, you can backup your xorg.conf and use it in other newer version of X

---

### Post by nkayhan on 2009-03-15
Great advice, I'll try Etch today.

---

### Post by tiresia on 2009-03-16
You may find also this thread interesting
[http://forums.debian.net/viewtopic.php?t=37098](http://forums.debian.net/viewtopic.php?t=37098)

---

### Post by roym4 on 2009-03-17
I was working on a G4 Cube today and after installing Hardy I got the same "Failed to open framebuffer device" errors that you encountered.

I made changes to the xorg.conf that are discussed in [http://ubuntuforums.org/showthread.php?t=772808](http://ubuntuforums.org/showthread.php?t=772808) (Thanks avtolle) and when I rebooted it went straight to a log-in screen. This thread also references another iMac thread [http://ubuntuforums.org/archive/index.php/t-770033.html](http://ubuntuforums.org/archive/index.php/t-770033.html) that is specific for G3 iMac. 

I would think that, since you're working on an iMac, if you kept your xorg.conf Monitor section HorizSync 58-62 and VertRefresh 75-117 iMac settings and made the other specified changes you may have some success.

---

### Post by narcisgarcia on 2011-11-25
With an iMac G3 350 (ATI), all the examples of xorg.conf worked for me when I added the following line in the "Device" section:
```
Option "NoInt10" "true"
```
(Ubuntu 11.04)

---

### Post by rsavage on 2011-11-25
narcisgarcia, I'd be interested in seeing your full xorg.conf file if you are using ubuntu 11.04.  Can you post it please?

---

### Post by overdrank on 2011-11-25
Please start a new thread with your issues. Back to sleep thread. :)

---

