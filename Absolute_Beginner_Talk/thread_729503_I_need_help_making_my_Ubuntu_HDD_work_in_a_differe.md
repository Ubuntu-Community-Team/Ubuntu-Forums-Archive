---
title: "I need help making my Ubuntu HDD work in a different computer"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by witeboy724 on 2008-03-19
Hi, I am visiting my home from college, and I brought my hard drive back that has Ubuntu installed.  I didn't want to drag my whole computer back just to show my dad on Ubuntu and try to sell him on it.  I tried unplugging the hard drive that was in the computer and replacing it with mine, but it has some kind of X Control graphics error.  It has a different graphics card then mine, but I was under the impression that I wouldn't have to install drivers for the graphics card.  My nVidia 6800 didn't need one after installing it.  Is there an easy way that I can get this to work?  I can still get to the command line and everything.  Thanks in advance for any help/suggestions!

---

### Post by handydan918 on 2008-03-19
> **witeboy724 said:**
> Hi, I am visiting my home from college, and I brought my hard drive back that has Ubuntu installed.  I didn't want to drag my whole computer back just to show my dad on Ubuntu and try to sell him on it.  I tried unplugging the hard drive that was in the computer and replacing it with mine, but it has some kind of X Control graphics error.  It has a different graphics card then mine, but I was under the impression that I wouldn't have to install drivers for the graphics card.  My nVidia 6800 didn't need one after installing it.  Is there an easy way that I can get this to work?  I can still get to the command line and everything.  Thanks in advance for any help/suggestions!

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bodhi.zazen on 2008-03-19
You could run Ubuntu from a live CD. It is slower, but perhaps easier ?

---

### Post by witeboy724 on 2008-03-20
It would be easier to use a live CD, but I have everything set up so beautifully on mine.  I have custom settings with great graphics things going on.  Anyway I got it going with the line posted above (Thank you!) but now I'm having some weird mouse issues.  It's not moving and I think it's the same generic optical USB M$ mouse that I use back home.  I'll have to take a look around at forums.  Maybe this is just a different problem completely.

---

### Post by handydan918 on 2008-03-20
Try running ```
dpkg-reconfigure xserver-xorg
```again, and double check your mouse input settings.

---

### Post by witeboy724 on 2008-03-21
I did that again and the settings seemed to be ok.  I managed to find a PS/2 mouse that worked fine when I plugged it in.  After logging in I figured out that my USB ports aren't even working at the moment.  It didn't recognize a flash drive that it did when it was in my other computer.  On top of that, Compiz can't be turned on and I have to leave the visual effects on none.  I don't think that there's any simple fix that will take care of all of this and it's really not worth the trouble right now.  Thanks for you help though guys!

---

