---
title: "Brief freezes every 10 sec when dual screen"
date: 2011-01-17
forum: Apple Hardware Users
---

### Post by Emilrx on 2011-01-17
Hello,

I'm enjoying an Ubuntu 10.10 32-Bit single boot on my white macbook 4.1
I searched this forum for a similar problem unsuccessfully...
(My apologies if my searches where too superficial, and my thanks if one of you has a link to a similar subject)

Almost everything works fine except when I plug-in my hdmi TV.
Once it is plugged, before even activating the display, the system freezes briefly (approximately 0.2 sec) every 10 seconds (again approximately).

Thought this is not a major problem, it is quite frustrating when watching videos or even just moving the mouse...

The TV is plugged through the apple adapter and a dvi-hdmi cable.
But I don't believe it's a hardware problem since it worked flawlessly with leopard...

I tried to turn off the desktop effects with no improvement.
Even with the effects the frame-rate is good (except for the lagging pblm)

a "xrandr" in the terminal shows me :

```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 286mm x 179mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DVI1 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   50.0     24.0  
   1280x1024      60.0  
   1360x768       59.8  
   1280x720       50.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
TV1 disconnected (normal left inverted right x axis y axis)

```

witch looks normal to the beginner I am.

Because I'm an linux beginner, maybe I'll say something stupid but...
I've read somewhere that xorg.conf no longer existed since there was a kind of "auto-detection mode".
Might there be some process trying to auto-detect screens every 10 seconds?
I've had a look at the "system monitor", but couldn't find anything (maybe the monitor's refresh rate is too low?)

I've also read that it is possible re-create a xorg.conf file.
Would that stop the hypothetic auto-detection process?
I might try this solution (if one doesn't inform me it would be useless) but I fear the behavior of the system after that when I plug/unplug my screen.
So, before trying, I'd like to be sure there is a way to restore the previous "auto-detection mode" (might be as simple as removing the xorg.conf file, but I'd rather ask first than take the risk immediately)...

Well, that's all I could figure out by my own for the moment, so if anyone has any clue, or any investigation idea, or can reassure me about the deleting-the-xorg.conf part, I'd be glad to read it :)

Thanks by advance

---

