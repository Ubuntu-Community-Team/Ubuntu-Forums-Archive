---
title: "The Final Step: Grub to Lilo (MBP)"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-05
So I have all the major stuff down... wireless, sound, etc... now I need to try to switch my bootloader changed so my keyboard is detected....

My question... are there any risks in doing this or is it pretty easy to go back?


If not.. then what do I need to do?



Also one last thing.... anyone find the default settings for the keyboard/track pad for the mbp really annoying? Any guides to fix all that... I can't even right click!!

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> So I have all the major stuff down... wireless, sound, etc... now I need to try to switch my bootloader changed so my keyboard is detected....

My question... are there any risks in doing this or is it pretty easy to go back?


If not.. then what do I need to do?



Also one last thing.... anyone find the default settings for the keyboard/track pad for the mbp really annoying? Any guides to fix all that... I can't even right click!!
First step is to install something like GSynaptics or QSynaptics (I prefer Q, dunno why). Once you grab that you can futz with your trackpad settings. You'll have to add```
Option     "SHMConfig"     "true"
``` in your xorg.conf and restart X in order for it to work.

---

### Post by The_Giver on 2007-05-05
> **ronocdh said:**
> First step is to install something like GSynaptics or QSynaptics (I prefer Q, dunno why). Once you grab that you can futz with your trackpad settings. You'll have to add```
Option     "SHMConfig"     "true"
``` in your xorg.conf and restart X in order for it to work.



Does that "Option" just go anywhere in xorg... sorry not familiar with this file even though I should be

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> Does that "Option" just go anywhere in xorg... sorry not familiar with this file even though I should be
I apologize. In a terminal, type ```
sudo gedit /etc/X11/xorg.conf
``` Remember that it's case-sensitive, so the X must be capitalized. Then scroll down till you find the section for your trackpad. Once you do, add the Option line in there. (There should be other option lines, too. Just add it below them.)

Once that's done, save, then restart X. Quick and dirty way to do this is ctrl+alt+delete.

---

### Post by The_Giver on 2007-05-05
Thanks... did that.. now how should I be able to tell it worked??? I am under mouse pref and I cant remember if it is the same.

Also how do I right click and... is there a guide for mapping/modifying the keyboard layout?

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> Thanks... did that.. now how should I be able to tell it worked??? I am under mouse pref and I cant remember if it is the same.

Also how do I right click and... is there a guide for mapping/modifying the keyboard layout?
Try [here]("http://ubuntuforums.org/showthread.php?t=417669&highlight=macbook+right+click"). Perhaps [this guide]("https://help.ubuntu.com/community/MacBook") mentions it, though I don't recall.

---

### Post by The_Giver on 2007-05-05
I guess typing qsynaptics on the konsole works.. right click is three/two fingers.. however.. (can i get this from some other menu?) and is there anything on keyboard sutff ...

I remember hitting a key combo that would bring up like a run command on linux a few years back.. is that still there.. if so does anyone know the shortcut..  (run command as in I can type in some applications name or directory and it would bring it up)

Also... for initializing  different sessions of xserver... what is that command again

startx --01   fluxbox or something?

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> I guess typing qsynaptics on the konsole works.. right click is three/two fingers.. however.. (can i get this from some other menu?) and is there anything on keyboard sutff ...

I remember hitting a key combo that would bring up like a run command on linux a few years back.. is that still there.. if so does anyone know the shortcut.. also... for initializing  different sessions of xserver... what is that command again

startx --01   fluxbox or something?
ctrl+alt+f2 might be what you're thinking of. I personally prefer working in the terminal so I can, for example, keep chatting on this forum and in IM, too. ;) I don't know a command for another session, unfortunately. Please post it when you find it.

---

### Post by The_Giver on 2007-05-05
I got it all down to what I want but Qsynaptics wont automatically apply my settings at start up.... I have to open it up and "click" apply.. all my settings are already there but they are not applied until i click applied every time I reboot.


You were right about the shortcut.. its ALt + FN + F2 for me though.. its annoying to have to press FN though

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> I got it all down to what I want but Qsynaptics wont automatically apply my settings at start up.... I have to open it up and "click" apply.. all my settings are already there but they are not applied until i click applied every time I reboot.
Hm, this may be as easy as adding Qsynaptics at startup by doing:
```
sudo modprobe qsynaptics
```
Please someone correct me if I'm wrong, because that's how I'd do it.

---

### Post by The_Giver on 2007-05-05
Well I'm still wondering how the hell I migrate to LILO...  any guides?



Also, how do I know if I am connecting to  a WPA network? Will it asks me for something... can I check under OS X or XP?

---

### Post by The_Giver on 2007-05-05
FATAL: Module qsynaptics not found.


That's what I get when I try to run that command (and yes  all the packages under software sources were turned on).

---

### Post by ronocdh on 2007-05-05
> **The_Giver said:**
> FATAL: Module qsynaptics not found.


That's what I get when I try to run that command (and yes  all the packages under software sources were turned on).
My apologies, then. Perhaps you'll have more luck with Gsynaptics?

---

### Post by The_Giver on 2007-05-05
It's okay.. no big deal really.... minor annoyance.. however I do wish someone would help out with the damn grub problem... I feel like i'm just damaging my computer by cold booting so many times.

---

