---
title: "Xubuntu, TNT2 and tv-out"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by Cole_ on 2007-09-17
Hello!

I plugged a tv set to my PIII 600 desktop with nVidia Riva TNT2 and it works. However, the area of the screen is very narrow - I can't see either taskbar. The resolution is set to 800x600 and the display doesn't take the whole tv screen. Is there a way to make it fit? 

On a common CRT monitor there is a number of buttons to adjust it, but I don't have them on my tv. Earlier I had a Windows system working on that machine and the view was perfect. I've heard that there is a way to describe the screen's borders in xorg.conf, but I don't know how. 

Thanks in advance for any suggestions. I don't want to throw this 7 year old machine to trash while it's still working, so I'm going to make a low cost media center out of it :popcorn:

---

### Post by bone2006 on 2007-09-18
have you tried [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) also maybe try the new beta of ubuntu with liveCD.  I believe they have new features to help you change xconf

---

### Post by Cole_ on 2007-10-05
Thanks for your reply.

However, none of the drivers provided by Envy (there were three possibilities) work correctly - one brought proper resolution to my tv, but... greyscale. The others were forcing me to rebuilt xserver.

I can't use any live cd unfortunately - I don't have enough memory. I guess I have to wait for 7.10 (now it's 13 days left) and then update my system.

---

### Post by Golyadkin on 2007-10-05
Well, a normal (PDTV) television can't display 800x600, it is too big. I am not sure, but I think Poland has PAL televisions as well, which means it can only display 720x576 pixels.

---

### Post by Cole_ on 2007-10-08
Yes, you're right. I found somewhere, that PAL had 625 lines, but when I changed the resolution to 600x400 it works OK.

---

