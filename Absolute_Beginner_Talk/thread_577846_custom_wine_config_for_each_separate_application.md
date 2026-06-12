---
title: "custom wine config for each separate application"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by mhedges48 on 2007-10-16
Hello,

I use Wine a for several Windows programs (Photoshop, Flash, html editor, etc.) and have found I prefer no virtual desktop emulation.

However, with one program (Warcraft II), I have to have the virtual desktop emulation checked to run.  Is there any way, instead of running winecfg before WarCraft to enable the virtual desktop emulation and then run it after to disable it, that within the command line itself (currently ¨"env WINEPREFIX="/home/matt/.wine" wine "C:\Program Files\Warcraft II BNE\Warcraft II BNE.exe" ¨) I can specify for this program only to use desktop emulation?


thanks and best wishes
Matt

---

### Post by LanDan on 2007-10-22
guess nobody knwos the answer for this one, and i don't uyse wine myself either.

what you also can do is to set up a different user with that specific setting if it is too much trouble to set it in wine

---

### Post by phr0ze on 2007-10-22
I thought in winecfg you can create a new profile and give it a seperate setting. The profile will kick in when it detects the named program is being run.

---

### Post by Daveth on 2007-10-22
yes, that's rather what this suggests

[http://gaming.gwos.org/doku.php/wine:winestuff#stuff_in_winecfg](http://gaming.gwos.org/doku.php/wine:winestuff#stuff_in_winecfg)

---

### Post by yabbies on 2007-10-22
open a terminal and type

```
winecfg
```

 Select the Applications tab
 Click "Add application", and a file dialog will pop-up allowing you to select an executable
 Browse to foo.exe and click open.
 With foo.exe selected in the Application tab, select the windows version you want to use for that app
 and Click Apply to save the settings.

---

