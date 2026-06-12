---
title: "qCAD &amp; gCAD3D?"
date: 2009-04-10
forum: Art &amp; Design
---

### Post by BastardNamban on 2009-04-10
It's been a while since I posted, and I remember posting in the past about good parametric CAD for linux, and got mixed answers.

In the meantime, I ran into a project that had me doing actual manual (ie: pencil & paper with a stupid ruler on non-flat surfaces, rather annoying & unprecise) drafting of sorts, and after fooling around in Gimp for HOURS trying to teach myself from scratch how to draw simple lines and proportional circles/etc (big *** failure, I got there eventually, but am not sure what I did or how to repeat it quickly), I gave up and started searching for a simple 2D CAD program in the repos. (8.04 U) Now I heard all kinds of good about Gimp, and maybe I just don't get it yet, but let's just leave it at this- it wasn't intuitive at all for me, quite frustrating. I ended up filling & deleting for proper width lines.

Point of thread- I found qCAD & PythonCAD, and tried qCAD first- I liked the interface I saw, and really tried to use this, but it kept freezing/crashing on me! I ran the updater, rebooted, same stuff. I have 2.2 GB of free space left, and 1 GB of RAM- what I was seeing shouldn't happen- it would freeze (and my entire laptop with it!), and after 30 or so seconds, unfreeze- I got to draw a few rectangles this way, but constantly freezing mid selection, and made it impossible to draw anything other than random spaced, random sized things uncontrollably. PythodCAD confused the hell out of me- no buttons for anything, and it was freezing too, I believe, though not like qCAD (this one's harder to diagonose). I'm guessing this is for hardcore codeliners who do CAD- not my cup of tea. I need icons, sorry.

I don't know what the deal was, but despite liking what I saw from the qCAD interface (good, simple design!), and watching some tutorials for it on YouTube, I was really sad I couldn't get it working.

Has anyone else experienced this with qCAD or maybe know what happened? Since I've been out of work for over 8 months, stuck in a foreign country for a few more weeks waiting to go home with nothing to do, I have nothing but time to learn some new tricks/software. I'd love to give it another try if I could get it to work without issue.

Second reason for post- my search for 2D CAD for my immediate problem got me looking for a full-fledged powerhouse solution I've wanted for some time. I used to get chances to try AutoDesk Inventor & the new SolidEdge on other's computers, and I LOVE the 3D capability and ESPECIALLY the extrusion parametric modeling interface they have. Also, the motion modeling, all of this inside the CAD suite. I went looking, again, and found this:[http://www.tech-edv.co.at/lunix/CADlinks.html]("http://www.tech-edv.co.at/lunix/CADlinks.html")

I looked into all the major ones- BricsCAD, VeriCAD, ARCAD, FreeCAD, everythingintheuniverseCAD, etc.

I really liked what I saw in gCAD3D- screenshots remind me of Autodesk Inventor when you get the modeling part. It just seems really skimpy as a site page, with not much detail- and I'm not finding much about it in my searches to see videos of other's use.

Has anyone here used gCAD3D, and could chime in on what they think? Is the interface good for a relative CAD newbie (had some experience as said before, and with emachineshop's CAD in windows)? How is the 3D parametric design? Would you recommend this over the pay versions of other software for linux?

Being jobless, and coincidentally, of today, totally broke for a while, I want to find something totally OS that is still powerful/useful for creating blueprints for my dream projects, to be funded later on when I have as much cash as freetime now. I am willing to learn something new, emphasis on willing if it's something that could set me up to better understand other more popular/common CAD design programs with more standardized layouts/creation methods that I could buy for a small sum when I have money later (possibly VeriCAD later on, looks great). 

My time is open now, but if I can put myself in a position to better understand how CAD programs work in general, so I could adapt to a new system when I get some money for a pay linux version of something, I'd REALLY like to do that. Because I'm such a newb to CAD in all computer forms, I can learn without issue, I hope- I just need some (preferably) video guides. I don't get layers fully & a lot of other things, but I know what happens by trying new things/experimenting, or when someone explains something/SHOWS me. Yes, it must do 3D.

Any comments on what may have happened with qCAD, what's up with gCAD3D, or any other recommended strong 3D CAD performers that would fit the bill (0$) I'm looking for that I missed? :popcorn:

---

### Post by BastardNamban on 2009-04-10
Update- I finally figured out Wine, and for the TIME BEING, I got the latest version of eMachineShop.com's free 2D/3D Cad for windows working what seems to be flawlessly under linux!

This is my first time actually using Wine on my own/getting anything to work with it- I have the biggest smile right now- I'm truly amazed at what linux can do!

So, I am still looking for a native linux app that fits my bill, but haven't heard anything yet... but until someone cares to respond, and offer some advice to someone who could really use some from a veteran, I have the best of both worlds- a program that does what I need, in Linux, and non-pirated- as it's totally free in Windows! Hey, it ain't OSS, but it is free legally, and that's what I needed now.

Still, looking for a more permanent, stand-alone solution- any takers?

---

### Post by norwoods on 2009-04-11
Brl-cad

---

### Post by Peter76 on 2009-04-12
I use qcad quite a lot ( as of now the paid version ), and never had a problem with it. It is the only good cad program I know for Linux ( until Bricscad comes with their new version ) and it is very good for what it is ( basic 2d cad app ).
Could you try to run it from the command line and post your output here, maybe that can solve the problem.

---

### Post by Gemnoc on 2009-05-20
Hey BastardNamban,

I just came by your thread. I don't know if you're back home now, and if you've found a nice and paying job. I hope so. :p

Anyway, this is a subject close to my heart. At work, I've been using AutoCAD for years and had the chance to work on Solid Edge for the past two years. At home I've been trying to fully make the switch to Ubuntu. But I have to say that there are not many CAD apps on Linux, and none compare to what's available on Windows.

Pro/engineer, the actual precursor of parametric modeling (Solidworks, Solid Edge and Inventor followed later, and I think that even if CATIA is probably as old, it wasn't parametric at first), was available on Red Hat Linux Enterprise, I'm not sure it still is. It is obviously not OSS and very expensive.

gCAD 3D seems interesting but it is in its infancy. And to be honest, a parametric CAD application is such a complex app that it may take gCAD3D years before it reaches an interesting level of functionality. The developer may abandon it before that...

QCad Community Edition's interface (the one in the Ubuntu repositories) is simply horrid. The commercial version 2.2.2 is barely better. It simply doesn't compare to 2D tools you find in IntelliCAD clones like Bricscad, but of course they cost about 15x more.

On that subject, I've been able to run Bricscad V9.2 demo reasonably well on my PC with wine 1.1.20. But I have a good machine, Athlon64 x2 3GHz with an Nvidia GF8600 GTS 256MB video card. Still, there's a big performance hit as soon as your drawing has many elements. A file as small as 750KB is almost unusable. The developper, Bricsys, is planning to get a Linux-native version later this year. This will be interesting.

There's a free Autocad LT clone, ProgeCAD Smart, (runs on Windows) but I haven't been able to make it run in Ubuntu.

You might also want to take a look at Google SketchUp. If you have a recent dual core CPU and an Nvidia card, The V7 for Windows might work well. It's a really simple and user-friendly 3D modeler. The free version doesn't allow 2D drawings creation and doesn't export in other formats though.

One interesting Linux-native package is [[COLOR="Blue"]MEDUSA4 Free[/COLOR]]("http://www.cad-schroer.com/index.php?&ziel=Products-MEDUSA-M4Personal&land=com&scr=1.7") from CAD-Schroer. It's actually an hybrid 2D/3D design software. You draw on a 2D sheet with special tools, and the software generates a 3D model that you can preview. Although I don't think you can save just the 3D model. This software has the nicest UI I've seen for a Linux CAD app. Complete 2D drawing and dimensioning tools. Drawbacks are you need to register for a free licence every 6 months, and you can only save in the software's proprietary format. If you think you might want to open any work you do with it in years to come, this should give you pause.

And if you are still out of work and willing to keep a Windows partition, Solidworks has the [[COLOR="Blue"]"Engineering Stimulus Package"[/COLOR]]("http://www.solidworks.com/sw/esp/engineering_stimulus_package.html"). You get the software free for 3 months. [[COLOR="Blue"]Autodesk offers Inventor (and Autocad) free to the unemployed[/COLOR]]("http://students6.autodesk.com/?nd=assistance_home&lbon=1") for 13 months.

Good luck!

---

