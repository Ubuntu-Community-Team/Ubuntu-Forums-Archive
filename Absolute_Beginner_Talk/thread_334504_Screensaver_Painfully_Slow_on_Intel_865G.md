---
title: "Screensaver Painfully Slow on Intel 865G"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2007-01-09
I have noticed that on my wife's ubuntu setup, the full-size screensaver is painfully slow.  I was trying to find an explaination for it, but I only came up with these two entries in the search: [http://www.ubuntuforums.org/search.php?searchid=12464819](http://www.ubuntuforums.org/search.php?searchid=12464819).

I know this isn't the best computer out there, nor the best graphics chip, but I'm pretty sure it should be going faster than it is.  I tried to watch the flurry screensaver (the one ported over from the MAC OSX), but it was too slow to watch.

Is there anything that can be done?  Should I uninstall the gnome-screensaver and install xscreensaver instead?  It sounds like this is the only solution.

Just curious.  Thanks for any help in advanced.

---

### Post by SendDerek on 2007-01-09
You know... I'm sorry.  I didn't realize how many times this is touched upon in the forums.  My first search wasn't nearly good enough.  I'm reading through the other posts to figure out what to do and how to do it.

Thanks for looking.

---

### Post by deadgobby on 2007-01-09
Oh my eye are on fire for looking. :eek: 
Gobby

---

### Post by housam on 2007-01-09
I have the same problem with intel GMA950 card, but this happened only after installing beryl and XGL. I knew from the forum that XGL slow ubuntu with intel cards. I don't know if there is a solution for this or not.

---

### Post by sardion on 2007-01-09
As to the general queation here: make sure you have the right Xorg driver being used and that drm and dri are working.  Search the forums for more info.

As to the beryl/xgl on intel..... don't use XGL with Intel chips.  Its slow and pointless.  Just install beryl on top of the standard xorg-aiglx (included with edgy).  XGL is for ATI cards.

---

### Post by housam on 2007-01-09
> **sardion said:**
>   
As to the beryl/xgl on intel..... don't use XGL with Intel chips.  Its slow and pointless.  Just install beryl on top of the standard xorg-aiglx (included with edgy).  XGL is for ATI cards.
So, I 've to remove beryl and XGL then install aiglx then reinstall beryl.

---

