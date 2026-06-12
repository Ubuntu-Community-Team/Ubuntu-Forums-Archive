---
title: "Random Hard Freezes"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by msisk on 2007-03-08
Hello all,

I've started making the switch from windows by installing a duelboot (with Edgy) on my laptop and thus far I'm extremely happy with Ubuntu with one rather large exception. After a completely unpredictable amount of time I'm getting hard freezes nearly every time I load (ie no mouse control, keyboard shortcuts don't work, screen stays the way it was). There doesn't seem to be anything systematic about when its happening either. Sometimes its right after booting, sometimes it can be after several hours of working. No correlation with open programs either (not ever Firefox). My first instinct would be a hardware problem, but since this is never happening with windows and that runs my everything a lot harder, it doesn't seem to be the case.



I've looked around the forums a good bit before posting and it seems possible that this is somehow related to my graphics card. Its an older (2003) Gateway laptop with an Intel 82852/82855 GM/GME graphics controller. The drivers seem to be installed correctly.

Anyways, thanks in advance for any replies as this is the only thing keeping me from switching nearly completely from windows.

---

### Post by haelters on 2007-03-08
Did you try to go into console mode (ctrl-alt-F1) ? 
You can also try to log in from another computer using SSH (make sure the daemon is started before).

If you can do this, the problem is narrowed down to an X11 problem. Is there something interesting in /var/log/messages or dmesg ?

---

### Post by msisk on 2007-03-08
No, I'm not able to access to console mode.  And as near as I can tell there is nothing in the logs that repreents the freeze.

---

### Post by bigken on 2007-03-08
I would use sudo dpkg-reconfigure xserver-xorg and select vesa as my video driver 
to see if it still freezes if it still does then we know its not your video drivers so you can rerun the command select your correct drivers

---

### Post by msisk on 2007-03-13
Well, I did as you recomended and it seemed to work for a little bit, but I just got another freeze.  Any further suggestions?

Thanks a lot.

---

### Post by bigken on 2007-03-13
remove your ram chips and use them one at a time in alternate slots also do you have different video card you could try anything will do

---

