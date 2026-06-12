---
title: "Sketchup in Linux?"
date: 2007-12-23
forum: Art &amp; Design
---

### Post by alexv305 on 2007-12-23
I searched and couldn't find Google Sketchup for Linux. Prolly doesn't exsist. Anyways is there a linux program available that is similar to it? I'm doing basic wood working models in inch sized units.

Any suggestions?

---

### Post by omega_user on 2007-12-25
No, there's no Linux version of sketchup and there doesn't look like there'll be one for a little bit.  

Others:
Blender 3D seems to be okay.  Equinox seems quite good too, but that isn't in the Add/Remove Programs like Blender.  Hope that's a step in the right direction.

---

### Post by rfruth on 2007-12-25
No sketchup for linux yet ...:confused:

---

### Post by IanW on 2007-12-25
> **rfruth said:**
> No sketchup for linux yet ...:confused:

People (me included) have been asking Google for it for at least a year now, still no progress.:(

---

### Post by jetrost on 2007-12-25
> **alexv305 said:**
> Any suggestions?

I just downloaded SketchUp from Google and installed it via wine, and it worked fine. The menu bar and the "quick pick" buttons on the top of the screen, as well as the status bar on the bottom of the screen would go black frequently, but when I moused-over them, they would reappear. 

Modeling a quick house went without a hitch, and the 3D rendering worked fine. I'm no expert, but the menu bar issue may not be a universal problem...but again, it wasn't *that* big of an issue. If you use the program enough, you will get the hotkeys down quickly enough. 

So, to answer your question, my suggestion would be to install and run it using wine. Good luck!

---

### Post by gigafish on 2008-02-12
Maybe Google intends to release a Linux friendly version of Sketchup when it releases a Linux Distribution.

---

### Post by Ecclesia on 2008-02-12
I doubt that google is going to release a linux distro.  This is a rumor that keeps going around.  Apparently they use linux in-house, but aren't planning on releasing anything.  I'd personally be interested to see what they come up with, but I doubt they're going to take such a major undertaking.  Or perhaps they're using Android as a test bed for what this type of thing might look like for them.

---

### Post by IanW on 2008-02-13
Sketchup now seems to work OK for me using Wine 0.9.54 on 64-bit Ubuntu.

---

### Post by hardyn on 2008-02-13
sketch up was aquired by google, as was initially written by a small unknown 3rd party (i think my old man still has an old copy with the original label on it somewhere).  it was never designed for linux, so a port may be REALLY difficult.

---

### Post by weelibin on 2008-02-13
im very suprised that there isnt something like sketchup for linux theres every thing else, open office, lmms, hydrogen etc... blender seems to be ok but i think its a bit over complicated to be honest i was going to learn it till my workload became just a bit too much and i realised that its more of a 3 D rendering tool than a design program.

---

### Post by Jeffa on 2008-02-14
> **hardyn said:**
> sketch up was aquired by google, as was initially written by a small unknown 3rd party (i think my old man still has an old copy with the original label on it somewhere).  it was never designed for linux, so a port may be REALLY difficult.

The company that originally developed Sketchup was called @last Software. 

> **Ecclesia said:**
> I doubt that google is going to release a linux distro.  This is a rumor that keeps going around.  Apparently they use linux in-house, but aren't planning on releasing anything.  I'd personally be interested to see what they come up with, but I doubt they're going to take such a major undertaking.  Or perhaps they're using Android as a test bed for what this type of thing might look like for them.

Google does use a flavor of Ubuntu in house (called Goobuntu). While rumors have been circulating for years that they are going to release on OS (perhaps even a web based OS!) most insiders generally agree this probably won't happen. (at least not in the near future)

> **jetrost said:**
> I just downloaded SketchUp from Google and installed it via wine, and it worked fine. The menu bar and the "quick pick" buttons on the top of the screen, as well as the status bar on the bottom of the screen would go black frequently, but when I moused-over them, they would reappear. 

Modeling a quick house went without a hitch, and the 3D rendering worked fine. I'm no expert, but the menu bar issue may not be a universal problem...but again, it wasn't *that* big of an issue. If you use the program enough, you will get the hotkeys down quickly enough. 

So, to answer your question, my suggestion would be to install and run it using wine. Good luck!

This is precisely what happened when i installed sketchup via Wine. Glad I'm not the only person. I tried disabling Compiz, but still had the same problem. Maybe it's an OpenGL problem?

---

### Post by trig on 2008-02-15
I do not know what this is, can anyone discribe it
trig

---

### Post by senectus on 2008-03-25
they've[ hinted]("http://googlesystem.blogspot.com/2007/06/google-to-launch-more-linux.html") at doing a linux version of sketchup...

---

### Post by jorwex on 2008-03-25
I've been running Sketchup with a patched version of 0.9.40 wine for a while. It's pretty damn stable and I can't find one thing that hinders my normal usage of the program on Windows.

[http://aksels.de/php/count.php?action=download&filename=SketchUp-Wine-v0.2-aksels.de.tar.gz&filepath=../d/SketchUp/](http://aksels.de/php/count.php?action=download&filename=SketchUp-Wine-v0.2-aksels.de.tar.gz&filepath=../d/SketchUp/)

His readme is not the most user friendly (or it wasn't for me 3 months ago when I switched from windows), so if any one wants it, I wrote a little readme to complement his.

I tried 0.9.56 for a few minutes, and everything that was a problem without using the patched old version of wine seems to have been worked out.

In 0.9.57, there's actually a bug fix in the release notes for Sketchup:
   8694  Google SketchUp Fails to Launch

I haven't tried it since then, but it must be even better.

---

### Post by ubunter1 on 2008-05-01
mine just crashes and says- sketchup was unable to initialize open gl, please make sure you have installed the correct drivers for your graphics card. error;choosepixelformat failed.

---

### Post by albertoramirez on 2008-05-27
It is a real shame that Google has not released Sketchup for Linux.

I installed it through wine, and installation worked fine, buy got the same "open GL" problem.

There must be a workaround around....

---

### Post by IanW on 2008-05-28
The changelog for Wine 1.0rc2 claims that they've fixed the "choosepixelformat" bug for Sketchup.

---

### Post by Tyche on 2008-05-29
Sketchup 6 requires the .NET framework, which may explain the reason there are problems with porting it to Linux.  It may also explain why there are the problems that have been reported in running it under WINE.

:(

---

### Post by grimsqueaker on 2008-11-15
> **Tyche said:**
> Sketchup 6 requires the .NET framework, which may explain the reason there are problems with porting it to Linux.  It may also explain why there are the problems that have been reported in running it under WINE.

:(

hasn't stopped them porting it to Mac....  or maybe i'm missing something ??

---

### Post by sarahjohn on 2008-11-17
I'm a Linux user and have been disappointed that there seems to be no
Linux support for Sketchup. Are there any plans here? I think there
would be a significant interest among Linux users, and a Linux
friendly release (even as a closed-source commercial product) would in
turn strengthen the software offerings for the Linux platform. At
present the only really satisfactory 3d modeling tool for Linux is
Blender, but Sketchup is so much better for many tasks (and so
complementary with Blender in other ways).

If producing a Linux release is too intensive, then is there the
possibility of working with people at the Wine project to make
Sketchup work under Wine on a Linux machine?

---

### Post by -yay- on 2008-11-17
I never tried this Sketchup thing, is it better than for example [Wings3D]("http://wings3d.com/")?

---

### Post by kayosiii on 2008-11-17
The two are quite different - Sketchup is really targetted at architectural models and to a large extent it is successful at this. Sketchup is a really simple tool to learn - but makes it easy to make really bad models - from the point of view of using it in a multi program workflow. At work we spend a lot of time cleaning up bad sketchup models. 

Wings3d is targetted on the other hand towards subdvision surface modelling which lends itself better to impresise organic style modelling.

---

### Post by -yay- on 2008-11-19
I see, thanks for clarifying it kayosiii :popcorn:

---

### Post by alexhrdr on 2008-11-19
> **gigafish said:**
> Maybe Google intends to release a Linux friendly version of Sketchup when it releases a Linux Distribution.

That and Chrome eh?

---

### Post by dankegel on 2008-11-23
Sketchup 7 is working fine for me once I follow the tips in [http://wiki.winehq.org/GoogleSketchup](http://wiki.winehq.org/GoogleSketchup)
but I'm no expert.  Can anybody who's having problems
report them to the wine appdb or bugzilla?
Thanks!

---

### Post by jeromio on 2008-12-29
I have proprietary NVidia and I've tried both Sketchup 6 & 7 on both wine 1.0.1 and crossover office 7.1.0. I have tried changing the registry key(s) and even deleting the key - I still get the OpenGL error on every configuration.

---

### Post by dankegel on 2009-01-01
> **jeromio said:**
> I have proprietary NVidia and I've tried both Sketchup 6 & 7 on both wine 1.0.1 and crossover office 7.1.0. I have tried changing the registry key(s) and even deleting the key - I still get the OpenGL error on every configuration.

Your Wine is probably too old.  Try again with wine-1.1.11 (or
a newer version, depending on when you read this).

---

### Post by desconocido on 2009-01-03
> **hardyn said:**
> sketch up was aquired by google, as was initially written by a small unknown 3rd party (i think my old man still has an old copy with the original label on it somewhere).  it was never designed for linux, so a port may be REALLY difficult.

It is supported for Mac OS X which is UNIX so it can't be that difficult to port to Linux/Ubuntu..

> Mac OS X
    * Software
          o Mac OS X® 10.4.1+ and 10.5+.
          o QuickTime 5.0 and web browser for multimedia tutorials.
          o Safari.
      Neither Boot Camp nor Parallels are supported environments.
    * Recommended hardware
          o 2.1+ GHz G5/Intel™ processor.
          o 2 GB RAM.
          o 400 MB of available hard-disk space.
    * Minimum hardware
          o 1 GHz PowerPC™ G4.
          o 512 MB RAM.
          o 160 MB of available hard-disk space.
          o 3D class Video Card with 128 MB of memory or higher. Please ensure that the video card driver supports OpenGL version 1.5 or higher and up to date.
          o 3 button, scroll-wheel mouse.

---

### Post by markov035 on 2009-04-01
> **desconocido said:**
> It is supported for Mac OS X which is UNIX so it can't be that difficult to port to Linux/Ubuntu..

[http://www.mono-project.com](http://www.mono-project.com) alloows you to develop on several platforms, and should be easy to "port" the code: just say "compile to linux"....

---

### Post by mesae on 2009-04-22
I use Varicad ([www.varicad.com](www.varicad.com)).  They have Windows and Linux (deb & rpm) versions.  This is commercial software so is not free (around 600-700$ retail for commercial use), but there is an academic license as well for around $110-120, depending on the exchange rate.  This is excellent mechanical engineering software, IMO, and is very suitable for home educational woodworking projects, which is what I use it for.  It is very easy to use, once you learn the basics (much easier than TurboCAD).  I am not an engineer or even a pro draftsman but I find that I am much more productive in 3D with VariCAD than I ever was with TurboCAD, AutoCAD LT, or any of the AutoCAD clones.  VariCAD is parametric (you can specify standard screw or bolt holes types, grooves, booleans, etc., specifying the size parameters, etc, and you can later go back and easily move, resize, delete or otherwise change any "parameter" of the hole or other parametric feature.  It supports 3D constraints as well.  It's very stable under Ubuntu, and I have used it extensively for more than a year.  It can very quickly and easily generate 2D views from 3D models, which you can then dimension using familiar methods.  Another benefit of the student license it that it is not time-limited like the ones from AutoDesk, etc.  Once you purchase a license, it's yours to use forever, just not commercially.  You obviously must purchase a commercial license if you want to use it commercially.  It does not have sophisticated rendering ability, like materials, raytrace etc., but it is very suitable for my purposes.

---

### Post by Newfoundlander on 2009-04-23
> **IanW said:**
> People (me included) have been asking Google for it for at least a year now, still no progress.:(

I'm curious how you have been asking them.  E-mail?  Forum?  So I can do the same because I'd love to have a Linux version.  It crashes under Wine.

---

### Post by yakov_w on 2009-06-20
Hi, [Art of Illusion]("http://www.artofillusion.org/") is a good option to Google Sketchup, try it. [http://www.artofillusion.org/](http://www.artofillusion.org/)

---

### Post by chips24 on 2009-06-20
blender is hard to learn, but try that, thats what im trying to learn right now.

---

### Post by mfr1003 on 2009-07-17
Just wait for Google Chrome OS, or whatever the Silicon Giant decides to call their new Microsoft-rival Operating System. =D> Surely a Google OS would come with or at least be compatible with all Google's wonderful software!:D Unless they are just imbeciles. ](*,)

:popcorn:

---

### Post by djfunkey on 2009-07-26
another good program is k-3d on ubuntu :) but google sketchup didn't work on my computer :( even though I used wine I clicked run with wine and nothing happened.:confused:

---

### Post by jackpipe on 2009-08-14
[http://www.sweethome3d.eu/](http://www.sweethome3d.eu/)

---

### Post by Mysearch on 2009-08-30
Hi,
I am new to Ubuntu having just installed 9.04. So I hope this posting is not inappropriate for this forum. One of the things I am trying to get a handle on is what applications are Windows dependent. As a Sketchup user I was interested in what SU options were available. Tried WINE, but had problems that I will posted on separately, but thought there might be some interest in a discussion within the Google SU feature forum, see below. 

-------------------------------------------------------
On Sun, 2009-08-30 at 08:41 -0700, LewisWadsworth wrote:
Gerhard asked me to stop by this discussion group.
> 
> I spoke to the SketchUp team about this topic at the Googleplex in
> Mountain View last summer: I'm sorry to inform you that you will not
> find SketchUp as a native application in any Linux distro in the
> foreseeable future.  There are only a handful of people working on
> SketchUp in the Google Boulder office, and I was told that there is
> simply not the manpower to develop and maintain any more versions of
> it.  Development on Windows and Macintosh versions is continuing
> (don't even think to ask about that), of course, but any Linux version
> is a non-starter. You can infer from this that SketchUp, as beloved as
> it is by a certain relatively-small user group which includes myself,
> is not a priority for Google in a larger sense.  It is simply not a
> core product for the company.
> 
> Your best bet is better performance with SU on Linux using WINE.
> However, I do not consider this a particularly hopeful avenue...with
> the kind of complex architectural models I develop using SketchUp, the
> screen-redraw lag makes SketchUp unusable on Linux systems for me, and
> I have wasted too much time that frankly could be better used
> elsewhere in attempting to make the software work acceptably in Linux.
> 
> With regard to Chrome OS and 3D modeling, you might get a better sense
> of Google's "3D" interests from their efforts with O3D:
> 
> [http://code.google.com/apis/o3d/docs/techoverview.html](http://code.google.com/apis/o3d/docs/techoverview.html)
> 
> If Chrome OS is to be essentially a minimal gateway to "the Cloud", it
> would be logical to see future developments in 3D modeling from Google
> arising from things like O3D or alternative, OS-independent
> implementations of 3D in Javascript that run in a web browser and
> store data on a remote server as Google Docs do now.  Google is not
> the only company working on Cloud-based applications of course:  for
> instance, Aviary has acknowledged that it is working on a 3D modeler
> called "Hummingbird" that will sync with its own Flash-based (and
> fairly impressive) image editing tools.
> 
> [http://aviary.com/blog/posts/advertising_artwork_for_hummingbird_revealed](http://aviary.com/blog/posts/advertising_artwork_for_hummingbird_revealed)
> 
> --~--~---------~--~----~------------~-------~--~----~
> You received this message because you are subscribed to the Google Groups "Feature suggestions" group.
> To post to this group, send email to [email]sketchupsuggestions@googlegroups.com[/email]
> To unsubscribe from this group, send email to sketchupsuggestions+unsubscribe@googlegroups.com
> For more options, visit this group at [http://groups.google.com/group/sketchupsuggestions?hl=en](http://groups.google.com/group/sketchupsuggestions?hl=en)
> -~----------~----~----~----~------~----~------~--~---
>

---

### Post by jlukescott on 2009-09-22
alexv305, you mentioned you wanted a program for wood working. For this I would recommend [QCad]("http://www.qcad.org/") over Blender3D.

QCad is definitely more of a CAD/CAM oriented program, although it is simple. But I personally prefer its simplicity, and I also prefer its adherence to a more standard interface & workflow, like AutoCad. The main drawback compared with Sketchup, Blender3D, or other 3D programs is visualization. It's harder to print out a meaningful drawing if you're not used to looking at line drawings and knowing what they correspond to in real life.

I built my first deck (ever) using a drawing made with QCad, and I have to say with total modesty that it came out perfect, except for one mis-measurement that happened in the drawing - before I printed out the diagram - which then got transferred into a bad cut. This goes back to what I was saying about being comfortable reading/interpreting line drawings.

Hope this helps.
Luke

---

### Post by bknhnd on 2009-11-23
> **gigafish said:**
> Maybe Google intends to release a Linux friendly version of Sketchup when it releases a Linux Distribution.
 What??!! Their releasing a linux distribution?? Well, anyway, I'm going to try Google Sketchup in Wine and see how it goes. It probably won't work anyway.:icon_frown:

---

### Post by loell on 2009-11-23
> **bknhnd said:**
> What??!! Their releasing a linux distribution?? Well, anyway, I'm going to try Google Sketchup in Wine and see how it goes. It probably won't work anyway.:icon_frown:

it's been working for the last six months or so, it's a bit rough but usable.  especially if you nvidia card, sketchup will work.

---

### Post by rodericx on 2009-12-25
if u can.... maybe have the both OS could a good responde... 

sketchup can export to format to COLLADA.

1) export your model to collada
2) change extension of collada to .ZIP
3) unzip... all the stuff materials etc, keep in one folder
4) leave or copy in some media to be read in ubuntu
5) open blender, and import the model.

maybe u can learn blender and practice.

thats its what i do to learn blender.. the 2.5 its incredible.

---

### Post by acornbrain on 2010-01-19
Hoping someone in the forum can help me with this.

Just learned about SketchUp the other day. Decided to DL sketchup 7 and take a stab installing thru WINE. (ver. 1.01) (I am on jaunty)

seemed to work at first, but got the "open gl" error. Should have checked the forums first, but I wasn't in the mood, so I just gave up, uninstalled sketchup7, and installed it on my other Windows box instead.

now I'm thinking I was a little too hasty. I'd like to try again, but now I can't re-install googlesketchupWEN.exe. I downloaded another copy, but instead of a fresh install, it only gives me the option to "repair" my first installation. When I click on this, the installer goes thru its paces and appears to finish, but I can't even get Sketchup to start, just does nothing.

I think there is some remnant of Sketchup stuck in my system somewhere, via a 'cookie' or registry or something. Or maybe the product can only be registered to a given computer once or something. I am afraid that unless I somehow expunge all evidence of my first install, I won't be able to try again with a fresh copy.

At this point, I don't know if the offending issue is with Ubuntu, WINE, or Google itself.

Any advice?

-Brian (noob)

EDIT:

I guess I should add that I am also willing to find a Linux substitute for SU. I am going to be using it pretty much exclusively for architectural renderings. Even though I am a 2D CAD drafter, I've always done my renderings by hand, and I don't have much, if any, experience with 3D CAD, so I need the software to be quick and easy to learn. Needs to have the ability to export to PDF, JPG or other raster image. Hopefully is geared towards architectural rendering, and has surface materials like siding, brick, shingles etc, landscaping also a plus. I'm going to give Sweet Home 3d a try. Any other suggestions are appreciated.

Thanks again!

---

### Post by hyburn on 2010-01-19
sketchup works fine for me through wine

---

### Post by acornbrain on 2010-01-21
UPDATE:

DL'd a registry cleaner that zapped SketchUP entirely. I was then able to reinstall a fresh copy. Did the openGl registry fix. Now SketchUP will open, and I can use it for a few minutes, but then it crashes. Also, there is a white box that surrounds the cursor image which partially obscures the points I am trying see. Pretty annoying.

I'm going to do some more digging and see if I can make this work better.

-brian

---

### Post by 23dornot23d on 2010-03-01
I have just installed sketchup 7 ..... works great through using wine 1.2 .... 1.1.39-0ubuntu1~karmic5 ,,, 
from synaptic download ........ 

I also have a Nvidia card ... which seems to be a useful thing for this application to run properly ......

it is also good that files can be moved from 3ds into sketchup ..... 

_____________________________________________

? back out again if needed .... as Colladra files .... 

(.dae) .... seem to need to start paying money if you want useful 3D output files from it

Ok as of just ........  I cannot get the .dae file output from sketchup ..... it needs to be upgraded to Sketchup Pro ........

and I cannot find any free plugins .....

---

### Post by huangweiqiu on 2010-03-07
run it with Wine

---

### Post by robsc on 2010-05-11
i've had success on my pc installing sketchup 7 and some plugins. i've run sketchup ona pc and two laptops running linux int 8. oddly, sketchup 7 and the dim_angle.rb plugin work fine. howeve3r, one either of my laptops, sketchup runs, but the dim_angle.rb jplugin will not load. i get thisw message: Error Loading File dim_angle.rb
C:/Program Files/Google/Google SketchUp 7/Plugins/dim_angle.rb:2: syntax error
# The code related to click 3 points was reused here from an original
^
C:/Program Files/Google/Google SketchUp 7/Plugins/dim_angle.rb:11: syntax error
require 'sketchupclass DimAngleTool.       any  ideas on what might explain this odd incongruency?

---

### Post by gandra on 2010-06-07
How about Autodesk Autocad ?
 
Anyone could run it unde Linux??
 
Wich version ?? 
 
Regards 
 
Gandra

---

### Post by scoty1991 on 2010-06-09
> **mfr1003 said:**
>  =D> Surely a Google OS would come with or at least be compatible with all Google's wonderful software!:D Unless they are just imbeciles. ](*,)

:popcorn:

haha, you mean unless they're microsoft! ;)

---

### Post by jfreak53 on 2010-06-19
> **Ecclesia said:**
> I doubt that google is going to release a linux distro.  This is a rumor that keeps going around.  Apparently they use linux in-house, but aren't planning on releasing anything.  I'd personally be interested to see what they come up with, but I doubt they're going to take such a major undertaking.  Or perhaps they're using Android as a test bed for what this type of thing might look like for them.

I bet you feel foot in mouth now don't you!  Chome OS baby, waiting for it with anticipation, very soon, very soon now!

And yes sooner or later all Google's software has to port to Linux since they are releasing Chrome OS, they have to.  So it's just a matter of time.  Hey they released Chrome for Linux, so the others are soon to come people, just be patient.

---

### Post by dchurch24 on 2010-06-28
Give the bloke a break!

That post was over 3 years ago!

I bet even Google didn't know they were going to release an OS back then!

---

### Post by Thomas_Bates on 2010-07-15
> **dchurch24 said:**
> Give the bloke a break!

That post was over 3 years ago!

I bet even Google didn't know they were going to release an OS back then!

You really think they an code an OS and provide functionality for everything, ranging form hardware to software, to internet things, in just 3 years? LOL.
I'm sure they've been working on this for quite some time.

---

### Post by evgen_m on 2010-09-01
i installed wine through add/remove programms. version is 1.2
than i try install sketchup. in beginning looks ok, only not scroll down and up for choose templates, but than when i push start using sketchup it writes: "sketchup was unable to initialize OpenGL! Please make sure you have installed the correct drivers for your graphics card. 
Error: ChoosePixelFormat failed

any advice?

---

### Post by 23dornot23d on 2010-09-02
> **evgen_m said:**
> i installed wine through add/remove programms. version is 1.2
than i try install sketchup. in beginning looks ok, only not scroll down and up for choose templates, but than when i push start using sketchup it writes: "sketchup was unable to initialize OpenGL! Please make sure you have installed the correct drivers for your graphics card. 
Error: ChoosePixelFormat failed

any advice?

What graphics card do you have in your computer ?

System - Administration - Additional Drivers ....... just check that there are no outstanding or newer drivers that need installing to make things work properly.

---

### Post by dchurch24 on 2010-09-06
> **Thomas_Bates said:**
> You really think they an code an OS and provide functionality for everything, ranging form hardware to software, to internet things, in just 3 years? LOL.
I'm sure they've been working on this for quite some time.

Nope, but I do think that with their dosh they could easily put together lightweight window manager for Linux in which all the applications they provide are web-based (meaning that they could develop them without the OS even being in existence) - which is what Chrome is.

Indeed, according to Wikipedia:

[quote=wikipedia]
Google developers began coding the operating system in 2009
[/quote]

---

### Post by scottme on 2010-10-27
Just a quick note to say that I installed the latest Sketchup 8 under Wine on Ubuntu 10.10, and after the registry fix for OpenGL, it appears to work very well.

---

### Post by Yaroslav_L on 2010-10-30
During the installation of Pro version I'm getting error:
".NET Framework 2.0 must be installed prior to installation of this product"
Is it possible?

---

### Post by bug770515 on 2010-11-02
.net Framework _2.0_ does work with wine/crossover. so try to install it and then run it. the other versions... not so much

---

### Post by montreano on 2010-11-03
hello  all , google sketchup  now in linux .

---

### Post by grey1beard on 2010-11-04
> **scottme said:**
> Just a quick note to say that I installed the latest Sketchup 8 under Wine on Ubuntu 10.10, and after the registry fix for OpenGL, it appears to work very well.

Just found your post scottme.
Could you spell out the fix, as I'm in the same boat, and seem to have lost the paddle.
John

---

### Post by alanmoore78 on 2010-11-05
> **montreano said:**
> hello  all , google sketchup  now in linux .

Nein.

from the Sketchup Blog:

"**SketchUp for Linux**
'Desktop Linux users should be able to run a native port of SketchUp on their distro of choice.'
We hear this request all the time, but realistically we’re not likely to ever make a version of SketchUp that runs as a native client application on Linux. However, SketchUp can be run effectively on Linux using Wine, and we’re keen to improve that where it is practical to do so."

---

### Post by grey1beard on 2010-11-05
Ja.
I have just solved my problem with the help of a thread I found in the wine sub-forum, so many thanks to noriegafam for his final step.
John

---

### Post by Yaroslav_L on 2010-11-18
> **bug770515 said:**
> .net Framework _2.0_ does work with wine/crossover. so try to install it and then run it. the other versions... not so much

trying to install .net Framework 2.0, but get error message - look at screenshot.
Any ideas?

Sh... can't attach *.jpg

Can anybody make step-by-step instructions of how to install .net Framework 2.0?
Thanks!

---

### Post by grey1beard on 2010-11-18
I didn't need to install .net Framework 2.0 for google sketchup version 8.0.3117, the basic free download.
Are you installing a different version, perhaps, the Pro for instance ?
John

---

### Post by hyperAura on 2010-11-19
it should be working with wine..

---

### Post by danger89 on 2011-12-20
It disappoint me from Google. Please, just build a native Sketchup application for Linux. Why Windows & Mac only (5 year later...).. come on please.. please..

---

### Post by overdrank on 2011-12-20
Back to sleep thread. Thread closed.

---

