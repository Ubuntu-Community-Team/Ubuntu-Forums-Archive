---
title: "[SOLVED] why is evetything so small?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-22
I've been a windows user for many years and I've only just switched to ubuntu feisty. There are a lot of things I can't figure out, and here's one:
Everything - and I mean pretty much everything is really small in ubuntu! It may sound ridiculous but it's making work difficult.
The font on websites is really small by default - for instance, in windows xp, my gmail inbox showed up in a normal, readable size but now its miniscule to the point of being unreadable. (I can increase that temporarily using the view menu, but how do I do it permanently?) Same is the case with all websites - all content is tiny. Sometimes it doesn't even fill up the whole window and leaves a good bit of space on the sides or bottom blank.
Even other things - like pictures - are smaller than they used to be in windows.
How do I fix this?
Thanks.

---

### Post by Verlaine on 2007-07-22
Is your screen resolution set higher than it was in windows perhaps?

Go to preferences>screen resolution and see if it is higher than your windows setup.

---

### Post by Gannin on 2007-07-22
Have you installed the msttcorefonts package to make web pages display a bit better?  Also, in Firefox, go to Edit > Prefrences > Content > Advanced and set a minimum font size of something like 12.

---

### Post by kleo skywalker on 2007-07-22
> **Verlaine said:**
> Is your screen resolution set higher than it was in windows perhaps?

Go to preferences>screen resolution and see if it is higher than your windows setup.

er... I don't remember what it was in windows. I just tried a lower resolution, and things did get bigger but now the whole screen is smaller than my monitor and I can't fit it properly manually. What next?
Thanks

---

### Post by forestpixie on 2007-07-22
Have you tried changing font size in system>preferences>font ?

---

### Post by kleo skywalker on 2007-07-22
> **forestpixie said:**
> Have you tried changing font size in system>preferences>font ?

I'm on the absolute beginner forum but uh... that's the first thing I did after installing feisty.

---

### Post by ddrichardson on 2007-07-22
<CTRL><+> increases font size in Firefox - send a screenshot to show exactly what you mean

---

### Post by armandh on 2007-07-22
if the resolution that has the desktop items sized to your preference leaves the display slightly undersized on the monitor try the monitor adjustments?

---

### Post by kleo skywalker on 2007-07-22
CTRL+ is temporary, and for the current tab only - I want a permanent fix.
Screenshot attached (default resolution).
I tried a lower resolution and I can't get the screen to fit the monitor properly using the monitor settings.
What next?
Thanks.

---

### Post by ddrichardson on 2007-07-22
OK, System/Preferences/Font will set the font sizes within the window manager.

Edit/Preferences/Content under Firefox can set the default font size, but with many websites using a specific font size you need to click advanced and untick the box about pages setting their own font sizes.

When you say a lower resolution wont fit your monitor - do you mean you cant use the monitor controls to adjust the picture to fit the screen, or do you mean only a part of the screen is displayed (viewport).

---

### Post by forestpixie on 2007-07-22
How are your fonts set in firefox?

unchecking the "allow pages to set their own fonts" helped me - as did changing fonts about.

---

### Post by ddrichardson on 2007-07-22
Sorry just noticed the image size you posted is 1280x1024 - what size is your monitor?

---

### Post by Verlaine on 2007-07-22
Is it too big or too small for the monitor. 

BTW what was your screen resolution originally and what did you change it too?

Try setting it to 1024x768

---

### Post by kleo skywalker on 2007-07-22
The screen resolution is 1280x1024 by default.
I changed it to 1024x768.
My monitor is 17 inches.
I've adjusted the monitor settings and the screen fits the monitor ok - not snug but works.

---

### Post by Verlaine on 2007-07-22
That was your problem 1280x1024 is too high a resolution for a 17 inch monitor.

---

### Post by mlentink on 2007-07-22
Interesting. Why do you say that 1280*1024 is too high for a 17"?

---

### Post by pyros on 2007-07-22
> **mlentink said:**
> Interesting. Why do you say that 1280*1024 is too high for a 17"?

because eyestrain causes blindness... and because many 17 inch crts were never intended to run that high a resolution.

---

### Post by Verlaine on 2007-07-22
1280x1024 is at the bottom end of useability for 17 inch monitor but many users (like the one who started this thread) will think it looks too small. Especially if they are used to running at 1024x768 as I suspect he was in windows.

It's also worth bearing in mind that most web site designers optimise their pages for 1024x768 as it is the most common resolution.

---

### Post by kleo skywalker on 2007-07-22
I think my screen looks workable now, thanks everyone.

---

