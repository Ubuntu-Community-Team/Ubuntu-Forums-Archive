---
title: "LCD black text on light background issue"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Långlykta on 2007-08-26
Helo.

I recently got my first linux distribution running on my machine - xubuntu 7.0.4 or so, and while I've gotten a few basic things to work, so far, one of the main malfunctioning things is this:

My screen (Eizo L550 , 17" LCD) 's ability to show black characters on light background. It's a rather subtle thing that I've seen before but I cannot remember what affects it. 

It's..like this: When I look closely at the letters of the topic titles the similarity-suggester brings up above this part of the browser window, in particular at the word 'blinking', the first part of the b (the vertical line) looks like its side is coated with light green, and there is green on the right side of the l, on the right side of the i, and pinkish red on the left side of the right part of the n, - etc. It's a bit like looking through '3d glasses' although of course nowhere near as pronounced.

In Settings- display, I get different resolutions. (I don't know how to check what my current one is, because it's set to 'default' , and whatever else I choose (like 1280*768) decreases the resolution, so I'm guessing 'default' is 1280*1024). All are @60Hz. I changed my /etc/X11/xorg.conf file's 'section "Monitor" to: 
Section "Monitor"
        Identifier      "L550"
        Option          "DPMS"
        HorizSync 31.5 - 64.0
        VertRefresh 59.0 - 69.71
EndSection

In order to try and make other refresh raters available, but that  made no difference whatsoever to the options in the settings->display panel.

I haven't found any drivers or so for this display for linux.

I am as evident all new with this and would of course greatly appreciate any hints :)

Edit. My graphics adapter is a radeon x800xl (default driver).

---

### Post by sumguy231 on 2007-08-26
I think a good place to start would be to find the section for subpixel hinting on the font settings (should be under antialiasing) and play around with that. Full+RGB works OK for me.

---

### Post by Långlykta on 2007-08-26
Well, thanks a bunch : )

That has solved it.  Somehow..

I can't remember what the default setting was for Hinting and Sub-pixel hinting, but I know the issue didn't affect the desktop icons. Now, I can only reproduce it in say Firefox and wordsheets if I turn hinting off, and sub-pixel hinting on, and then it affects the icons on the desktop too :p

Either way, using just hinting, or hinting+sub-pixel hinting appears to have done it. Again, thanks!

---

