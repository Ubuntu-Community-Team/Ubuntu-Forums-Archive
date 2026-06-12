---
title: "Know any good Animation Software?"
date: 2011-01-29
forum: Art &amp; Design
---

### Post by H13N.H3N on 2011-01-29
Hi, i'm very interested in software for making animations, unfortunately, sometimes FOSS solutions aren't enough/good, other times commercial solution are good, but not supported for Linux and working them via Wine may prove to be a nightmare, i want to know if some of you know a good program for the making of animations, 2D preferably, saving you some effort to mention some programs, i'll list here the ones i have tested/used:

**Pencil**

_Pros_: Works as expected, has a timeline, custom frame rate and it's under constant development
_Cons_: While easy panning/zoom with wheel mouse is becoming a standard, controls in pencil aren't that conventional, plus, has no tweening, vector layer is quite primitive and sometimes the tracing tools behave buggy on simple task such as brush color or size, even worst, is a nightmare for mouse-only users

**Ktoon**

_Pros_: A good program back in version 0.8, stood strong against other programs and was always a good option, it had the basics, drawing tools and timeline/exposure sheet, export options and things
_Cons_: It's fate is unknown now, it might get commercial or something, and the current version is unstable.

**Tupi**

_Pros_: New and fresh fork of Ktoon, it has now Motion tween and the option for use SVG graphics, and minor improvements which are nice to see
_Cons_: Very unstable, the basic tools for drawing and handling objects are inaccurate, is still beta.

**Synfig Studio**

_Pros_: Excellent quality, many ways to export an animation, nice effects and an interesting way to tweening.
_Cons_: Most users complain of it's complexity, not my case as the Documentation is for that purpose, what is giving me headaches now is that is now unusable as the speed drops near to program freezing, no one knows/care/want to hear about the cause

**Anime Studio**

_Pros_: Very interesting tool, it was and still is good since the time it was called Moho, now it even has effects simulation
_Cons_: Versions 5 and 6 were good, while version 7 is available for Mac and Win, there is no version for Linux last time i checked, also.. there is thigs little thing that annoy me about Win and Mac being better/more supported than the Linux one...
_Under Wine_: I purchased version 7 for windows to use through Wine, is impressive and things but Wine itself can't take some native work for windows, making rendering the project crash the program, also with the use of the program the speed of the program itself starts to drop

**Flash 8 (Wine)**

_Pros_: I fell in love back in 2004 when for first time i used Macormedia Flash, and used it untill i changed to Linux, using it through Wine make it work decently well.
_Cons_: Many little glitches in the user interface, Adobe versions don't install, and using flash in long projects make it slow.

**GIMP**

_Pros_: I have made little animation inside Gimp, each layer counts as frame, Gimp is an excelente piece for effects and creation of graphics itself, if someone build a timeline (Independent from the layers) for gimp let me know, that would make it perfect
_Cons_: The more layers as frames you use, the more memory it takes, natively, GAP might help on exporting the animation and natively exporting to GIF is the only way to render an animation, also Gimp doesn't export layers as png, there is a plugin for that tho.. 

**Creatoon (Wine)**

_Pros_: Interesting Cutout animation program, went free for some unknown reason, it has an excelent control over objects.
_Cons_: Some releases of Wine make it crash, some make it works flawlesly, and some updates leave it buggy... the program itself works well, but some changes in Wine itself may cause some problems.

**Styckz (Wine)**

_Pros_: A newest program for make stick animations, it has some fun options
_Cons_: No further complains than it takes huge amounts of memory via Wine, and the eternal promise of a Linux version is still showing on their download page.

**StickyPy**

_Pros_: Can natively run in Linux as it is written in Python
_Cons_: Usable and stable, but still...

**mtPaint**

_Pros_: Pixel art program (Hurray!!) which contains some nice features for the making of gifs
_Cons_: Pretty much the same with GIMP, indeed, is better exporting gifs from GIMP.

**Notes:**

I didn't tested ToonBoom! and TvPaint, i know about their existence, but seems that these need higher requirements that the ones i have, also i'm not counting 3D editors because only Blender and K-3D are worth of use under Linux, there are some outdated programs that don't run anymore in new distros, or that are abandoned, unstable, no longer maintained or unexplainable unusable, here i list some minor programs that caught my attention but for different reason aren't good options:

[B]Java Animation Studio
Animata
F4L
ganim8
Gnash[/B]

well.. hopping there are some new answer soon, greetings!

---

### Post by onilink422 on 2011-01-29
You can actually install Macromedia Flash 8 in ubuntu with wine and it works great. Unfortunately it is a paid software.
But I see you have tried that

---

### Post by prokoudine on 2011-01-30
> **H13N.H3N said:**
> Hi, i'm very interested in software for making animations, unfortunately, sometimes FOSS solutions aren't enough/good, other times commercial solution are good, but not supported for Linux and working them via Wine may prove to be a nightmare, i want to know if some of you know a good program for the making of animations, 2D preferably, saving you some effort to mention some programs, i'll list here the ones i have tested/used:

There's also [Plastic Animation Paper]("http://plasticanimationpaper.dk/").

---

### Post by H13N.H3N on 2011-01-30
> **prokoudine said:**
> There's also [Plastic Animation Paper]("http://plasticanimationpaper.dk/").

Interesting option, the downside is that can't run:

[IMG]http://img209.imageshack.us/img209/4988/18288399.png[/IMG]

---

### Post by Lucradia on 2011-01-31
> **H13N.H3N said:**
> Interesting option, the downside is that can't run:

[IMG]http://img209.imageshack.us/img209/4988/18288399.png[/IMG]

You probably can't run Flash4Linux, or its successor either. (Since both were abandoned, even though they were going to be full ports of flash.)

---

### Post by weedeater64 on 2011-01-31
:~$ acs create animation
arkhart - former world for Arkrpg
arkrpg - roleplaying kernel
libarkrpg-dev - development headers for Arkrpg
libarkrpg0c2a - shared libraries for Arkrpg
epix1 - Create mathematically accurate line figures, plots and movies
gimp-gap - The GIMP Animation Package
k3d - 3D modeling and animation system
onscripter - Visual novel games engine compatible to NScripter
piespy - An IRC bot to visualize social networks
python-gnuplot - A Python interface to the gnuplot plotting program
shoes - tiny graphics and windowing toolkit using Ruby
stopmotion - program for creating stop motion animations
worlded - world editor for Arkrpg


k3d looks interesting,
 Some of its features are:
 .
  - Record and play back interactive tutorials and macros.
  - Able to create and edit documents in multiple realtime OpenGL
 solid, shaded, texture-mapped views. You can even model, animate, and
 interact with animations while they play back.
  - Unlimited Undos/Redos.
  - Default output to Pixar Renderman Interface Bytestream (RIB) files.
  - K-3D documents are stored using a simple, flexible, easy-to-understand
  XML markup.
  - Scripting interface supports Python, with open API for other scripting
 languages.
  - Plugin support through its architecture in ANSI C++ and GTK+.
Tag: implemented-in::c++, interface::x11, role::program, scope::application, uitoolkit::gtk, use::editing, works-with::3dmodel, x11::application

---

### Post by H13N.H3N on 2011-01-31
> **weedeater64 said:**
> :~$ acs create animation
arkhart - former world for Arkrpg
arkrpg - roleplaying kernel
libarkrpg-dev - development headers for Arkrpg
libarkrpg0c2a - shared libraries for Arkrpg
epix1 - Create mathematically accurate line figures, plots and movies
gimp-gap - The GIMP Animation Package
k3d - 3D modeling and animation system
onscripter - Visual novel games engine compatible to NScripter
piespy - An IRC bot to visualize social networks
python-gnuplot - A Python interface to the gnuplot plotting program
shoes - tiny graphics and windowing toolkit using Ruby
stopmotion - program for creating stop motion animations
worlded - world editor for Arkrpg


k3d looks interesting,
 Some of its features are:
 .
  - Record and play back interactive tutorials and macros.
  - Able to create and edit documents in multiple realtime OpenGL
 solid, shaded, texture-mapped views. You can even model, animate, and
 interact with animations while they play back.
  - Unlimited Undos/Redos.
  - Default output to Pixar Renderman Interface Bytestream (RIB) files.
  - K-3D documents are stored using a simple, flexible, easy-to-understand
  XML markup.
  - Scripting interface supports Python, with open API for other scripting
 languages.
  - Plugin support through its architecture in ANSI C++ and GTK+.
Tag: implemented-in::c++, interface::x11, role::program, scope::application, uitoolkit::gtk, use::editing, works-with::3dmodel, x11::application

Indeed i considered using the 3D suites as 2D animation projects, Blender can do pretty much what AnimeStudio does, i'm checking out the arkart, etc., thank you!, hope to see more suggestions ):P:p:p

---

### Post by xtremethegreat1 on 2011-02-12
Synfig studio is undoubtedly the best in this list. The last time I tried to install F4l, it had serious compilation problems.. Never could make it work though...

---

### Post by Lucradia on 2011-02-12
> **xtremethegreat1 said:**
> Synfig studio is undoubtedly the best in this list. The last time I tried to install F4l, it had serious compilation problems.. Never could make it work though...

That's because it was unfinished, and was abandoned for a newer project with more promise, which was also abandoned.

Neither of them will ever be completed.

---

### Post by rg4w on 2011-02-15
> **H13N.H3N said:**
> **Styckz (Wine)**

_Pros_: A newest program for make stick animations, it has some fun options
_Cons_: No further complains than it takes huge amounts of memory via Wine, and the eternal promise of a Linux version is still showing on their download page.
FWIW, the author of Stykz, Ken Ray, is a very good friend of mine.  I know he's been working on the Linux version - I'll check in with him and see if I can get a status update on that for you.

EDIT:  I just heard back from Ken, and he says that he's ironing out some performance issues on Windows and OS X, after which he'll be focusing on the Linux version.

---

### Post by H13N.H3N on 2011-03-10
> **rg4w said:**
> FWIW, the author of Stykz, Ken Ray, is a very good friend of mine.  I know he's been working on the Linux version - I'll check in with him and see if I can get a status update on that for you.

EDIT:  I just heard back from Ken, and he says that he's ironing out some performance issues on Windows and OS X, after which he'll be focusing on the Linux version.

ouh, thank you i'll be waiting it release! =)

---

