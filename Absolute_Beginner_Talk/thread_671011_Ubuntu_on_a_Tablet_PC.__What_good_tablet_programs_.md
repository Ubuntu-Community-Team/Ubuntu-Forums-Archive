---
title: "Ubuntu on a Tablet PC.  What good tablet programs are there?  Screenclip is a must."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Mysticle31 on 2008-01-18
I've got and older M275  1.5Ghz Centrino that works just beautifully with Ubuntu.

I've played with many of the notetaking apps I've read about and really like Xournal.  It's lacking some features of OneNote but very promising.  I plan to try it more.  One note could still remain my default though.  I'll have to try launching it seamlessly in a trimed down XP VM.

I'm looking for other programs.

I already know of xstroke.  Is there any others that offer recognition?

Is there anything close to a:

TIP replacement?  Character Recognition?


How about an on screen keyboard?  I'm trying GOK as I write this.  It has some issues I need to fix in order for it to work right.  None of the buttons do anything right now.  Probably something to do with that "device controlling GOK is also controlling system pointer" message I received when starting it.

How about a screen clip tool where I can select an area of the screen to "clip" and save it as a jpg or paste it into a document?

Any ideas how I can make the rotate screen button work?  Maybe though a compiz-fusion plugin I don't know about?  I've read that you can edit xorg.conf for the Nvidia GPU tablet.  I have an Intel, and the famous shutdown problem that goes with it :)

---

### Post by LeAstrale on 2008-01-18
i actually dont think that there is that many apps for tablet notebooks YET. however it would be nice to see some in the future. 

How well does Ubuntu handle your tablet pc by the way? (im very interested in that)

---

### Post by Mysticle31 on 2008-01-20
Quite well. 

The basic digitizer functions (moving the cursor, left click, right click, pressure sensitivity) worked with a modification of xorg.conf.

I uncommented all the things that say uncomment if you have a wacom tablet

And I added this to the wacom input device section
# Added for pressure
	Option		"PressCurve"	"50,0,100,50"
# Added for rightclick
	Option		"Button1"	"1"
	Option		"Button2"	"3"


I'm interested in getting more info on some kind of on screen keyboard, screen rotation, and a screen clip program.

---

### Post by solar george on 2008-03-16
Cellwriter
[http://risujin.org/cellwriter/](http://risujin.org/cellwriter/)

---

### Post by bcw on 2008-03-25
> **Mysticle31 said:**
> 
Is there anything close to a:

TIP replacement?  Character Recognition?


How about an on screen keyboard? 

I use XVkbd.  I modified the 'fitaly' layout, and the slides are quite helpful.  Search for my posts for details.

I am working on the TIP replacement.  Don't expect anything for a month or two.

Cheers,
Bret

---

