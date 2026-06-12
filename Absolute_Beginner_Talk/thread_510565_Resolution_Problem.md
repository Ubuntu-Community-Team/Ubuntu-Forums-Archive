---
title: "Resolution Problem"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by IDunno19 on 2007-07-26
Hey everybody,

I have a widescreen monitor and I'd like to run Ubuntu in 1680x1050 resolution, but it isn't an option when I try to change the screen resolution.  Can anybody give me a hint on how to fix this?

Thanks!

---

### Post by skymera on 2007-07-26
whats your graphis card?

---

### Post by Rocket2DMn on 2007-07-26
You will need to run:
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through the configuration of some of your computer's components (mouse, keyboard, etc).  Select your video driver based on the type of graphics card you have, then when you get to the resolution, use TAB to move through the selections and SPACEBAR to select the highest resolution your monitor supports and everything less than that.  Then restart the Xserver (the GUI) by hitting CTRL+ALT+BACKSPACE

---

