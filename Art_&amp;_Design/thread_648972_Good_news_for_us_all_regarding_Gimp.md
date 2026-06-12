---
title: "Good news for us all regarding Gimp"
date: 2007-12-24
forum: Art &amp; Design
---

### Post by BLTicklemonster on 2007-12-24
New user interface in the works, which should calm some people:

> **Some aims for GIMP 2.6**

2007-12-20 01:56:58

We've listened to a German podcast with one of gimps main developers, Sven Neumann, today, have searched the web and read all the mails of the developers mailing list. Although the roadmap for GIMP 2.6 is not yet finalized it is already clearly visible what GIMP 2.6 aims for. Below we've listed some of the top goals the devlopers want to achieve with the next version:

There are two main parts in the 2.5 developement branch that is being worked on: the GIMP's internal core and the graphical User Interface. 2.4 already has set the course for the future of GIMP and so does GIMP 2.6. By connecting and replacing some GIMP core code with the advanced "Generic Graphics Library" (GEGL - [http://www.gegl.org](http://www.gegl.org)), which will be a long and difficult process, the developement team sets the course for future non destructible image manipulation capabilities in GIMP.

For those that don't have a clue what GEGL is / can do - here's a short example: GEGL offers graph based non destructible image manipulation - which means following: original pixel regions are not being altered by a certain operation. assume you're doing a color correction on a photo, then you work another hour on that photo appliing lots of other filters. After all operations you can still change the first color correction operation because the original pixel information has not been altered. You don't have to redo all the steps or go back in the journal.

The second main point being worked on is the user interface. One of the most annoying things for lots of users is the many windows you've to deal with when working with GIMP, it sometimes just interrupts the workflow. The developers are trying a solution where tools and other windows can 'dock' at the main image window. Finally it should be then possible to have only one window open in the task bar, which make life easier for many of us. This is the goal. We're all anxious to see the developement on this!

From a user perspective of view we shouldn't expect too many 'visible' changes when GIMP 2.6 arrives. Because of the implementation of GEGL much code has to be rewritten for the future, which will take most of the developement time.

Nothing final yet but here are some other things that will be also worked on: It is planned to make the IWarp filter a tool, "smudging" will be accessible from all paint tools and the jitter functionality will maybe also be available from the paint tools.

The vector layers will probably not make it into the 2.6 release, also it is unclear if 16bit colors per channel support or native CMYK support will make it into the next release but we can at least hope for it ;-)

The upcoming stable versions are aimed to be released in a 6 months cycle. The dev-team wants to do more smaller steps than only a few big ones. That has been decided to bring the new features faster to users. So that means for us we can expect GIMP 2.6 somewhere in late spring / ealry summer - ah, and thats 2008 not 2009 of course, heh ;-)

from here: [http://www.gimpusers.com/news/2007-12-20/gimp-2-6-aims.html](http://www.gimpusers.com/news/2007-12-20/gimp-2-6-aims.html)


With a 6 month release cycle, this looks good for us all.

---

### Post by z0mbie on 2007-12-24
Compiz + Current Gimp GUI is excellent. Compiz completes Gimp. I hope they leave the old/new GUI as an option,

---

### Post by BLTicklemonster on 2007-12-24
I hope they leave it as an option, also, as I like things the way they are. Compiz and the current gui... what do you mean? Does this do something different? Can you post a screenshot if it does?

---

### Post by Half-Left on 2007-12-24
Gave in to the Photoshop UI nazis most lightly.

---

### Post by SOULRiDER on 2007-12-24
I do prefer the phosohop UI a lot more, but maybe its because i learned photoshop and got used to it.

---

### Post by Samhain13 on 2007-12-24
> Compiz + Current Gimp GUI is excellent. Compiz completes Gimp. I hope they leave the old/new GUI as an option,

+1 here. I like it the way it is and I'll certainly be choosing this as the default. :)

---

### Post by omega_user on 2007-12-25
Well, the current UI, is nice, but a rework to make it clean and nice like photoshop would be nice.  Also, the startup screen needs to be remade to look really nice, like the Adobe Photoshop Feather.

Features to Work In:
Built in cascading menus for layers, color tools and filters, etc.
The new start screen
Unified look and feel

---

### Post by BLTicklemonster on 2007-12-25
I started out with Paint Shop Pro, then moved on to Photo Shop, took some classes in it, then started learning the Gimp, and quite honestly, I prefer the Gimp's layout.

---

### Post by smartboyathome on 2007-12-25
By the way, one thing I would really like to see in GIMP is a single-window mode where the main window folds back into the side and can be opened by clicking on a very small bar on that same side (ie, see the side pane for Opera). This would make photo editing much easier for me (since I don't have to switch windows all the time just to switch a layer).

---

### Post by omega_user on 2007-12-25
> **BLTicklemonster said:**
> I started out with Paint Shop Pro, then moved on to Photo Shop, took some classes in it, then started learning the Gimp, and quite honestly, I prefer the Gimp's layout.

well, I don't mean like make it a totally new layout, just fix up the current layout so it works better.  The only real change I want is easier access to things to help with layers and colors, maybe like an optional feature that enables a drawing board mode, sort of like photoshop's all inclusive feel.  Of course that'd be easy to just have a button that enables that, and just pops up all the helpful little boxes around the piece you're doing. That feature, I feel, is something Photoshop did well.  Smartboy's idea would be nice too, just do something that gives u a chance to remove the hassle

---

### Post by digitalis_vulgaris on 2007-12-25
I'm disappointed. The most important feature for this kind of application is set on "we shall see about that... maybe one day..." . All people resources in gimp development team should work on CMYK. This is the only mayor feature Gimp don't have!

I really don't understand what is going on with GIMP!?

---

### Post by BLTicklemonster on 2007-12-25
Years ago I got some c programming thing that had borland something (I'm old, can't remember specifics, so just nod like you know what I'm talking about, and eventually I shut up) and I remember making a text editor in it. Now seeing how that is done, I don't see why no one has done several things, like take gimp and create a whole new gui out of it, or maybe take the steps involved in setting up a network (see my sig) and make a gui out of it, either. Surely there's something in linux to program where you have everything out there in the open, place buttons, and assign them tasks or whatever, right? Shame no one has made some programming software like this where you can have the editor up and the program you want to make a gui for open, too, and just click in the editor whatever button you want to assign, then go to the actual program you're making a gui for, and click a button, and ... well, now I'm off topic for sure. Anyway, I'm surprised no one has come up with a totally different gui for gimp already. Makes me wish I had a longer attention span. Hey look, a shiny object!!!

---

