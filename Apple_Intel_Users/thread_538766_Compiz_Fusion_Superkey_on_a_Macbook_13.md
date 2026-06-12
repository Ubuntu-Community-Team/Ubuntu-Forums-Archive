---
title: "Compiz Fusion Superkey on a Macbook 13?"
date: 2007-08-30
forum: Apple Intel Users
---

### Post by gmc on 2007-08-30
Hi Folks,

Does anyone know how to make the "Apple" key on my 13" Macbook, act as the **superkey** in Compiz Fusion. I have CF installed but cannot use any operations that require the use of the superkey? I have a feeling it's because I have :

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      **"pc105"**
        Option          "XkbLayout"     "us"
EndSection

```Can anyone shed any light on this problem?

Thanks
Gord

---

### Post by viciouslime on 2007-08-30
You need to set the keyboard model to be mac. When you installed ubuntu you should have had the choice of a mac keyboard. I'm not sure how to change it for the whole system now. But you should be able to change it on a per user basis from System/Preferences/Keyboard

---

### Post by cyberdork33 on 2007-08-30
> **viciouslime said:**
> You need to set the keyboard model to be mac. When you installed ubuntu you should have had the choice of a mac keyboard. I'm not sure how to change it for the whole system now. But you should be able to change it on a per user basis from System/Preferences/KeyboardI think that will only change for your Gnome session, try changing:
```
Option      "XkbModel" "mac"
```

---

### Post by gmc on 2007-08-30
Hi Folks,

During my hacking around to get the superkey working in Compiz Fusion, I really screwed up my gnome configurations. So I deleted **~/.gnome, ~/.gnome2, ~/.gconf and ~/.gconfd** (I believe CF stores it's configurations in one of those directories). Anyhow when I restarted the system, the apple key began acting as the superkey. I guess I must have turned on/off something in CF that caused the problem.

It's working now. Thanks for the assistance..

Regards
Gord

---

### Post by benanzo on 2007-08-31
I'm not sure what you did, but the Apple keys (both left and right) should function as Super_L and Super_R by default with your keyboard set as pc105.  I've run Ubuntu on my first-gen MacBook since Edgy and have never set the keyboard as **mac**, always **pc105** and have never had any problems.

---

### Post by trvr on 2007-09-01
mine also act as the superkey. the one way I know to test what key does what is to install xbindkeys and run it from the terminal as 'xbindkeys -k' and then press the key you want to find out. When I do this, the command key is Mod4 + Super_L.

I'm not sure that will fix your problem, but it may help to find out what key it is programmed to.

---

