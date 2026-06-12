---
title: "Title-bar too large with gutsy (with compiz)"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by superimad on 2007-10-26
I just installed gutsy from scratch. I installed compiz-fusion with it. Also XGL. I have ATI X1400 video card on a DELL 6400.

I do not have emerald or beryl installed because as I understand it, compiz-fusion should be the combination of beryl and compiz.

Problem: I have unusually large window title-bars (font AND buttons - close, maximize, minimize). I tried my best to shrink them, but I can't find a way.

I prefer not to install things I don't need, so not having to install emerald JUST for this issue would be preferred, especially that as I understand it, it should work without...

thanks for the help

---

### Post by speed145a on 2007-10-26
Same problem for me when I installed on my mom's PC.  The login window is really messed up as well with the size looking stretched and the username being HUGE when typed.

I have tried another video card and it still does it.
Only thing I can think to note is that her monitor resolution is only a max of 1024x768, and that it is not the newest computer in the world

---

### Post by SunnyRabbiera on 2007-10-26
attempt to change your resolution with:
system> preferences, then to "screen resolution"
that might help.

---

### Post by superimad on 2007-10-26
my screen resolution is 1680X1050. the fact that the title-bar is large is not related to the resolution i believe...

what to do....!!?

---

### Post by superimad on 2007-10-26
short of a good answer, it'd be a good idea if anyone knows where the information on 
- title-bar font
- title-bar icon size
is stored. Changing it in that file would probably work great.

if anything I've said doesn't make sense, please do point it out. I know nothing of linux or ubuntu

---

### Post by Starks on 2007-10-26
Change the DPI back to 96.

---

### Post by superimad on 2007-10-26
How do I do that?

---

### Post by superimad on 2007-10-26
mind you, everything else looks just fine. the problem only resides in the title-bar.

it looks like it is the natural design, but i know enough to know that it isn't, it really is too big.

---

### Post by pashashome on 2007-10-26
Check this link out...see if it helps.

[http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login](http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login)

---

### Post by sailor2001 on 2007-10-26
sudo dpkg-reconfigure -phich xserver-xorg    set your resolution to a higher value. I use 1280x1024 whereas I usually use 1024-768

---

### Post by superimad on 2007-10-26
Thanks pashashome that did the trick!  and it also fixed my login window font!   :)

my apologies for the repost, but I included "title-bar" in my search and never came across that thread.

Thanks again.

---

### Post by SpookyET on 2008-01-04
I have the same problem. It's not the resolution, nor the DPI.
My resolution is 1680x1050 at 96DPI.

When I login, I get huge titlebars. When I go to Appearance > Visual Effects and select "NONE," the titlebar font resets to the proper size.

Then I set the visual effects back to "CUSTOM." The titlebar font size remains at the proper size, and it will stay at that size until the next FULL restart at which point The process has to be repeated.

I would love to know what's causing it.

---

### Post by beniji on 2008-01-08
@SpookyET - yep that fixes it for me too (gutsy x86) - disable then re-enable 3d effects.

---

### Post by SpookyET on 2008-01-08
> **beniji said:**
> @SpookyET - yep that fixes it for me too (gutsy x86) - disable then re-enable 3d effects.

[http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login]("http://ubuntuforums.org/showthread.php?t=575978&highlight=huge+fonts+login") fixed it for me.

---

