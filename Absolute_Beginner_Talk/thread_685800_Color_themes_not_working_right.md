---
title: "Color themes not working right"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-02-02
Ok, so I got ubuntu up, working, and wonderful. I installed CompizFusion and think it beats the crap out of Vista and Leopard combined. However, I've got one small problem that you can hopefully help me fix. 

If I try to use the usual "appearance" option to switch themes, it changes my scroll bars, the virtual desktop space colours down in the bottom left, etc. However, for some reason, all of my window frames stay a blood red colour. 

I couldn't find anything in the advanced settings that is overriding it, but I very well may have missed it.

To install it, I used this guide:

[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200]("http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200")

So I used synaptic to get: 
compizconfig-settings-manager
Emerald
and Gnome-compiz-manager

Are any of these conflicting and making the frames red? I'd include a screen shot, except that it doesn't include the frame and if I do it of just the desktop, the frame fades to gray anyway.

---

### Post by Tenken on 2008-02-02
You are using the emerald window manager instead of metacity, which is the default in gnome. You have to change the window boarder in System->Preferences->Emerald Theme Manager, it doesn't have any themes installed by default except that red one, you can find more [here]("http://gnome-look.org/index.php?xcontentmode=102&PHPSESSID=348dfb1008ab573cff70d2c824b69978") or [here]("http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=fd85decee16f234d21ca3eabca3e246b").

---

### Post by dgbearcat on 2008-02-02
> **Tenken said:**
> You are using the emerald window manager instead of metacity, which is the default in gnome. You have to change the window boarder in System->Preferences->Emerald Theme Manager, it doesn't have any themes installed by default except that red one, you can find more [here]("http://gnome-look.org/index.php?xcontentmode=102&PHPSESSID=348dfb1008ab573cff70d2c824b69978") or [here]("http://compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=fd85decee16f234d21ca3eabca3e246b").

Awesome, thanks! I wasn't sure exactly if emerald was a window manager or if it was some kind of package dependency thing that Fusion needed.

---

