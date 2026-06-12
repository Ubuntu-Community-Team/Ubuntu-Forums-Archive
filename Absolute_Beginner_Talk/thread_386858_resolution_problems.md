---
title: "resolution problems"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Vandorius on 2007-03-17
Ok i just installed ubuntu for the third time. All just cozz i wanted to set my resolution to 1280x1024.

When i changed the resolution trough termminal it was fine. Ecept it was very slow even if changed back to 1024x1024 wich ran good before.

I have ATI Radeon 9600 and a fresh install now. Wuld anyone be kind enough to explane to a nob like me how do i change the resolution without messing with speed of graphic or anithing else...

And one more thing i noticed is that when ichanged the resolution my keyboard layout broke down

---

### Post by ajgreeny on 2007-03-17
Possibly the simplest way is to edit your /etc/X11/xorg.conf file by going to the section at the bottom where resolutions are listed and making sure the resolution you want is there.  For example mine looks like this, with the resolution you also want shown in bold:-

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes       ** "1280x1024"** "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

and the figures are repeated for each colour depth listed in the file (not actually needed in my case as I always use 24 bit colour, like most people.

Make sure you have the appropriate graphic driver also running (I use the open source ati driver without any problems and get 3D acceleration OK).  I have tried to get the fglrx driver to run but never managed it in dapper, though I did in breezy quite easily.  I don't actually need it as I'm not a gamer and the OS ati is great for me.

Good luck and I hope this helps.

---

