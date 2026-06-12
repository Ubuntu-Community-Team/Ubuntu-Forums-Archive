---
title: "No sound at all???"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-12-25
I have just installed Ubuntu on a new computer and I am not getting any sound at all.  Not even system sounds.  I have put the Volume and sound control in the task bar and it is not muted.  

Any Ideas?

---

### Post by NeoLithium on 2006-12-25
In a terminal window, type ```
alsamixer
``` and try turning up *all* of the volumes in there to max.  sometimes alsa mutes something that normally should be left alone.

---

### Post by Russty of Oz on 2006-12-25
OK, did that, everything was already turned up.   Still NOTHING! :(

---

### Post by Russty of Oz on 2006-12-25
Doesn't anyone have any ideas?  I get full sounds on Windows on the same machine, so its not the sound card.

---

### Post by xpod on 2006-12-25
Theres a "multimedia system selector" in your preferences menu....(may need enabled in your munu editor)...you can check things in there too and do sound tests at the same time.

May or may not help??...gives you something else to check

---

### Post by Russty of Oz on 2006-12-25
> **xpod said:**
> Theres a "multimedia system selector" in your preferences menu....(may need enabled in your munu editor)...you can check things in there too and do sound tests at the same time.

May or may not help??...gives you something else to check

It is not there, so how do I enable it in the menu editor?   What is the menu editor?:confused:

---

### Post by logos34 on 2006-12-25
right click on Applications>edit menus

read this:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by Russty of Oz on 2006-12-26
Thanks logos34, that helped, now I can get   sound through speakers, but still nothing through headphones.  Strange!  In alsamixer there is a headphone section but it can't be adjusted, where the others have a volume adjustment above them, headphones don't, just the little green box with oo in it?    Doesn't ubuntu  allow for headphones?

---

### Post by logos34 on 2006-12-26
I don't have 'headphone' in alsamixer on the gnome desktop (terminal or gui), nor  is it in preferences.  Is this a desktop, did you try rear audio jack?...if it works then the front audio cable might not be connected to the board/soundcard.

---

### Post by iPirates on 2006-12-26
Yea, I had a similar problem, except it was no sound coming from the sound card I had (some no-name brand.... guess that's what you get for being cheap!  ;)  )

Switched to on board sound, speakers work fine now, but havent figured out the headphones yet...

---

### Post by Russty of Oz on 2006-12-26
I am using KDE and headphones does show up in alsamixer there.  I tried the headphones in the rear jack but the sound wasn't very loud, even when turned up full.

---

### Post by logos34 on 2006-12-26
ok so it looks like its just a volume issue after all...in cases like this there's usually a simple explanation...some setting that's turned down gets overlooked.  When I plug in my headphones the volume is controlled by the PCM and master volume sliders (and CD is i'm playing a disc).  Try playing around with the settings, check Sound in system settings and try different output.  maybe aRts is causing some mischief.

---

