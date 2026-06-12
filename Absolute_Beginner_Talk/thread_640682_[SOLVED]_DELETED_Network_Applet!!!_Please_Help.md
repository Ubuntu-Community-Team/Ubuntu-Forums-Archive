---
title: "[SOLVED] DELETED Network Applet!!! Please Help"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Scarath on 2007-12-14
Hi

Ok so on the top bar of the gnome desktop there is the network applet, the one that you right click on and you can choose to 'enable wired' and 'enable wireless' etc and when you left click on it it shows you the wireless networks that are around.

Anyway i deleted it by accident (trying to remove something else) and when i added the 'network applet' back onto the tool bar it was different!!!!!

This network applet splits into 2 applets (one for wired one for wireless), does not seem to pick up wireless signals as well and is generally spoiling my computer use.

Is there anyway of getting the other one back (the one u get when u first install ubuntu)??

Last time this happened i just reinstalled and i dont really wanna do that. 

I have already:  Tried uninstalling and re-installing the gnome network status applet 
                         Tried doing the same for the ubuntu keyring

                         Would uninstalling and reinstalling the whole ubuntu desktop do it?

Thanks

---

### Post by Nano Geek on 2007-12-14
Try running this.```
killall nm-applet && nm-applet &
```

---

### Post by philinux on 2007-12-14
Dont panic,

Click add to panel then find notification area. Add it. You may need to restart x for it to come back.

---

### Post by Scarath on 2007-12-14
> **philinux said:**
> Dont panic,

Click add to panel then find notification area. Add it. You may need to restart x for it to come back.

**notification area!** at last i know the name of that damn thing! 

Thanks for the help guys SOLVED!

---

### Post by Nano Geek on 2007-12-14
You're welcome.

---

