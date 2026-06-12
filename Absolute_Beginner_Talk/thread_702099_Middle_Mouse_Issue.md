---
title: "Middle Mouse Issue"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by kelots on 2008-02-19
Hi Guys,

I'm fairly new to ubuntu and have managed to get most things working

Only thing that is not is my middle mouse button

I've gone through alot of the suggested things and i'm not too bad with command line and have changed everything around as much as i can, but i cant get it to work

when use that command that tells me what buttons is mapped to what, and i click on the middle button, it says it is detected as 'left scroll'

how do i map this to be 'mouse click'?

i have a 5 button mouse + wheel :)


any help would be appreciated as i dont know where to start looking :P

---

### Post by kristjans on 2008-02-19
Your mouse's brand and make please. :)
I had to change xorg.conf to get my 5-button Logitech MX310 working correctly. I won't have access to neither Ubuntu or my desktop for the next 2 hours though, stuck at work with my laptop and Arch Linux.

---

### Post by kelots on 2008-02-20
lol it just says 'microsoft mouse'

umm its white and red, optical USB mouse

don't know the specs or a copy of my xorg

im at work atm just had some downtime thought i'd see if anyone had seen it before, will post the info once i'm home and its in front of me :)

---

### Post by kelots on 2008-02-20
[http://www.x.org/archive/X11R6.8.2/doc/mouse.4.htm](http://www.x.org/archive/X11R6.8.2/doc/mouse.4.htm)


first part: 

     

Auto, Microsoft, MouseSystems, MMSeries, Logitech, MouseMan, MMHitTab, GlidePoint, IntelliMouse, ThinkingMouse, ValuMouseScroll, AceCad, PS/2, ImPS/2, ExplorerPS/2, ThinkingMousePS/2, MouseManPlusPS/2, GlidePointPS/2, NetMousePS/2, NetScrollPS/2, BusMouse, SysMouse, WSMouse, USB, Xqueue. 

I've tried it as ps/2 and explorere ps/2


going on this should i be trying it as micro$oft i assue? :)

---

### Post by rainwalker on 2008-02-20
Well for me, my middle mouse button (the scroll wheel) is named Button2, I guess you could try that

---

### Post by kristjans on 2008-02-20
Home now ;)
Copied my relevant part of xorg.conf to Google and found that:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

BTW, it's kind of difficult (not impossible!!!) to get things working without knowing what they are exactly.

---

### Post by kelots on 2008-02-20
yeap gone through that and got my back/forward working

just cant re map the middle mouse button

---

