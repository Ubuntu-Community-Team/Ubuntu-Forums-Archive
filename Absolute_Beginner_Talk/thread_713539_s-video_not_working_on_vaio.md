---
title: "s-video not working on vaio"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by utitanka on 2008-03-02
hi, i have a vaio PCG-7R2P laptop, with a built in s-video output, and i cant figure out how to make it work, i have been looking in other post but the only solution is based on an nvidia video card, and i have an Intel video card, i don't know if this information is useful. i appreciate any idea,thanks.  have in mind I'm a complete newbie, but ill make the effort.

---

### Post by ggaaron on 2008-03-29
I have an Intel card too, so I can help. Just mind the fact that I haven't found any graphical tool to change outputs that actually worked as I wanted.

There is a tool named xrandr, and this is what you need. Install this program, plug in something to s-video and then just run "xrandr" you should have there an LVDS entry and a TV entry. Now you can do something like:
xrandr --output LVDS --mode 1280x800 --output TV --mode 800x600 --above LVDS

see xrandr --info for more options like --right-of or --same-as.

---

