---
title: "what do graphics drivers do?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2007-05-13
What do they actually do, Im thinking of getting a new graphics card (around 128mb and £30 if anyone has any suggestions) and need to know what will happen with no drivers, will it have the old windows problem of only going 640x480 and 16colours and will I be able to use compiz 3d cube (in startcom enterprise)

---

### Post by mikewhatever on 2007-05-13
[http://en.wikipedia.org/wiki/Graphic_driver](http://en.wikipedia.org/wiki/Graphic_driver)
welcome to wikipedia :popcorn:

---

### Post by jgrabham on 2007-05-13
OK, perhaps I should re-phrase that.  If I buy an ATI graphics card, what will happen?

---

### Post by psyopper on 2007-05-13
> **jgrabham said:**
> OK, perhaps I should re-phrase that.  If I buy an ATI graphics card, what will happen?

If you buy an ATI card for a Linux distro, well... pretty much nothing will happen... however, if you buy an nVidia card lots of pretty things start happening... Sorry, I couldn't resist. 

Truth be told ATI's support for Linux drivers is slow and painful but they can be made to work. nVidia is more supportive of Linux and they configure much easier. Either way you decide, make sure that your card supports per pixel shading, this is a requirement of Beryl/Compiz. Sometimes they will refer to it as a "Pixel Shading Engine" or a "Shader".

---

### Post by jgrabham on 2007-05-13
So if I get an ATI card ill boot and get an annoying beep code, with nothing on the monitor

---

### Post by Wim Sturkenboom on 2007-05-13
You will get that more than likely of the card is much different from the old video.

Before installing the card, I suggest that you change the video driver (in /etc/X11/xorg.conf) to vesa (pretty universal).
Next install the card; it should work.
Next install the driver for the card and change xorg.conf to use the driver.

Best advice is to do a bit of reading first how to perform the last step (there are plenty instructions here on the forum for the different makes).

---

