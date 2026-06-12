---
title: "Ballon Tutorial for Blender"
date: 2011-10-28
forum: Art &amp; Design
---

### Post by Radical_Dreamer on 2011-10-28
Okay, very recently I downloaded Blender off there site (not ubuntu software center) and have started watching the tutorials but now, I am facing difficulties on the one on making ballons with link here

[http://cgcookie.com/blender/2010/11/04/creating-a-bunch-of-balloons/](http://cgcookie.com/blender/2010/11/04/creating-a-bunch-of-balloons/)

Now, some things I noticed don't seem to work.
First, I don't know how he deselects stuff.  I notice he has it on the bar to the left but I don't so I don't know.

Second, he says to use alt right click but that doesn't seem to work for me (I get a window asking about minimizing, maximizing, moving etc) and what's control space because I only get a small window from my clicker also with things like find missing files, move down modifier, make parent and such).

Further control r is supposed to add rings to the image but it doesn't do anything different from just r (ie rotate)

Also, I am using version 2.60a

And also, I don't understand what he means when is talking about extruding at the 3 minute mark.

---

### Post by Radical_Dreamer on 2011-10-28
Now that I am playing around more with it, I don't think the control key is working for this or at least not correctly because the hotkeys that are supposed to do certain things either don't work or they do something that isn't supposed to like control up arrow doesn't make fullscreen it just makes a box that says something on frames

---

### Post by Radical_Dreamer on 2011-10-28
Apparently this has something to do with Linux it turns out

[http://www.blender.org/education-help/faq/linux/](http://www.blender.org/education-help/faq/linux/)

It says

Until the time comes when all Blender hotkeys are user configurable, your only choices are going into your Window Manger configuration and disabling or re-directing the offending hotkey; or trying to substitute the troublemaker hotkey with it's GUI counterpart (witch is not always feasible).

 

To access KDE's hot-key editor go into Control Center -> Regional Settings and Accessibility -> Keyboard Shortcuts

 

A special note should be made about the ~ hotkey (the one that toggles all your layers on/off). If that hot key isn't working for you, the Window Manager is not the one to be blamed, but your keyboard configuration:

 

For some non standard English configurations, that key is used as a modifier to input Latin characters, specially the &#65533; letter (ascii codes 164 and 165) used often in the Spanish language (like in "Pi&#65533;a Colada"). On those keyboard configurations, the ~ key event isn't treated as a keystroke on itself, but like a modifier for the next key that you press. Again, besides changing your keyboard configuration, there isn't much that could be done to fix it.

But I don't know what or how to go about fixing because I don't find any that disagree with the commands I've been putting into the program

---

### Post by Radical_Dreamer on 2011-10-29
So actually, the solution is going into compiz, then selecting the windows move one and just disabling it.  that helped me a lot.

---

