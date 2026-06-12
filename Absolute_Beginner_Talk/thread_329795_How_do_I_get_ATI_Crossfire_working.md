---
title: "How do I get ATI Crossfire working?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-01-02
I have 2 ATI cards ready for crossfire (1800) only have 1 in right now though Can someone tell me how to do this, or point me to a wiki that might give me some help?  I just tried to put the other one in, but Linux wouldnt start up past the load screen, thanks! ;)

Edit: Just researched a little and found out that crossfire isnt up and running yet, guess Ill just have to wait like everyone else :P Its odd though, Run an ATI x1800 and an AMD X2 4200+ and I run low graphic games at about 2 FPS. Anyone else have this problem? Its getting frustrating.

---

### Post by bikeboy on 2007-01-02
Do you have fglrx installed? If not, you may not be getting hardware acceleration.

```
glxinfo | grep rendering
```

Should show direct rendering.

---

### Post by Daergeth on 2007-01-02
I do have it installed, but direct rendering isnt on! How would I go about fixing that?

It says:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No

---

### Post by bikeboy on 2007-01-02
Ok, I haven't used ATI cards for a while so I don't know whether fglrx supports you card or not. What I would do is make a backup of your current xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then run the xorg reconfigure:
[code]sudo dpkg-reconfigure xserver-xorg[code]

Most of the defaults are ok, use them if you don't know better, but make sure fglrx is selected as the driver. After that, restart X with ctl + alt + bksp and see if direct rendering is on after that. If not, post again, there must be a good turotial around we can work from.

---

### Post by pather on 2008-01-24
I've got fully working ATI card on my PC using fglrx driver, two displays each with different resolution, no problem here. 
Now  I've got second ATI card and connect them using crossifre, works great in games under windows :) But I use windows ONLY to play the games, not for daily use. 
Now is there ANY way to make it work under kubuntu 7.10?
I must say, i did not tried latest drivers from ATI (8.1), I will do it this weekend. But i am still not sure of succes :) ATI's support to linux community is very little.

Since I am not convinced about ATI improving their linux drivers, I still plannig to buy nvidia card, but until such time, i would realy appreciate if I could use my kubuntu like I'm used to... 

thanks a lot for ANY idea :)

---

