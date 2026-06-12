---
title: "Mac mini + Ubuntu + 22&quot; display = ?"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by nerubz on 2008-12-02
Hello,

My question is pretty straightforward - I have mac mini (graphics are GMA 950) currently running Winxp. I have installed Ubuntu normally like any other program, everything runned just fine, except that I couldn't set any higher resolution than 1300x1024 or something like that. Under windows I'm using 1680x1050, why I can't under Ubuntu? That res just isn't in the menu...

Thanks!

---

### Post by Snufkin UK on 2008-12-08
Also having the same problem, anyone have any idea?

---

### Post by stream303 on 2008-12-08
Which version of Ubuntu?

At any rate, the following might help you get started by manually editing your **/etc/X11/xorg.conf** as root.

With Intrepid 8.10 / Debian Lenny-Testing, this is what I used to get up and running on my 22" Viewsonic on an Intel box.

Find out your displays horizontal and vertical frequency rates and CHANGE them from what is shown here:

AND, change your video driver if you aren't using the nv driver for nvidia. (ie, ati, radeon, etc) Note that this is a simplified xorg.conf based on the open 2D drivers.

Update:  in your case, it looks like "i810" might be the one to use, however you may have to use 915 resolution.  See this older thread for some additional tips:

[http://ubuntuforums.org/showthread.php?t=160521](http://ubuntuforums.org/showthread.php?t=160521)

Not sure if you'll have that situation today.

```
Section "Monitor"
  Identifier  "Configured Monitor"
  HorizSync    30-82
  VertRefresh  50-85
EndSection

Section "Screen"
   Identifier "Default Screen"
   Monitor    "Configured Monitor"
   Device     "Configured Video Device"
   DefaultDepth   24
     SubSection   "Display"
       Depth     24
       Modes     "1680x1050"
     EndSubSection
EndSection

Section "Module"
EndSection

Section  "Device"
   Identifier   "Configured Video Device"
   Driver "nv"
EndSection

```

Be sure to change the horizontal, vertical freqs, along with the correct 2D driver.  At least this should help get you up and running if you want to use proprietary drivers later.

If nothing else, this should allow you to see more ranges available when you use the screen resolution utility.

Much of this isn't really Apple-specific, so be sure to check the normal hardware boards too.

---

