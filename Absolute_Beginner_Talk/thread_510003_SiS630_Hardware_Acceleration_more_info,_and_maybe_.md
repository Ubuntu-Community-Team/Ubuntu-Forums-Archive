---
title: "SiS630 Hardware Acceleration: more info, and maybe progress"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Paulmd on 2007-07-26
Well, it appears I'm too stubborn to give up on the Sis630 hardware acceleration issue.

I have made headway. Or at least I have found out some hopefully useful information.

1) [www.sis.com](www.sis.com) does have a file called xsis.tgz that has the appropriate drivers

2) xsis.tgz  contains one program called XSiS_SVGA, and no helpful readme file.

3) XSiS_SVGA  is NOT a module to be loaded in xorg.conf, despite bogus info on the Web. (praise be that i backed up xorg.conf first , or I would be without a GUI just now). It is a program that wants to edit the xf86config file found in other versions of linux, but not apparently Ubuntu 7.04. 

4) XSiS_SVGA cannot be run while in GUI mode, it must be run in recovery console (a terminal window doesn't cut it)

5) when run in recovery console, it wants the location of the xf86config file, which doesn't exist, and when pointed to the location of xorg.conf, it returns a compile error. 

After that, I'm uncertain of where to go.  Some instant research reveals that the xf86config and xorg.conf files are very similar in format. Perhaps if i had a valid xf86config file (preferably generated from my system) , I could point XSiS_SVGA to it, and then manually edit xorg.conf to match the changes made.

If I succeed, I can post a procedure for all the many people with the same issue.

How would I go about generating an xf86config file? (typing xf86config in the terminal does nothing)

---

### Post by ddrichardson on 2007-07-27
There's lots of info [here]("http://www.xfree86.org/4.3.0/XF86Config.5.html") and [here]("http://www.treachery.net/~jdyson/infosec/linux/XF86Config_Demystified.html").

At one stage Xorg and Xfree86 releases were very close (around the time all that GPL unpleastness arose). How about copying the xorg.cong to xf86config. There used to be a utility called XF86Configurator that did the trick but I've no idea if its still around.

---

### Post by Paulmd on 2007-07-28
> **ddrichardson said:**
> There's lots of info [here]("http://www.xfree86.org/4.3.0/XF86Config.5.html") and [here]("http://www.treachery.net/~jdyson/infosec/linux/XF86Config_Demystified.html").

At one stage Xorg and Xfree86 releases were very close (around the time all that GPL unpleastness arose). How about copying the xorg.cong to xf86config. There used to be a utility called XF86Configurator that did the trick but I've no idea if its still around.

Thanks, I'll give it a go tomorrow. (its past midnight here) I'll keep you posted.

---

### Post by micdhack on 2007-08-12
> **Paulmd said:**
> Thanks, I'll give it a go tomorrow. (its past midnight here) I'll keep you posted.

any progress on this driver?

---

### Post by Paulmd on 2007-08-14
> **micdhack said:**
> any progress on this driver?

Not really. After 20 or 20 times of losing the gui and having to fix it, i had to give up.   On most desktop machines with this chip, you can just slap an agp video card in it and be done with it.  On laptops, and my all in-one that wasn't an option.  If you have a desktop with an agp slot, a compatible card (say a geforce 2) can be had second-hand, cheap. 

I may revisit the issue at some point.

---

