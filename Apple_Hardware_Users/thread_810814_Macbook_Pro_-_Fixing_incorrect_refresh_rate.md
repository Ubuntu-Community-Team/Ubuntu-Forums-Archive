---
title: "Macbook Pro - Fixing incorrect refresh rate"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by _alex_ on 2008-05-28
Hey guys,

Since the wiki pages don't seem to mention it, I'm not sure whether it's a problem that's affecting only me: If you have a Macbook with an nvidia card, the driver misreports the refresh rate as 50Hz: meaning that compiz will run at a lower frame rate than your screen's 60Hz refresh rate.

First check what GNOME thinks your monitor's refresh rate is, by executing "gnome-display-properties" at the shell. If the refresh rate is not 60Hz (50Hz for me) for your native resolution, then there are two ways to fix it. The first is to disable refresh rate detection in compiz settings manager, and to specify it manually instead. I prefer the second method because it is a global fix rather than exclusive to compiz:

Edit /etc/X11/xorg.conf, and add the following line to the "Device" section for the nvidia driver:

```
Option "DynamicTwinView" "False" # fix refresh rate
```

Here's what mine looks like for my Macbook Pro 4,1:

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    Option "DynamicTwinView" "False" # fix refresh rate
EndSection

```

Log out, and log back in. Now check to make sure the refresh rate reported by "gnome-display-properties" is 60Hz for your native resolution. Compiz should now run noticeably smoother! As a bonus, you can prevent jagged window edges when moving windows by enabling "Sync To VBlank" in Advanced Desktop Effects > General Options > Display Settings Tab. Now your desktop experience should be just as smooth as OS X :)

Please do let me know if you're affected, and whether you think this should go into the wiki pages.

Thanks go to the following pages that identified the problem and fix:
[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/157623](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/157623)
[http://www.nvnews.net/vbulletin/showthread.php?t=96182&highlight=refresh+rate](http://www.nvnews.net/vbulletin/showthread.php?t=96182&highlight=refresh+rate)
[http://ubuntuforums.org/showthread.php?p=1557092](http://ubuntuforums.org/showthread.php?p=1557092)

---

### Post by stream303 on 2008-05-29
Whoa! thanks.  Although it's not an apple, that just fixed my 50hz problem on my HP box with an onboard GeForce 6150LE card.

pays to browse the mac-intel threads even if you don't own one!

---

### Post by cyberdork33 on 2008-05-29
> **stream303 said:**
> Whoa! thanks.  Although it's not an apple, that just fixed my 50hz problem on my HP box with an onboard GeForce 6150LE card.

pays to browse the mac-intel threads even if you don't own one!
This might just be a generic nVidia problem then. 

For the record, my iMac (w/ ATI X1600) did not exhibit this issue.

---

### Post by _alex_ on 2008-05-29
It is a generic nvidia problem; see the following for nvidia's explanation:
[http://www.nvnews.net/vbulletin/showpost.php?p=996326&postcount=37](http://www.nvnews.net/vbulletin/showpost.php?p=996326&postcount=37)

I think pretty much everyone with an nvidia card is currently affected. What's worse, is that it's not easy to track the fix down (I have been looking for it for several weeks!); and many people seem oblivious to the problem.

Perhaps the Macbook wiki pages are not the best place to put it, but it should definitely go somewhere where people can easily find it.

---

### Post by cyberdork33 on 2008-05-29
[Desktop Effects & Customization]("http://ubuntuforums.org/forumdisplay.php?f=330") might be the best place for it (or Maybe general help). I would recreate this thread to be less Mac-inclined in one of those forums and ask for a sticky.

---

