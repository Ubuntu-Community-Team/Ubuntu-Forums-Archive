---
title: "Text size too big inn applications (Gnome)."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Ba|der on 2006-10-15
I have a laptop with screen resolution 1024*768. [APPEND: KRuler says 1023*768 after some calculations from my side, due to menu-bugs for Gnome Desktop] In System-Setup-Screen resolution this shows correct.

But:
Comparing to Windows 2000 text size in all programs are terribly big, and some menues (Like advanced menues in Gaim-initial setup) is outside the screen.

So far:
* I reduced text size in Firefox from 16 to 13 in the preferences- Content menu.
* I used gconf-editor to change text size for desktop icons (apps-Nautilus-Preferences) from 10 to 8.

Problem:
All icons and all toolbars etc taking up much space in all programs, and the text too big for 1024*768 resolution.

This appears to all X/Gnome programs. Like if I start xterm from the menues all text is big. If I start another xterm from the first xterm the last xterm has normal (small) text.

Please help :)

---

### Post by Gokudan on 2006-10-15
Hi there Ba|der and you too guys!

I have the same problem Ba|der, i had to set up resolution to 1280 x 1024 at a terribly low 60Hz refresh rate

Att.
Gokudan

---

### Post by Hmarroqu on 2006-10-15
using gnome, go to system-preferences-font

---

### Post by Gokudan on 2006-10-15
> **Hmarroqu said:**
> using gnome, go to system-preferences-font

That should solve the font size, but what should Ba|der and i do to resize the GUI elements to make them smaller? Is there any way to do it rather than put a higher resolution?

Att.
Gokudan

---

### Post by Ba|der on 2006-10-15
> **Gokudan said:**
> That should solve the font size, but what should Ba|der and i do to resize the GUI elements to make them smaller? Is there any way to do it rather than put a higher resolution?

Att.
Gokudan

Thanks Hmarroqu for font size advise. I think even icons/GUI elemens were effect after restarting programs, will do some more testing...

BTW: All LCD-panels runs on 60 Hz.

---

### Post by Gokudan on 2006-10-15
> **Ba|der said:**
> 
BTW: All LCD-panels runs on 60 Hz.

Not all of them, i've seen some working at 75Hz. But in my case it is unnaceptable to work at this refresh rate since i use a Samsung 17" CRT :)

Att.
Gokudan

---

### Post by Ba|der on 2006-10-15
I understand, for a CRT 60 Hz is tiresome to look at. 

I think some GUI elemensts got smaller then I reduced the font size. But there are still some problems. In Avast scanner the text is very litle (almost unreadable and unclear) and does not change whatever font I set in the Gnome-menu font manager. Fonts in PDF'files and in documents in OpenOffice and other also have a bad shadow effect. That is the pixel-column to the left of the characters is half dark. Also characters that does not consist of solely sharp angles, (H and I is fine) the pixels is smugded a bit. I tried advanced settings, LCD, monochrome etc, but it still looks like a litle bad printout.

I found a way to all sizes, icons and text. It's under the advanced font settings and the top you can set a number for DPI. It was on 96 DPI and if reduced icons and other GUI items seem to get smaller.

APPEND:
 I found a tread about ClearType text and patent issues here:
[http://ubuntuforums.org/showthread.php?t=180647](http://ubuntuforums.org/showthread.php?t=180647)

I'll have another look at the suggested solution, but I think the smugded /fuzzy charcters might be due to the cleartype problem. At least it's very tiresome and hard to read smaller prints. The same kind of problem can be seen in Windows when showing PDF-files, but to a lesser degree.

---

### Post by Gokudan on 2006-10-17
> **Ba|der said:**
> I understand, for a CRT 60 Hz is tiresome to look at. 
I found a way to all sizes, icons and text. It's under the advanced font settings and the top you can set a number for DPI. It was on 96 DPI and if reduced icons and other GUI items seem to get smaller.


I used your advice and reduced the DPI down to 65 and now GUI elements are way smaller than before, now i can use 1024 x 768 at 85HZ :D

Att.
Gokudan

---

