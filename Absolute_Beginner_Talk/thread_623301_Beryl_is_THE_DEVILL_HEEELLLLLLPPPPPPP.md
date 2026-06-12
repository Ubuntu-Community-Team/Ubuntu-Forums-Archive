---
title: "Beryl is THE DEVILL HEEELLLLLLPPPPPPP"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by austinbowman on 2007-11-25
OK, i have read every guide there is to try and get beryl to work. it mostly works, i just dont have the tops of windows, minimize, maximize close whatever. i installed compiz and that worked, but the settings manager is just a little to complicated for me. i like the beryl settings manager and i really need it back. i checked the xorg settings i installed and reinstalled emerald and nothing seems to work. help me out please guys this is my last resort.

---

### Post by bluepowder7 on 2007-11-25
i think those are called window decorations.  it's one of the plug-ins.

---

### Post by austinbowman on 2007-11-25
well what is the solution dude?

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> OK, i have read every guide there is to try and get beryl to work. it mostly works, i just dont have the tops of windows, minimize, maximize close whatever. i installed compiz and that worked, but the settings manager is just a little to complicated for me. i like the beryl settings manager and i really need it back. i checked the xorg settings i installed and reinstalled emerald and nothing seems to work. help me out please guys this is my last resort.

Hi and did you try emerald --replace using the alt,F2 keys?

---

### Post by austinbowman on 2007-11-25
yes and it doesnt do anything

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> yes and it doesnt do anything

Ok what is the model of the video card?

---

### Post by austinbowman on 2007-11-25
nvidia 7600gt

---

### Post by hanzomon4 on 2007-11-25
Beryl is so outdated, stick to compiz-fusion. Not doing so is just asking for problems.

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> nvidia 7600gt

Ok then you may want to add these to your xorg.
 Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
In the device section using the command ```
gksudo gedit /etc/X11/org.conf
```but back up you xorg first
To copy Xorg
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
To restore backup
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by austinbowman on 2007-11-25
ok well i entered the command and i have already checked that area and all of the changes where aready there. but i entered them again anyway and nothing happend.  I dont really have a problem with compiz fusion, except that the menu sucks. is there another interface?  compiz fusion works but i cant get cubed desktop on it, only like a peice of paper, two sides. and it wont change even if i select four desktops at the bottom taskbar or whatever. whats up with that?

---

### Post by austinbowman on 2007-11-25
And Now Compiz Doesnt Have Window Tops.. I Have Been On Here All Day Trying To Figure This Out!!!!!!!!!! Uggh

---

### Post by bluepowder7 on 2007-11-25
i only use CompizFusion, never tried Beryl.

the desktop thing is weird - in the general menu, there's 3 sliders.  the top one is set to 4 or whatever, the middle and bottom are on 1.  right?  yeah, no tops.  at least no "desktop" tops.  you can put a picture on the top and bottom, though.

by the way, did you install the desktop manager?  the window decorations are one of the plugins, and you can just checkmark them on or off, and adjust some of the "features" of the borders.

---

### Post by austinbowman on 2007-11-25
im talking about the tops to individual windows. i have to use alt to move them and all of the effects work but i cant just click close minimize or whatever. frustrating

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> im talking about the tops to individual windows. i have to use alt to move them and all of the effects work but i cant just click close minimize or whatever. frustrating

In the ccsm under system, preferences, advance desktop effects. You will need to make sure windows decoration is check.

---

### Post by austinbowman on 2007-11-25
it is there, checked and everything, i have probably check that a hundred times in beryl and compiz and still no result

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> it is there, checked and everything, i have probably check that a hundred times in beryl and compiz and still no result

Ok which version of ubuntu, Fesity or  Gutsy?

---

### Post by austinbowman on 2007-11-25
gutsy

---

### Post by Tteddo on 2007-11-25
You might want to read through this [page]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"). It helped me fix some weird problems. Check the troubleshooting section.
I big thing in things like this is to do one thing at a time, test it, then move on.

---

### Post by Tyke91 on 2007-11-25
you need to get the compiz-config settings manager if you haven't done so already, the choice for more and fewer desktops is under "general" and the cube effect is under "Desktop Cube"

I've gotten desktop cubes ranging from 2 to 19 sides :D

---

### Post by austinbowman on 2007-11-25
i have been to that page and i already did all of that and it didnt work, i have to cube effect i just cant change the amount of desktops. it seems like the more i try and fix this problem the worse it gets, if anyone can get me a walk through for uninstalling all gui stuff  and starting over from the beginning and maybe the problem will be easier to find

---

### Post by overdrank on 2007-11-25
> **austinbowman said:**
> i have been to that page and i already did all of that and it didnt work, i have to cube effect i just cant change the amount of desktops. it seems like the more i try and fix this problem the worse it gets, if anyone can get me a walk through for uninstalling all gui stuff  and starting over from the beginning and maybe the problem will be easier to find

HI you can just use synaptic manager to remove all of compiz when you search. Synaptic manager is located under system, administration, synaptic. If you installed beryl by adding repos from Feisty this will cause several issues with compiz-fusion.

---

### Post by hanzomon4 on 2007-11-26
Do you have compizconfig-settings-manager?

---

