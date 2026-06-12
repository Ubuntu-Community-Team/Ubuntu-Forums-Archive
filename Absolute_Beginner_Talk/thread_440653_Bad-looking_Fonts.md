---
title: "Bad-looking Fonts"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-05-11
I've noticed Firefox displaying fonts poorly with certain websites. Primarily gmail and ubuntuforums give me really bad-looking fonts. I use 915resolution with 1400x1050 resolution, if that plays a role in this issue.

I've tried dragging in tahoma and other fonts into "fonts:///", but that does nothing for the issue. I've also tried different options in the font properties to no avail.

I appreciate any tips!

---

### Post by Bachstelze on 2007-05-11
```
sudo apt-get install msttcorefonts gsfonts-x11
```

---

### Post by shanepardue on 2007-05-11
I failed to mention I've done that already also. Thanks!

---

### Post by kerry_s on 2007-05-11
set the fonts in edit> preferences> content and uncheck the let web sites choose there own fonts.

---

### Post by Bachstelze on 2007-05-11
That's weird, though, I have that box checked and my fonts look normal here or on gmail...

---

### Post by shanepardue on 2007-05-11
> **HymnToLife said:**
> That's weird, though, I have that box checked and my fonts look normal here or on gmail...
Yeah, my desktop looks fine also. The working desktop is nvidia with a CRT and the offending screen is an lcd on a laptop with an intel card. It looks fine in windows (i am forced into for work).

---

### Post by st33med on 2007-05-11
Is the font way too small? In Firefox, ctrl-scroll and it will resize your text. However, if it is a pure font problem, go to Edit-> Preferences then go to the Default Fonts tab and have the tab empty.

Hope that helped.

---

### Post by shanepardue on 2007-05-11
> **st33med said:**
> Is the font way too small? In Firefox, ctrl-scroll and it will resize your text. However, if it is a pure font problem, go to Edit-> Preferences then go to the Default Fonts tab and have the tab empty.

Hope that helped.
It's not a size issue, but how do you make the font tab empty? I'm not following you.

---

### Post by st33med on 2007-05-11
I do believe that there is a place when you click on the drop down tab, it is empty.

Meaning when you click it and it drops down, it has a completely empty spot at the top. That's my setting currently, anyway.

---

### Post by luckykar on 2007-05-11
Have a look at this thread in the debian forum , 

[http://www.linuxquestions.org/questions/showthread.php?p=2586211#post2586211](http://www.linuxquestions.org/questions/showthread.php?p=2586211#post2586211)

works wonders here i have mine setup the same and all is looking very nice.

---

### Post by shanepardue on 2007-05-11
I appreciate the link, but it seems a little too different for my liking. However, with LCD smoothing, it helps a little so it's at least readable.

Any other suggestions?

---

### Post by Gen2ly on 2007-05-11
make sure you don't have adobe 100dpi and 75dpi fonts installed, they are non-kerned.

---

### Post by shanepardue on 2007-05-11
Here's a screenshot to show just how bad it looks. (if you can tell from this pic)
[http://img.photobucket.com/albums/v330/shanepardue/screenshot2.png](http://img.photobucket.com/albums/v330/shanepardue/screenshot2.png)

---

### Post by Bachstelze on 2007-05-11
It looks well enough to me, you're a bit of a perfectionnist :p

---

### Post by shanepardue on 2007-05-11
Oh maybe it's my screen then because it looks horrible..I did change the pic once..did you see a pic of gmail logged in or the "gmail is a new kind of webmail..."

---

### Post by Bachstelze on 2007-05-11
It's the "gmail is a new kind of webmail blah blah blah".

---

### Post by shanepardue on 2007-05-11
You are absolutely right..this is a screen issue not a font one. I checked the picture on my desktop and it looks perfectly fine there. I wonder if it has to do with 915resolution forcing a resolution that windows handles, but ubuntu didn't by default.

---

### Post by shanepardue on 2007-05-11
> **st33med said:**
> Is the font way too small? In Firefox, ctrl-scroll and it will resize your text. However, if it is a pure font problem, go to Edit-> Preferences then go to the Default Fonts tab and have the tab empty.

Hope that helped.
Also, I wasn't able to make the tab for default font empty. my desktop already has it empty..not sure if that can be done or if it matters.


:edit - Epiphany has the same problem..can't be my firefox settings.

---

### Post by kerry_s on 2007-05-12
What font is that?
Taking a closer look at the font, it looks like a non-aliased font.

Did you try running->

sudo dpkg-reconfigure fontconfig-config

autohinter
always
no

---

### Post by shanepardue on 2007-05-12
I hadn't before, but it didn't help the situation here. I really appreciate the research you did on that screenshot. I'm not sure how much that pic helps, but I'd like to have a decent-looking font throughout the system and not just in certain areas and I'm running out of ideas.

---

