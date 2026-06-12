---
title: "my monitor is messed up."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by je.famous chief on 2008-04-08
i was messing with the screen resolution. screens and graphics, that sort of stuff. i totally blew it. the resolution has to be so low in order to get the full screen. i'm missing the left and the bottom. i feel like its something dumb. Like some goofy setting i put on.

why i was messing with this is that video quality looks real bad and i was messing with it to get it to work right.

i have a toshiba satellite m35-s320. 15.4 inch widescreen lcd. what should this be at? why was my video quality bad in the first place?

and it tells me this,

"no monitor supporting DDC/CI available.
If your graphics card need it, please check all the required kernal modules are loaded (i2c-dev, and your framebuffer driver)."

whats going on?
Someone help me and be easy on me. I'm new.

---

### Post by Joeb454 on 2008-04-08
Ok, so can you open up a Terminal, from Applications>Accessories>Terminal

and then type or paste the following```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That should allow you to reconfigure the graphics options :) It's not too hard to understand either from what I remember :)

---

