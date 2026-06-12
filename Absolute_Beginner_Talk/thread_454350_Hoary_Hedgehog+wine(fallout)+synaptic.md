---
title: "Hoary Hedgehog+wine(fallout)+synaptic"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Bocalt on 2007-05-25
Hi, 
i'm still new with Ubuntu though i've been using 5.04 for two years now, Its stable and great to do the stuff i need to do(work). Recently i've found that synaptic is like completely broken, can't update and stuff, but i guess its okay unless someone has an idea...
My issue is that i want to install wine, a recent version, the last one i installed from synaptic dates back to 2005 and i can't run games except for fallout 1 and even then its in a small window . So basically how either:
1) to install a new wine without synaptic
2) run Fallout 1 more comfortably (with sound +  resolution)
3) i successfully installed  fallout 2 but it begs for the cd what to do?

Any help would be considered equivalent to a miracle

---

### Post by Outrunner on 2007-05-25
I'm not sure about the 1 and 3 but I think I might have an idea for 2. First you need to know what resolution Fallout uses natively. then type xrandr in the terminal. It will display a bunch of resolutions available to you. Now look at the number beside them(and below SZ). Lets say 800x600 is the native resolution for Fallout and that 2 is the number for 800x600. Now look at this script

```
#/bin/bash
#
xrandr -s 2
killall -19 gnome-panel
wine .wine/drive_c/Program\ Files/Starcraft/StarCraft.exe -nice 20
xrandr -s 0
killall -18 gnome-panel 
```

Basically you would just need to change the directory path. Then save it in your home foldre as, say, fallout.sh and type in the terminal

```
sudo chmod a+x fallout.sh
```

And everytime you want to start Fallout you can just do a ```
sudo ./fallout.sh
``` from the terminal. It works for me to play starcraft fullscreen

NOTE: I did not make this script by myself, I too used an example given by a member of this forum. I'd like to give credit where it is due, but I just can't remember who this user was(I found his post by searching the Gamimg & Leisure forums)

---

### Post by compmodder26 on 2007-05-25
Hoary is no longer supported.  I'm pretty sure that is why you can't update any more or install new stuff through synaptic.  Each ubuntu release is supported for 18 months, with the exception being LTS releases which are supported for 3 years on the desktop and 5 years for the server.

I would suggest you upgrade.

---

### Post by Bocalt on 2007-05-25
Thanks for the script Outrunner but wine doesn't want to launch the game... still launches in small window 
modified it as follows:
#/bin/bash
#
xrandr -s 2
killall -19 gnome-panel
wine .wine/fake_windows/Program Files/Interplay/Fallout/Falloutw.exe -nice 20
xrandr -s 0
killall -18 gnome-panel


ps
I'm going to update someday as soon as i can find time away from work and resources to backup all my stuff.

---

### Post by Outrunner on 2007-05-25
```
#/bin/bash
#
xrandr -s 2
killall -19 gnome-panel
wine .wine/fake_windows/Program\ Files/Interplay/Fallout/Falloutw.exe -nice 20
xrandr -s 0
killall -18 gnome-panel
```

Should look like this, I think. Notice the \ between Program and Files. Linux, by default, doesn't recognize white spaces.

---

### Post by Bocalt on 2007-05-25
Thanks it works... any idea for the no sound issue? (hopeful eyes)

---

### Post by Outrunner on 2007-05-25
Ohh, I didn't notice you had a problem with your sound. OK, well to get this work for Starcraft I just typed ```
winecfg
``` in the terminal then chose add application, and choose your fallout .exe click ok. Then, having Falloutw.exe(I assume) selected in the Application Settings menu go to the Audio tab. Then experiment with the settings. For example for Starcraft I had to set Hardware Acceleration to Emulation instead of Full. Good luck.

EDIT: I've also noticed [HERE]("http://appdb.winehq.org/appview.php?iVersionId=43") that you should use -nice 18 for a better gameplay experience. Of course, you might want to experiment with this setting as with the Audio settings above, to find out what works best for you.

---

### Post by Bocalt on 2007-05-27
Thank you so much i've just found time to experiment a little, i get a message while launching the winecfg which tells me that "winecfg does not actually alter your configuration" and tells me to modify wine/config file... any idea where i go from there?

---

