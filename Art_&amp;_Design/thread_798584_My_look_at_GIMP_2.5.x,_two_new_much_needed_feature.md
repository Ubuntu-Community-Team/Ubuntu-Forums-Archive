---
title: "My look at GIMP 2.5.x, two new much needed features"
date: 2008-05-18
forum: Art &amp; Design
---

### Post by Half-Left on 2008-05-18
I've just compiled GIMP 2.5.x branch I thought I'd share with you some of the new features already implemented.

**User Interface**

One of the main issues people talk about with GIMP is the default layout and window management, tool and layer palettes have their own window, well not any more. GIMP 2.5.x already has the option to put everything into one window, a real deal maker for most who are used to applications like it (Photoshop ect..) 

The toolbox now has a nice GIMP image behind it instead of a menu bar for options, it's much cleaner.

2.5.x window setup
[[IMG]http://img178.imageshack.us/img178/6391/gimp25uiex2.th.png[/IMG]](http://img178.imageshack.us/my.php?image=gimp25uiex2.png)

**GEGL**

Some of the features I miss or you my know in Photoshop is a ability to add layer effects like dropshadows, glows and bevels onto the layer and adjust them in real time. GIMP 2.5.x now has this sort of options, there is nothing worse then having to guess at adding a shadow and then having to adjust it on it's own layer, thankfully 2.5.x does this like layer effects now which is much easier to manage.

It's rather slow at the moment but I'm sure speed will pickup in later development. These two features alone should get more attention for GIMP as a Photoshop alternative and are much needed. 

GEGL at work
[[IMG]http://img134.imageshack.us/img134/5915/gegldropshadowym0.th.png[/IMG]](http://img134.imageshack.us/my.php?image=gegldropshadowym0.png)

You better get ready for GIMP 2.6, it's going to be a real awesome release. :guitar:

---

### Post by exploder on 2008-05-18
Now that is nice! Thanks for pointing out the new features and the screenshots. I like the ability to have everything in one window, very nice!

---

### Post by pkkid on 2008-05-18
This is great news.  These two things are probably the two biggest things I struggled with when trying to replace Photoshop for Gimp.  It's good to see they are starting to impliment features that people have been suggesting. :)

---

### Post by days_of_ruin on 2008-05-18
Nice!When will it be in the repo?

---

### Post by Half-Left on 2008-05-18
> **days_of_ruin said:**
> Nice!When will it be in the repo?

You'll have to wait until someone works out a deb for it along side 2.4 or you'll just have to compile it. It's only the first release of the 2.5.x branch, a long way to go for stable 2.6 release.

---

### Post by Sordelka on 2008-05-19
Nice new features.

---

### Post by NeonBible on 2008-05-19
I hope this is not a stupid question but how do I get this version running on Mac OS X?

---

### Post by Twitch6000 on 2008-05-19
This is good news but,I like having multiple windows :).

---

### Post by jpeddicord on 2008-05-19
*drools

Thanks for the preview there. I'm definitely looking forward to this release more than any other just because of Layer Effects.

---

### Post by Half-Left on 2008-05-19
> **NeonBible said:**
> I hope this is not a stupid question but how do I get this version running on Mac OS X?

Unless they build it for OS X you can't, dev versions are only available as source so you'll have to wait for a 2.6 installer.

---

### Post by jpeddicord on 2008-05-19
> **Half-Left said:**
> Unless they build it for OS X you can't, dev versions are only available as source so you'll have to wait for a 2.6 installer.

Technically GIMP could be compiled from source for Mac, but not without a hassle, such as the Mac X11 debacle.

---

### Post by lyceum on 2008-05-19
The second thing looks awesome. As for the "all in one window" PhotoShop IS just like GIMP (multiple windows) on a Mac. I think it is nice they did that for PC users, but really there are more important things they could work on. Thanks for the info though

:popcorn:

---

### Post by Genius314 on 2008-05-19
Wow, that's great. I was just searching today for a way to group the GIMP windows together (it's a pain minimizing them all separately). Now I don't have to! :D

The second feature isn't all that important to me. I've gotten too used to doing all the shadows and glows and stuff manually (even in Photoshop)... much more configurable, IMO.

---

### Post by jcornuz on 2008-05-20
Hi there,

Regarding 1) I think the Gimp people want to support both (everything in one window and multiple windows).
Regarding 2), this is just the beginning of what GEGL integration will offer: effect layers, more bit depth support, better color management and eventually "non destructive editing".
But there is no time frame yet and features will appear gradually over the next versions.

Have a looks at Peter Sikking's presentation at LGM (Gimp UI) and Øyvind Kolås (GEGL) if you haven't already:

[http://media.river-valley.tv/conferences/lgm2008/quicktime/0302-Peter_Sikking.html](http://media.river-valley.tv/conferences/lgm2008/quicktime/0302-Peter_Sikking.html)

[http://media.river-valley.tv/conferences/lgm2008/quicktime/0104-Oyvind_Kolas.html](http://media.river-valley.tv/conferences/lgm2008/quicktime/0104-Oyvind_Kolas.html)

Take care,

Joël

---

### Post by ad_267 on 2008-05-20
> **Twitch6000 said:**
> This is good news but,I like having multiple windows :).

I'm pretty sure you can still have the multiple windows if you want, but now you have the option to dock them in the main window. Is this correct? I've downloaded the source but haven't got around to compiling and having a play yet. :)

---

### Post by Half-Left on 2008-05-20
Effectively it works similar to Photoshop in OS X, you have a option to minimize the canvas window or all of them together.

---

### Post by vishzilla on 2008-05-20
Its been long time since I've used Photoshop. Gimp is really improving with each release and I am looking forward to 2.5

---

### Post by Colonel Kilkenny on 2008-05-20
I sure hope those screenshots are very much work-in-progress. Just to make few points.
1) "Use GEGL" in toolbox - nobody understands / knows what is GEGL, but pretty much everyone wants to use it (or there shouldn't be any reason why not to use it). This is perhaps just because development is very much in progress.
2) "GEGL Operation" - once again "GEGL", get rid of it as nobody has any idea what that means.
3) GEGL Operation -dialog:
 - Seems to be quite simple with dropshadow (and it should be just plain Shadow or something, nobody, I repeat, nobody, is interested knowing what is the name of script file which produces that effect), maybe too simple?
 - How do you manage your layers "GEGL Operations"? (If it isn't possible to use multiple "GEGL Operations" on one layer then the whole thing is totally useless). Effects must be at least grouped effectively and all of them should be behind one dialog. 

As a positive note: finally something is happening with GUI and at least they seem to be fixing GIMP. Whether they succeed in it is a totally new question.

---

