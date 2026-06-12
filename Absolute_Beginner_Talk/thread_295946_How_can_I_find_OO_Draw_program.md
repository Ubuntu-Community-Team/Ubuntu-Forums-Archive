---
title: "How can I find OO Draw program"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-11-08
Hi
 When I go to ADD/Remove Applications I see OO Draw but when I go to Applications > Office OO Draw does not show up. How can I get it to show up so I can use it?

OO Draw also shows up as installed in Synaptic.

Thanks

---

### Post by dbott67 on 2006-11-08
Right-click the APPLICATIONS menu and select EDIT MENU.  Browse to the APPLICATIONS > OFFICE and place a checkmark in the OO Drawing.

-Dave

EDIT:  Sorry, you are right... make the Right-click the APPLICATIONS menu and select EDIT MENU.  Browse to the APPLICATIONS > **GRAPHICS** and place a checkmark in the OO Drawing.

---

### Post by That_Geek on 2006-11-08
ok, in the menu go to accessories--> al acarte menu editor ---> office --> click the square and select it and voila you have OOo draw

---

### Post by kent41 on 2006-11-08
> **dbott67 said:**
> Right-click the APPLICATIONS menu and select EDIT MENU.  Browse to the APPLICATIONS > OFFICE and place a checkmark in the OO Drawing.

-Dave

dbott67
Only OO Spredsheet, OO Write, OO Presentation showup.

BTW Im using 6.10

---

### Post by That_Geek on 2006-11-08
> **kent41 said:**
> dbott67
Only OO Spredsheet, OO Write, OO Presentation showup.

BTW Im using 6.10

oh snap!

its in graphics, not office, sorry bout that

---

### Post by kent41 on 2006-11-08
> **That_Geek said:**
> oh snap!

its in graphics, not office, sorry bout that

Yes that works thanks for the help from all.
Kent

---

### Post by kent41 on 2006-11-08
Ok is there a way to put OO Draw with the other OO applications in Office?

---

### Post by dbott67 on 2006-11-08
Yes... just make note of the PROPERTIES of the program in the GRAPHICS menu by right-clicking it & selecting PROPERTIES.  Next, HIGHLIGHT the new submenu, select FILE > NEW ENTRY and create a new entry with the following parameters:

NAME: OpenOffice.org Drawing
COMMENT: Create and edit drawings, flow charts, and logos by using Draw.
COMMAND: ooffice -draw %U

---

### Post by That_Geek on 2006-11-08
> **kent41 said:**
> Ok is there a way to put OO Draw with the other OO applications in Office?

yes, in the menu editor, just drag DRAW into the office tab make sure its clicked and you are done

---

### Post by kent41 on 2006-11-08
> **dbott67 said:**
> Yes... just make note of the PROPERTIES of the program in the GRAPHICS menu by right-clicking it & selecting PROPERTIES.  Next, HIGHLIGHT the new submenu, select FILE > NEW ENTRY and create a new entry with the following parameters:

NAME: OpenOffice.org Drawing
COMMENT: Create and edit drawings, flow charts, and logos by using Draw.
COMMAND: ooffice -draw %U

I don't see that option in Edgy 6.10 it does not show properties, It only shows add to panel and add to Desktop with right click on OO Draw

---

### Post by kent41 on 2006-11-08
Dave and That_Geek

Boy what a ride that was a trip to you know where.

First I tried to Drag and drop that did not seem to do anything (but it was but they just did not show up right away) 

So I tried to add a new entry that did not seem to do anything ( but it was)

Then the system crashed and I got a BUG window.

I re-booted and and wala I had 2 Draw pgms in OO and eight (8) in the editor and I could not delete any of them.

Then They started going away and I now have only 1 OO Draw in OO.
For some reason it was taking minutes to implement the changes.

Boy Thanks :)

---

### Post by Peepsalot on 2006-11-08
inkscape is better IMO :p

---

### Post by kent41 on 2006-11-09
Thanks Peepsalot

Ink was the drawing package I was looking for - There are just too many applications to choose from.

Thanks

---

### Post by Peepsalot on 2006-11-09
> **kent41 said:**
> Thanks Peepsalot

Ink was the drawing package I was looking for - There are just too many applications to choose from.

Thanks
Hehe, I actually had never used the OO drawing program till I saw this thread.

I gave it a try just to see what it was like.  I had some prior experience using inkscape... in windows :-#.  I only played with the OO drawing app for a short time but it didn't seem to really have the same polish as inkscape.

Then again, it may be a case where the two projects are not really aiming for the same goals. The OO drawing app save options are in a bunch of formats I haven't heard of, so I'm not even sure if they are raster or vector formats.

I just know that inkscape is vector, which is nice for drawing, and can always be converted to raster when needed.  I like SVG :D

Anyways, glad I could help.

---

### Post by msimon1960 on 2007-02-24
I'm having a similar problem except that Synaptic and the Add/Remove Applet say the program is installed -- but it doesn't have a launcher on either the 'Graphics' or 'Office' menus.

I used the instructions above to create a launcher -- thanks for the syntax!

Matt.

---

