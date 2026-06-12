---
title: "Put the virtual desktop too small for wine"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-08
Is there a way to increase the Virtual desktop for WINE, I need to configure it but can't reach the apply button becuase the VD is too small

---

### Post by Daveth on 2007-11-08
```
winecfg
```

then the graphics tab, and alter the desktop settings, is one way.

---

### Post by Dapman01 on 2007-11-08
thanks

---

### Post by kealan on 2008-02-17
I'm having the same problem, and winecfg is useless because the screen is to small to reach the apply button at the bottom of the screen after unchecking the virtual desktop option.

---

### Post by kealan on 2008-03-31
Really? No one can help us? I've spent many hours on this problem, it's not quite worth reinstalling ubuntu, but it's really driving me nuts.

---

### Post by Tyke91 on 2008-03-31
Shift+A will accept if your mouse is held over the window.

---

### Post by rkd on 2008-03-31
I'm not clear on what the problem is, but this might help:

You can drag a window around by holding down the Alt key then clicking and dragging on ANY spot in the window.  So you can use this to get any part of a window that is too big for the screen to be visible.  It still is a bit of a pain to use such a window because you can't see it all at once, but at least you can get to all parts of it fairly easily.

---

### Post by ben2talk on 2008-04-08
Ok, let me try to explain the problem again - I now have the problem too!

The 'Virtual Desktop' is now in a window, with a lovely wobbly emerald window. I checked this because I wanted my 'netmeter' application in a small window, and sticky on all desktops (can't do in wine, but can do with emerald window).

So I set the desktop settings in wine to 320 by 240. Nice.

Problem - now if I open the settings, I cannot access the parts of the windows I need. In WINE, you cannot drag the WINE window using the ALT click - this will only work for the whole desktop window. I need to either move the contents, or....

WHERE ARE THE SETTINGS FOR WINE stored, is there a config file I can reach and edit? It seems that WINE is unable to give me access to the settings.

I hope someone understands, and can give me an answer - I now had to stop using WINE for everything except for the NetMeter.

---

### Post by rkd on 2008-04-08
Sorry, I don't know anything about WINE, but post #2 says that you can change WINE settings using winecfg.  I assume you open a terminal and enter winecfg to the command prompt, but, as I said, I don't know anything about WINE.

---

### Post by Tylazene on 2008-04-08
I had that same problem too. I figured out a real easy way to fix it. I typed (not clicked) the size I wanted into the box and hit enter. Oh, and make sure your screen resolution is up high enough.

---

### Post by SpongeBob SquarePants on 2008-04-08
> **ben2talk said:**
> Ok, let me try to explain the problem again - I now have the problem too!

The 'Virtual Desktop' is now in a window, with a lovely wobbly emerald window. I checked this because I wanted my 'netmeter' application in a small window, and sticky on all desktops (can't do in wine, but can do with emerald window).

So I set the desktop settings in wine to 320 by 240. Nice.

Problem - now if I open the settings, I cannot access the parts of the windows I need. In WINE, you cannot drag the WINE window using the ALT click - this will only work for the whole desktop window. I need to either move the contents, or....

WHERE ARE THE SETTINGS FOR WINE stored, is there a config file I can reach and edit? It seems that WINE is unable to give me access to the settings.

I hope someone understands, and can give me an answer - I now had to stop using WINE for everything except for the NetMeter.

I had this problem a while ago. It's to do with the "Emulate a virtual desktop" setting. For some reason, once this option is ticked "winecfg" comes up in a virtual sized window too, and depending on what settings you've chosen, more often than not it cuts off half your options. 

The way round it, for me at least, was to untick "Emulate a virtual desktop" under "Graphics", then hit enter (the keyboard key). Then reopen "winecfg". It will be just as it was before. Change what you need to change and then re-enable "Emulate a virtual desktop" again by ticking the option under "Graphics" and hittng "OK".

---

### Post by kealan on 2008-04-14
Ben2Talk, yes I totally understand.  This was finally solved for me on this thread: 
[http://ubuntuforums.org/showthread.php?p=4718112#post4718112](http://ubuntuforums.org/showthread.php?p=4718112#post4718112)

---

