---
title: "beryl and xfce"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by dhalgren on 2006-10-29
HI,
I have installed ubuntu and then added xfce to the installation. Upgraded to edgy without any trouble ( :p ) nd have beryl running without any trouble in gnome.

But i want to run beryl in xfce.  When i run the beryl-manager I get the following message 

> 
beryl: Another window manager is already running on screen: 0
beryl: No manageable screens found on display :0.0

As i do not have a clue what this means in terms of how to fix it (if it is possible to fix it) is there anyone out there who can help me please??

---

### Post by dhalgren on 2006-10-29
well, it took a lot of time reading everything I could find....
the answer for me was to remove xfwm, so that xfce ran using gdm.

now i have beryl in xfce, and it is faster than gnome, despite everything.

I assume that the same thing would have to be done to run beryl on a box using only xfce.

---

### Post by crimesaucer on 2006-10-29
**Where is the xfwm located?**

Hello, I tried to install beryl to my xubuntu 3/4 days ago and I think my intel media accelerator 900 wasn't enough of a graphics card to work with beryl. I had the xfce4-sessions in gdm set to use beryl like the tutorials in ubuntu and beryl said to, and it was so slow and would ruin my xine video playback when I went into full screen. Besides that the scroll was really slow and all static and herky-jerky.

Then I removed the beryl it ruined my system. I think a chmod 755 xgl.usr start command that I used from the beryl wiki forum destroyed my 6.10 edgy with a setting that wouldn't let the gnome or xfce or xfwm work properly, so I had to reinstall.

Anyway, I'm trying to use a gtk+2 theme from the xfce-looks page: [http://www.xfce-look.org/content/show.php?content=46153](http://www.xfce-look.org/content/show.php?content=46153)

and I am trying to find the xfwm to add a command to direct it to my new .themes folders, and since I'm new, I can't find the xfwm-theme-manager.

You just said you removed it and fixed your gdm, so you seem to know hat you're doing, can you tell me how and where the xfwm is located?

Thanks,
-c.

---

