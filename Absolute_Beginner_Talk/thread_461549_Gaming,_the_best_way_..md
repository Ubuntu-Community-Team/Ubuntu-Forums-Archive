---
title: "Gaming, the best way ."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-01
ATI Radeon Mobility x1400 is my graphics card, i didnt experience games on ubuntu yet, what packages needed? settings and any other considerations ???

---

### Post by KIAaze on 2007-06-01
I'd say that depends on the games.

Now assuming you want to play 3D games, you''ll most likely need to get 3D acceleration working.
Ubuntu usually offers the correct proprietary drivers for that. If Compiz (the 3D desktop) works well on your PC, that's already a good sign. :)

Anyway, here's a long and complete tutorial on 3D acceleration:
[http://www.gentoo.org/doc/en/dri-howto.xml]("http://www.gentoo.org/doc/en/dri-howto.xml")

To test if your 3D acceleration works, do this:
> $ glxinfo | grep rendering
direct rendering: Yes
(If it says "No", you don't have 3D acceleration.)
$ glxgears
(Test your frames per second (FPS) at the default size. The number should be 
significantly higher than before configuring DRM. Do this while the CPU is as idle as 
possible.)



If yes, great. If not, well, it may be difficult to get it to work...

Other than that, if you install games from the repositories via add/remove or synaptic, the dependencies will be installed automatically.
If you install from source, the configure script will tell you what's missing.

Usual libraries for games are python (language), SDL and OpenGL.

Generally, software problems will be the least of your worries.
The hard part is getting the hardware to work.

Also have a look at those sites for gaming on Ubuntu:
-[http://ubuntuforums.org/showthread.php?t=359842]("http://ubuntuforums.org/showthread.php?t=359842")
The [Ubuntu Gamers Arena]("http://gaming.gwos.org/") offers very good help for installing the games. ;)
-[www.happypenguin.org]("www.happypenguin.org")
-[http://www.tuxgames.com/]("http://www.tuxgames.com/")

As well as the gaming forums here:
[http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")

---

### Post by bone43 on 2007-06-01
> **akkad said:**
> ATI Radeon Mobility x1400 is my graphics card, i didnt experience games on ubuntu yet, what packages needed? settings and any other considerations ???

Here is one thing ive found true posted by and clears up some of the sad state  that is ATI support for Linux..

"This was posted by lebabyg


April 7th, 2007, 10:30 AM
In simple terms:

ATI are pretty rubbish when it comes to linux, and aren't releasing their source code to let open source developers get involved in the fray. So you have 2 choices for ATI drivers in linux:

1. Open source
2. Closed source (proprietary ones from ATI's website)

With open source you can run AIGLX to run Beryl with. AIGLX is built into the X-server so you can run hardware accelerated programmes as well as hardware accelerated desktop. However, the acceleration achieved is without opengl (I think but don't quote me on this), but whatever, games, desktop etc etc run at pretty poor accelerated performance.

With closed source you can't run AIGLX because ATI haven't enabled that yet. You do get **** hot acceleration however on a par with windows. With this acceleration you can either run Opengl proggys (googlearth) OR (THAT IS OR) a 3D accelerated desktop in XGL. This is because XGL runs over the normal xserver. Essentially, XGL-server is on open-GL programme running on X, which is why it eats resources.

SO to conclude. YOU CAN EITHER HAVE 3D DESKTOP OR 3D ACCELERATION FOR GAMES WITH ATI AND XGL. You can't have your cake and eat it yet. ;). Hope this clears up the issue for you and stops you chasing the impossible dream of Xgl AND direct rendering."

No matter how hard i tried i cant have my cake and eat it yet as was said:(
So we are still waiting hopefully  AMD will fix this but it may not be soon.;)

---

