---
title: "A new Window Manager"
date: 2008-07-21
forum: Art &amp; Design
---

### Post by SphereCat1 on 2008-07-21
Welcome to the original TWiMU Thread! The TWiMU Project has moved to the [TWiMU Forums]("http://apps.sourceforge.net/phpbb/twimu"), hosted by Sourceforge. Please visit there to post questions or to help with the project. The original thread begins below.

-------------------------------------------------------------------------------

Hi everybody! I'm new to Ubuntu, but I have some experience with Puppy Linux. Anyway, I want to try to write a new Window Manager, and I picked Ubuntu as my development platform because it comes pre-packed with so many tools.

The basic concept is kind of like the OS X dock in leopard: the desktop is a huge table that you can place icons and windows on, and it can be as big or small as you want.

There will also be a method of grouping items called Palettes, but I'm not exactly sure how they work yet.

Anyway, I'm creating this thread for any ideas or suggestions, just a general wish list. I'll make everything I can happen. This was going to be in programming, but I figured it's more about making things look good than anything else.

Post whatever comes to mind, I'm open to just about anything!
SphereCat1 :)

---

### Post by Merk42 on 2008-07-21
So you want the OSX Dock, or for Linux, [AWN](http://wiki.awn-project.org/)?

---

### Post by SphereCat1 on 2008-07-21
I'm not looking for any particular extension, I'm creating my own. It's just the same general idea as the Dock.

While I'm here, I'll post an idea: What if instead of having the desktop picture in the back, it goes underneath the "table" and shows through? Or maybe even having it as the table's surface?

---

### Post by Merk42 on 2008-07-21
I understand you were making your own, but if it already exists wouldn't it be better to work on the existing source?

I don't quite understand your "table" concept though

---

### Post by aimran on 2008-07-22
Do you mean having icons of running applications appear on the desktop instead of a dock? Or rather a taskbar but on the desktop? There's [backstep]("http://backstep.sourceforge.net/screenshots.html") which does the above. It displays running programs as icons on your desktop, which you could use feh to manage.

So far I've managed to get it to run. I think there's a live window preview (instead of icons) in the development/testing process, but the project seems dead. I've not even managed to get the live preview feature running as per instructed on the site.

Hope I've helped.

---

### Post by xakh on 2008-07-22
well, I'd be interested, but I think that you should build on something, and not start anew. Maybe XFCE, with its stability, would be a good start? At any rate, I'd probably try it out once it really hit a stable point, but if you're making it, please try to make a graphical theme designer, I have a lot of ideas, but I'm horrible at code.

---

### Post by SphereCat1 on 2008-07-22
Hi again!

Sorry I missed you're point Merk, I did look at Avant, and it might be a good place to start. I'm also looking at possibly using PYWM as a base, because it allows desktop zooming and you have an infinitly big desktop.

Aimran: The running apps would appear in perspective laying on the front of the table, they would be represented by the open window. They also have the ability to group the same app like in XP, and they would then pop up into a column when clicked. If you have the link to the project, pass it along, it would be useful.

xakh: Thanks for volunteering! We need lots of testers. As for a theme design tool, I'll work on it, but to start with you'll be able to change stuff just by changing image files and editing a few variables, I'll make sure to make the config file easy to edit.

I've included a rough sketch done in Inkscape to give you all a basic idea of what it looks like, the weird shapes are icons, notice how they get smaller as they get farther back.

[Link to concept drawing here!]("http://spherecat1.googlepages.com/tabledesk.png")

More to come! :)

---

### Post by Merk42 on 2008-07-22
And when a program is opened full screen, how do you see your apps?

---

### Post by SphereCat1 on 2008-07-22
Good point, Merk, but you can't in Windows either, you have to minimize. Maybe I can use the infinite desktop feature to zoom out a little when you hit a shortcut or move the mouse to the bottom, then a bar with open apps could show up, and also have a minimize and close button.

SphereCat1

---

### Post by Merk42 on 2008-07-22
> **SphereCat1 said:**
> Good point, Merk, but you can't in Windows either, you have to minimize.

In Windows (or OSX, GNOME, KDE XFCE...) you can see what apps are running while a full screen application is running.  You can also easily get to a menu to run another application in any of those other environments.

---

### Post by xakh on 2008-07-22
okay, the shelf is cool, REALLY cool, the main questions I have are:
How will a 3D desktop work with this? Could it become something of a "Flower", with the tabletops spreading out?
Will there still be a menu bar at the top or bottom, as well as a little toolbar like on windows/gnome/ everything but Mac's default WM where we can switch between windows? because those would be seriously counter-intuitive.

---

### Post by aimran on 2008-07-23
Spherecat: I suggest you work off backstep as they have already done something similar. Only thing missing is the window preview. That smaller icons in the distance is a bit hard to click on for someone who needs them fast. Just my $0.02

---

### Post by SphereCat1 on 2008-07-23
Good morning, everyone! (or it is here anyway...)

Where to start?
Merk: I completely forgot about the taskbar popping up, because on mine at least (I have really old computers, it might just be lack of experience) you have to hit the Windows key, but I think I've been on computers where you just move to the bottom. I think I'll do what I mentioned earlier, just have it zoom out slightly to show a bar.

xakh: The flower is a good idea, I think that would look awesome! I was also thinking of just having the current view sliding off screen, and having the new one slide in from whatever direction. Maybe make it an option?
Also, since the middle of the flower would get progressively larger with more desktops, maybe it could have layers going outward, like (bad simile) an onion? That would mean you have way too many desktops. And we could also put something useful in the middle!

aimran: Thanks for the recommendation, I'll look at backstep. Also, the picture is obviously smaller than a real screen, too, so they won't (hopefully) end up being too small. Plus you can zoom back and forth by moving the mouse to a back arrow at the back of the screen. This may need some work to make it more intuitive.

Thanks for helping, guys!
SphereCat1

EDIT:4 minutes later: I've just looked at backstep, and it combined with Xrender will be nearly perfect. I'll mix the code in with whatever WM we use as a base. We do, however, need a way to draw the previews laying down in perspective. I'm sure there's a way to do that.

---

### Post by SphereCat1 on 2008-07-23
Hi again! As of about 5 minutes ago, I've downloaded [PYWM]("http://pywm.sourcefourge.net/") and [Backstep]("http://backstep.sourceforge.net/"), in the hopes of combining them. Both projects have been dead quite a while, backstep 0.3 (the latest version) was released in 2005. Hopefully both of these pre-1.0 releases don't have too many bugs, but we'll find out.

I also have to write a Python script to connect the two, which should be interesting, because I'm currently learning Python. :)

We'll start worrying about making it look like a desk after I get it running.

Thanks for all the help! :wink:
SphereCat1

P.S.: We need a name for it.

---

### Post by aimran on 2008-07-23
That's great! I'll leave the naming up to you. Can't wait to beta test this :)

---

### Post by xoger on 2008-07-28
i like the sound of this and your concept art looked very hopeful. will this combine with the cube effect in any way, i think it would be cool if when you use the cube the table would stick out

---

### Post by SphereCat1 on 2008-07-28
That's an interesting idea...

---

### Post by SphereCat1 on 2008-08-04
I'm back with an update everyone.
Things are _not_ going well. I don't have an internet connection on my development computer, so I've spent the last three days running back and forth with a CD-Rom full of packages. Right now I'm almost done with installing BackStep, one of the key ingredients, but then I have to install all of the Xlibs libraries by hand to get PYWM working. :(

On the bright side, I do have a new mockup coming, it includes a couple new features and looks much better than the original. (Which, in my defense, was made in 5 minutes.) I'll probably post it later today.

SphereCat1

---

### Post by conorsulli on 2008-08-04
I have an idea but not like you think, seeing as thier are so many osx docks out there why not make a very eye-candy loving version of gnome panel? with sort of e17 aspects like animated shines, fading and that sort? with a sort of cool start menu like winvis+a? where it would have reflection etc and nice throbbing  effects when you hover over icons etc?

*We have so many osx docks clones with endless plugins.
*gnome panel is limited and ugly, no alternatives that have true eyecandy.
*thier is a good source code with e17 (enlightenment) make life easy for you.

It is only a suggestion but a valid one I hope.

---

### Post by rbolio on 2008-08-05
Oh! just cought up with your scheem (or how ever that is spelled XD)

I thought about what  "someone"[aka not sure who] said about a button being to far behind not being productive....

so i thought, 

"it might be hard, but how about a 3D rotation of the seudo-desk applet or watchamaycallit,"  

i thought it would give you some sort of edge over the rest of the zombie projects...

Oh btw...would like to know how this project is working and as someone [another unknown >.<], id be interested in testing this aswell, i mean im not much of a programmer or anything...but heh! 

:lolflag:

---

### Post by SphereCat1 on 2008-08-05
Hi everybody!

Over the last 5 days, I have done _nothing_ but try to install various packages that are required to run backstep or pywm. I've screwed up my computer so badly that I'm currently reinstalling Xubuntu!

For some reason, backstep fails to recognize _any_ of the installed packages, and I've spent the last week trying to upgrade them, and I've done nothing but break things. Could someone help me?
I think the problem is that pkg-config isn't installed with Xubuntu, so none of the .pc files are created to identify that the packages are indeed there. Does anyone know how I can make it search for packages and generate them? I know almost all the versions that come with my distro are correct, because the packages I'm trying to use are at least a couple of years abandoned.

Please help! :(

SphereCat1

---

### Post by SphereCat1 on 2008-08-11
Alright, lots going on! I'm still waiting for a replay on how to get everything to work, but I think I may have figured it out. I'll let you know as soon as I make some progress.

As far as the new design preview goes, I've pretty much finished it, but my jump drive just died, so I'm having some difficulty getting it down here to my internet computer. I just dug up a floppy disk, so I'll have it down here today! You're gonna love it. I promise. :)

SphereCat1

---

### Post by SphereCat1 on 2008-08-11
Wooooo! Here's the long-awaited complete concept drawing:
[URL="http://spherecat1.googlepages.com/tablewindowmanager.png"]
This is a link to a pretty picture.[/URL]
Click it! Click it! Click it!

[Bows] Thank you, thank you! [Bows again] :)

Anyway, here's a quick play-by-play:
- Notice the minimized window laying at the front of the table. (Slightly off-axis, I'll work on that later.)
- The two boxes in the middle of the screen can be used for storing just about anything. The one on the left is holding the stuff for a project, and the one on the right is set to show recent documents. (Hence the recent documents icon.)
- The icons that float on either side can be configured too, the left is showing drives with the text set to be on the right, and the right side is a sort of system tray. It order on the right: My logo, Trash (with the document count!), Help (glows when there's a tip), and a printer. (it's emblem is supposed to be a clock, i didn't have a clock icon.)

Also, none of these icons are the ones it'll come with, they were on my computer and I liked the style. I'm creating some that are almost the same.

Post lots of ideas! :)
SphereCat1

---

### Post by xakh on 2008-08-11
I still don't see a basic menu bar. Is it a right click menu, or what? This is all very well and good, but I would like a simple menu to find my things, then a cool layout to display them.

---

### Post by SphereCat1 on 2008-08-11
Well, I haven't decided what my logo does, maybe it can open a menu!

---

### Post by xakh on 2008-08-11
Perfect. That is exactly what I'd need. I'm all up for shifting the paradigm, but some things just work and work right, you know?

---

### Post by SphereCat1 on 2008-08-12
Mornin, I've got a great idea! A while ago, I remember seeing a preview of a new feature in Windows 7 for touchscreens, a little circular menu that would appear wherever your finger was.

What if we changed that idea slightly so that it would appear around your mouse when you right click? A round menu would be faster to navigate, since you'd just have to make a quick move in any direction to reach any of the menus, instead for moving along a bar. After you picked one, it could unroll into a submenu, or something like that.

I'll post a quick drawing later. (And maybe learn how to spell quick on the first try.) :)
SphereCat1

---

### Post by xakh on 2008-08-12
> **SphereCat1 said:**
> Mornin, I've got a great idea! A while ago, I remember seeing a preview of a new feature in Windows 7 for touchscreens, a little circular menu that would appear wherever your finger was.

What if we changed that idea slightly so that it would appear around your mouse when you right click? A round menu would be faster to navigate, since you'd just have to make a quick move in any direction to reach any of the menus, instead for moving along a bar. After you picked one, it could unroll into a submenu, or something like that.

I'll post a quick drawing later. (And maybe learn how to spell quick on the first try.) :)
SphereCat1

If you can do it, your window manager will be amazing.

---

### Post by SphereCat1 on 2008-08-12
Alright, everybody, I'm making a plea for help. I don't have internet on the computer I'm running Ubuntu on, and I've spent almost two weeks trying to get the right packages installed.

I'm trying to install backstep, and every time I do ./configure, it says gtk is not installed. Do I need the -dev version too? I've tried to install it, but the version in the repositories is newer than the normal gtk+ that came with dapper. What do I need to do to upgrade or find the older dev package?

Thanks,
SphereCat1

---

### Post by SphereCat1 on 2008-08-12
Never mind, Never mind!!! Cancel my last request! Everything is solved!

I've connected my Ubuntu machine to the internet temporarily, and I'm writing this post as half of my computer is upgraded!

WoooooooooooooooooooooooooooooooOOOOOOOOOOOOooooooooooooot! :):):):):)

SphereCat1

---

### Post by VitaLiNux on 2008-08-12
> **SphereCat1 said:**
> Mornin, I've got a great idea! A while ago, I remember seeing a preview of a new feature in Windows 7 for touchscreens, a little circular menu that would appear wherever your finger was.

What if we changed that idea slightly so that it would appear around your mouse when you right click? A round menu would be faster to navigate, since you'd just have to make a quick move in any direction to reach any of the menus, instead for moving along a bar. After you picked one, it could unroll into a submenu, or something like that.

I'll post a quick drawing later. (And maybe learn how to spell quick on the first try.) :)
SphereCat1
 SphereCat1,
That'd be awesome to see something like that! I'm subscribing this thread now to further know how you're doing with this idea! :)

---

### Post by SphereCat1 on 2008-08-12
Thanks for the support! I can always use more people contributing. Tell all your friends!

SphereCat1

---

### Post by SphereCat1 on 2008-08-12
WOOOOOOOOOOOOOOOOOOOOO! I got backstep running! WOOOO!

PYWM seems to be broken, so I installed a few others from the repositories while I was connected. I'll let you know what I end up doing.

Right now, however, I'm going to watch Chris Pirillo unbox the epic Optimus Maximus keyboard! 

SphereCat1

OMG he just ripped his toenail off! No, seriously!

---

### Post by lyceum on 2008-08-12
A few ideas

1. hot keys. I like your idea, and there needs to be a way to get to programs quickly without minimizing. I would say to make the main menu the super key, or apple key on a Mac. A table (similar to the one you have now) could pop up in the middle of the screen from nowhere with icons (accessories, games, office, computer, etc..). When you click on one of these, the others hop up and disappear (this could be customizable) and the programs in that category would appear with an arrow to lead back to the main menu. When something is selected, or the hot key is pressed, the table is gone. There should also be an applet or widget on the desktop somewhere that can load it with a mouse click. That is my idea to get rid of the gnome bar.

2. Icon. I love the cat in your avatar. If you made it, I would use that. If you did not and want help making an icon, let me know. I could help with that. 

3. Make sure everything works with Compiz so the icons can be 3D rather than flat. They could be made in Blender. I would love to see 3D icons in orbit around the cube :)

4. Let me know if you need help with art, making icons, etc.

Good luck, looks cool!

:guitar:

---

### Post by SphereCat1 on 2008-08-13
Good Morning, everybody! Let's begin, shall we?

lyceum:
Hot keys are a very good idea. I'll work on a keymap for navigating every aspect of the desktop. In fact, all your ideas are good! We need more people like you hanging around here.

I did make the logo for my avatar, I enjoy making shiny things in inkscape.

More news will come later today!
SphereCat1

---

### Post by lyceum on 2008-08-13
> **SphereCat1 said:**
> Good Morning, everybody! Let's begin, shall we?

lyceum:
Hot keys are a very good idea. I'll work on a keymap for navigating every aspect of the desktop. In fact, all your ideas are good! We need more people like you hanging around here.

I did make the logo for my avatar, I enjoy making shiny things in inkscape.

More news will come later today!
SphereCat1

Thanks. I'll be hanging around, as long as you keep posting. I am very interested in seeing a desktop manger that is nothing like Windows or Mac. I think you have a good idea here.

---

### Post by smartboyathome on 2008-08-13
SphereCat:

Basically, you are creating [BumpTop]("http://bumptop.com/") for Linux, aren't you? I think that is a very good idea, as the concept does look cool. If you are, check out that site.

---

### Post by lyceum on 2008-08-13
> **smartboyathome said:**
> SphereCat:

Basically, you are creating [BumpTop]("http://bumptop.com/") for Linux, aren't you? I think that is a very good idea, as the concept does look cool. If you are, check out that site.

that...is...sweet! 
:guitar:

---

### Post by indecisive on 2008-08-14
SphereCat1, would you mind attaching the actual picture of your window manager instead of posting a link?  My own security policy does not like following links to random homspun sites.
--edit--
(No offense intended)

---

### Post by SphereCat1 on 2008-08-14
Hi everyone!

BumpTop...Is...Awesome!!!! I suppose it's kind of like that, I can try to incorporate more of those ideas later it the development cycle.

I've been using FLWM for a couple of days, I like the general style, but it would need a lot of work to be our window manager. Backstep doesn't work with it either. Luckily, they're both written in C++, so it should be easy to combine them permanently. Unluckily, I don't know C or C++, and the last time I tried to learn them, my brain nearly exploded. But, that was a long time ago, so it can't hurt to try again.

Also, I have the name for it, I've had it for a while, I just forgot to post it: TWiMU (It stands for Table Window Manager Ultra. Hopefully that's one of those things that gets lost in the mists of time...) :)

SphereCat1

---

### Post by lyceum on 2008-08-14
> **SphereCat1 said:**
> Hi everyone!

BumpTop...Is...Awesome!!!! I suppose it's kind of like that, I can try to incorporate more of those ideas later it the development cycle.

I've been using FLWM for a couple of days, I like the general style, but it would need a lot of work to be our window manager. Backstep doesn't work with it either. Luckily, they're both written in C++, so it should be easy to combine them permanently. Unluckily, I don't know C or C++, and the last time I tried to learn them, my brain nearly exploded. But, that was a long time ago, so it can't hurt to try again.

Also, I have the name for it, I've had it for a while, I just forgot to post it: TWiMU (It stands for Table Window Manager Ultra. Hopefully that's one of those things that gets lost in the mists of time...) :)

SphereCat1

TWiMU... I like the look of it. How do you pronounce it? (twh'i-moo)? Would you mind if I tried to come up with a few logo ideas?

---

### Post by xakh on 2008-08-14
I quite like TWIMU, it has a ring to it. If there is anything at all I can do to help, I'd be more than glad to do it!
List of things I can do:
Model in Blender
Make vector graphics
Contribute anything you'd like from my page on DA as a background, or otherwise.
(xakh.deviantart.com)
I'm okay with 2D work
My uncle's a professor at Stanford, so I can ask for his help if need be.
Oh! and I'm really freaking enthusiastic about this! Ingenious plans there, Spherecat1, and I'm willing to do whatever.

---

### Post by SphereCat1 on 2008-08-14
Wow! I didn't think anyone would really like the name... and yes, that's how you pronounce it, although I would have done the pronunciation key like this: Tweemoo. ;)
Feel free to create some logos, bye the way.

And xakh, thanks very much for all the support! Now I really hope I can end up finishing this... :)
I have a feeling you're 3D modeling will come in handy in the near future.

More prototypes to come soon! (Gotta finish my icon theme.)

Thanks again everyone! :)
SphereCat1

---

### Post by SphereCat1 on 2008-08-16
Hi everyone! I've been working on a logo without much success, hopefully lyceum is having more luck.

In other news type stuff: What if we also made a tablet/portable version of this, with kind of a rotating plate for quick access on a touchscreen or devices with a navigation disk? Just a thought.

SphereCat1

---

### Post by smartboyathome on 2008-08-16
Someone call for a logo? Here's my idea. :D

---

### Post by SphereCat1 on 2008-08-16
Nice work! I'm not sure that It's immediately obvious that it's for a window/desktop manager though... It looks like a logo for a file manager. Maybe if it was a window instead of a file cabinet? I'll keep this one, though, if we do a file-management utility, or something along those lines, it'll work perfectly! :mrgreen:

Thanks again,
SphereCat1

---

### Post by smartboyathome on 2008-08-16
Here ya go, this one with a window. :)

---

### Post by SphereCat1 on 2008-08-16
Really close, here's the same thing, slightly edited. Does everyone like it?

---

### Post by darthchaosofrspw on 2008-08-16
> **SphereCat1 said:**
> Hi everybody! I'm new to Ubuntu, but I have some experience with Puppy Linux. Anyway, I want to try to write a new Window Manager, and I picked Ubuntu as my development platform because it comes pre-packed with so many tools.

The basic concept is kind of like the OS X dock in leopard: the desktop is a huge table that you can place icons and windows on, and it can be as big or small as you want.

There will also be a method of grouping items called Palettes, but I'm not exactly sure how they work yet.

Anyway, I'm creating this thread for any ideas or suggestions, just a general wish list. I'll make everything I can happen. This was going to be in programming, but I figured it's more about making things look good than anything else.

Post whatever comes to mind, I'm open to just about anything!
SphereCat1 :)

Something like Macpup? I think an Ubuntu-based derivative using a Mac-flavored version of JWM (with the OSX-like dock included in Macpup) would be neat.

Oh, just read the thread. Never mind. But still, a Macpup-like Ubuntu would be neat.

---

### Post by lyceum on 2008-08-17
> **SphereCat1 said:**
> Really close, here's the same thing, slightly edited. Does everyone like it?

I like that it has a table under it, but do not think it really stands out. Gnome has a foot and KDE has gears. The sketches I have been doing are along that line, I have been trying different things that I think of what I say TWiMU. unfortunately, a cow has been taken. I am going to use the table as a base idea. I like that a lot.

:)

---

### Post by SphereCat1 on 2008-08-17
Cool, cool. I agree, lyceum, after looking at it, it isn't really noticeable. People need to remember our logo.

Today, I'm working on the icons.
SphereCat1

---

### Post by murriano on 2008-08-17
Hey, this looks insane! Im am really, REALLY!, looking forward to seeing this, and even though I am no programmer, I offer up my services to beta test  for ya. Ill try and see too if there are ways for me to help out even more as time goes on. 
Thanks for making something so awesome!!

---

### Post by xakh on 2008-08-17
> **lyceum said:**
> I like that it has a table under it, but do not think it really stands out. Gnome has a foot and KDE has gears. The sketches I have been doing are along that line, I have been trying different things that I think of what I say TWiMU. unfortunately, a cow has been taken. I am going to use the table as a base idea. I like that a lot.

:)

What of a bird? that or a tree. Both of those come to mind for me from TWiMU. I'd think a bird would make sense, with a slogan like "leave the nest, beat the rest!" I know, it's dorky, but we're brainstorming, right?

---

### Post by Neon Lights on 2008-08-17
A bird definitely comes to mind when I think of the word TWiMU. It's just kinda of the sound they make. xD Or a mouse. A mouse would be cool. :D haha

---

### Post by smartboyathome on 2008-08-17
> **Neon Lights said:**
> A bird definitely comes to mind when I think of the word TWiMU. It's just kinda of the sound they make. xD Or a mouse. A mouse would be cool. :D haha

Mouse already taken by XFCE. :p

---

### Post by lyceum on 2008-08-17
> **xakh said:**
> What of a bird? that or a tree. Both of those come to mind for me from TWiMU. I'd think a bird would make sense, with a slogan like "leave the nest, beat the rest!" I know, it's dorky, but we're brainstorming, right?

I really like the bird idea. After all, it will fly out at you :) That gives me some new ideas . . .

---

### Post by peruvianfreak250 on 2008-08-17
cool, this look like this is going to be awesome :)
im with murriano, im no programmer but im willing to help out any way i can
:popcorn:

---

### Post by SphereCat1 on 2008-08-17
Wow, lots of replies! I'll be back in the morning, the bird idea gave ME an idea.

SphereCat1

---

### Post by Neon Lights on 2008-08-17
> **smartboyathome said:**
> Mouse already taken by XFCE. :p
Dangit you're right.
The little DE that could. xD
But yeah, the bird would work. ^_^ Can't wait to see whatcha got SphereCat. :]

---

### Post by ianchristie on 2008-08-17
Hey, love the idea. SphereCat1, you mentioned a round menu that comes up when you right click, that reminded me of a DE I tried a long time ago, UDE (Unix Desktop Environment). it uses a menu that is a series of hexagons in a circular pattern. I think it's in the Ubuntu repositories.

[http://udeproject.sourceforge.net/images/screenshots/ude029.1.jpg](http://udeproject.sourceforge.net/images/screenshots/ude029.1.jpg)

I love your ideas and would love to help test it as well.

---

### Post by Sorivenul on 2008-08-18
I've been watching this thread for days.  6 pages in, and my question is, who's going to code, and when is that going to start?  Not trying to cause a fight, as artwork and icons are needed, but aren't they more they icing on the cake?  Just my two cents.

---

### Post by SphereCat1 on 2008-08-18
Mornin! I've been doing some sketching, (alright, inside my head. what do you want from me??!?!?!?! :)) and I've come up with one I kind of like. I'll see what I can do to get it on paper, I'm not very good at drawing what's in my head.

It can't look too much like the bird on Twitter's homepage, we don't want to confuse anyone. I think a robin would look good, maybe perched on the edge of the desk?

Keep posting more ideas! :)
SphereCat1

P.S.: I'll try to post a new concept drawing too, probably of the taskbar-type area.

EDIT: Sorivenul, sorry! I completely missed that there was a new page, so I forgot to answer your question!
At the moment we're mostly working on the look and feel, so we know what window manager's doe would be easiest to work off of. Once we figure that out, I'll be putting together a basic version, and we'll expand that with OpenGL and the like.

I've been trying several window managers, and I think FVWM is going to have another derivative. UDE might be a good one to build the desktop portion off of.

I'll of course accept any ideas from the community, and code, too. Once I have my website, SphereCat1.com up and running, it'll be there too.

By the way, everybody, should we make a sourceforge page or something like that? Or should it just get hosted on my site?

---

### Post by Sorivenul on 2008-08-18
> **SphereCat1 said:**
> I've been trying several window managers, and I think FVWM is going to have another derivative. UDE might be a good one to build the desktop portion off of.
UDE is a fine piece of work if it will still compile.  I've had problems with it in some instances on different distributions.  FVWM is an interesting choice, but from what I've read here seems in keeping with your project goals.
> **SphereCat1 said:**
> By the way, everybody, should we make a sourceforge page or something like that? Or should it just get hosted on my site?
SourceForge has great traffic and maintainability as it can be administered by whoever you wish.  I'm not sure how many hits your personal site receives or will receive on a daily basis, but having a centralized location like SF would not be a bad move IMO.

---

### Post by SphereCat1 on 2008-08-18
What license does everybody think we should put on it?

EDIT: I'm gonna go with the GPL, it's probably the best way to do this.

---

### Post by SphereCat1 on 2008-08-18
Ok, I've created a SourceForge project, it's pending for approval. Once it's up it'll be at [sourceforge.net/projects/twimu]("http://www.sourceforge.net/projects/twimu"). :)

SphereCat1

---

### Post by Sorivenul on 2008-08-18
Glad you got the SF page submitted for approval.  Good first step.  Also the GPL is probably the best bet for this project as the other two projects are released under the GPL as well, if I remember correctly - good call.

---

### Post by SphereCat1 on 2008-08-18
Alright, I've also requested takeover of the backstep project, this will make it easier to work on that portion of the project.

Still working on the logo! :)
SphereCat1

---

### Post by SphereCat1 on 2008-08-18
Maybe a drawing of [this bird]("http://www.digital-nature-photography.com/nature/showeng.php?id=GR10/GRBGH230708-7661&info=Twite") could be used as our logo?

---

### Post by picpak on 2008-08-18
I've always wanted a window manager with proper support for transparent pixmaps, so we can create more of a Compiz feel without using Compiz. Would this sort of thing be possible to do?

---

### Post by SphereCat1 on 2008-08-18
Great news, everybody! We're now on SourceForge! twimu.sourgeforge.net is the spot, though there's not much there yet... :D

Oh, and PicPak, I'll move transparent pixmaps to the top (ish) of my list. That's a good thing to focus on, since everything will be rendered in 3D. :)

SphereCat1

EDIT: Just finished reading the E-mail, twimu.sourceforge.net wont be available until probably tomorrow, so try sourceforge.net/projects/twimu for now. Still says pending, but once it figures it out I'll move the concept drawing there, too.

---

### Post by smartboyathome on 2008-08-18
> **picpak said:**
> I've always wanted a window manager with proper support for transparent pixmaps, so we can create more of a Compiz feel without using Compiz. Would this sort of thing be possible to do?

It has already been done with the (now ancient) project 3Dwm. You cannot find much online (project page [here]("http://www.cs.chalmers.se/~elm/projects/3dwm/"), though the source is still available on Launchpad.

---

### Post by picpak on 2008-08-18
> **smartboyathome said:**
> It has already been done with the (now ancient) project 3Dwm. You cannot find much online (project page [here]("http://www.cs.chalmers.se/~elm/projects/3dwm/"), though the source is still available on Launchpad.

Um, yeah, that's pretty ancient. Not to mention the few screenshots I found were pretty ugly. I'd like something looking like this: [http://www.compiz-themes.org/content/show.php/WhiteMod?content=64829](http://www.compiz-themes.org/content/show.php/WhiteMod?content=64829) while still being modern and lightweight.

 > **SphereCat1 said:**
> Oh, and PicPak, I'll move transparent pixmaps to the top (ish) of my list. That's a good thing to focus on, since everything will be rendered in 3D. :)

Will it work without 3D? My crappy graphics card won't even use direct rendering...

*needs new graphics card*

---

### Post by SphereCat1 on 2008-08-18
I can guarantee it'll run without a graphics card, I'm developing on the machine in my signature, a G3 PowerBook.

---

### Post by picpak on 2008-08-18
> **SphereCat1 said:**
> I can guarantee it'll run without a graphics card

Yes! Telepathic communications FTW! :lolflag:

---

### Post by lyceum on 2008-08-18
> **SphereCat1 said:**
> Maybe a drawing of [this bird]("http://www.digital-nature-photography.com/nature/showeng.php?id=GR10/GRBGH230708-7661&info=Twite") could be used as our logo?

Okay, good news/bad news. I have a really good drawing of the logo done. It is a humming bird hovering over a table, well the top of one, like the previous designs. Bad news, I moved over the weekend and cannot find the box with the scanner. I am working on remaking it on my laptop w/out the scanner. I am going to try to have it done by Wednesday.

---

### Post by picpak on 2008-08-18
I was bored and made this in 5 minutes. It's a bird sitting on a title bar.

---

### Post by smartboyathome on 2008-08-18
> **SphereCat1 said:**
> I can guarantee it'll run without a graphics card, I'm developing on the machine in my signature, a G3 PowerBook.

If you can guarentee that, then you will have to use psuedo transparency, as real transparency requires a graphics card, and is very slow on Intel-based cards. If you are going the psuedo transparency route, check out FVWM Crystal.

---

### Post by SphereCat1 on 2008-08-19
Hi again! Thanks for all the work, lyceum, and I hope your new place is really nice.

Picpak, I like the titlebar idea, the bird...needs some work. :)

I've got some experience in Java with fake transparency, I'll just have to learn how to do it in FVWM's language of choice. Not sure what that is yet, all I know is that I probably don't know it. But, I shall learn. Curse BASIC for making it harder for me to learn real languages!
SphereCat1

P.S.: twimu.sourceforge.net is up now, I'll build us a page.

---

### Post by picpak on 2008-08-19
> **SphereCat1 said:**
> Picpak, I like the titlebar idea, the bird...needs some work. :)

All it was was a set of circles drawn on Kolourpaint. I could do way better. :lolflag:

---

### Post by emshains on 2008-08-20
> **Merk42 said:**
> In Windows (or OSX, GNOME, KDE XFCE...) you can see what apps are running while a full screen application is running.  You can also easily get to a menu to run another application in any of those other environments.

If I run a game in fullscreen, it would start a new X server, and you couldnt access any of the kde or gnome interface.

---

### Post by emshains on 2008-08-20
> **picpak said:**
> I was bored and made this in 5 minutes. It's a bird sitting on a title bar.

I'd suggest a tux (the penguin) rather a bird.

---

### Post by lyceum on 2008-08-20
> **emshains said:**
> I'd suggest a tux (the penguin) rather a bird.

I think tux has been taken. What was that program using a penguin? ;)

---

### Post by lyceum on 2008-08-20
Update, I am more than half done with the logo, and it is looking good, IMHO. I am hoping to finish it tonight, but I will be working late. I got the hardest parts done last night, so a few more hours should be all I need to finish. If it gets too late when I am done I will post it here first thing Thursday morning, EST. Hope the coding is going well. I did find my scanner, so if anyone wants to see a pencil sketch, I can put one up after I get off work tonight. I figured that one more day is not much of a wait, so I have not scanned it.

---

### Post by SphereCat1 on 2008-08-20
Hi everybody! I'm back on my PowerBook, I connected it to the internet again So I could install some more stuff. The coding is going well, if you consider not doing anything going well. ;)

No, but seriously, coding will probably start today. I'm fairly happy with FVWM as a base, I can always mix in other stuff later. I do like FLWM, too, but it's not as flexible. (At least not when you don't know much of C++. :))

lyceum, don't work too hard on the logo, we don't need anyone going without sleep for this project. Not yet anyway.

Does anyone else have ideas for code to mix in, before I get started? I'll be online here until about 2:00, but I'll be back later, too.

SphereCat1

I wonder if Runescape will work on here... Must...stay...focused!

---

### Post by Sorivenul on 2008-08-20
> **SphereCat1 said:**
> I do like FLWM, too, but it's not as flexible. (At least not when you don't know much of C++. :))
First, which version of FLWM are you working off of, because from most of what I can tell it's in C and not C++.  Also, how familiar are you with the FLTK as far as writing/extending the WM functionality goes?  Just jumping blindly into the code, no matter how well commented, is NOT a great idea.  

> **SphereCat1 said:**
> Does anyone else have ideas for code to mix in, before I get started?
As an extension to my above response, make sure the base code compiles before you even think about making additions/modifications.  Also with something as comeplex (and sensitive) as a WM, especially one in a language you can easily shoot yourself in the foot with, you can't just throw a chunk of code in here and there.

Again, just my two cents, and I'm sure I'll have more questions, comments, but really they are only meant to help the project.

---

### Post by SphereCat1 on 2008-08-20
I appreciate your 2 cents, it's helping to keep me from screwing this up majorly. :)

> **Sorivenul said:**
> from most of what I can tell it's in C and not C++.
Like I said, I don't know much. I'm going to attempt to learn C again as I go, we'll see how well that ends up working.

I fact, this is my first time with most of this, but I'm a fast learner. That's why I'm just starting with creating the base WM, and then making it 3D and such. If you know of any tutorials you think it would be a good idea for me to read, send them along. :)

By the way, I'm upgrading to 8.04, so I might be out of commission for a bit.
SphereCat1

---

### Post by smartboyathome on 2008-08-20
SphereCat: Like I said, look at FVWM-Crystal. It uses psuedo transparency and is based on FVWM. It should provide you with clues on how to do this. :)

---

### Post by lyceum on 2008-08-20
I do not consider this finished, but I have to stop for now. Let me know what improvements are needed. This is only the third time I have used Inkscape, so it is not prefect.

[IMG]http://www.whitetreeevolution.com/pictures/bird4.png[/IMG]

---

### Post by picpak on 2008-08-20
I love it!

It's a hundred times better than mine :lolflag:

---

### Post by Sorivenul on 2008-08-20
lyceum, great logo!  It will be even more beautiful when tuned to perfection.  

SphereCat1, aside from hacking most of the WMs available for download, I've done some window manager work before and I think I can really help on this.  If we go with FVWM instead of FLWM, things would be much easier in my opinion.  FVWM dependencies center mostly around standard libs and Xlib, so what little "bloat" there would be could come from the effects and "table".  

Some helpful introductions/tutorials regarding this project would be:
[http://www.cs.utk.edu/~eijkhout/OSX/fvwm-man.pdf]("http://www.cs.utk.edu/~eijkhout/OSX/fvwm-man.pdf") - FVWM general tutorial/manual
[http://www.fvwm.org/documentation/perllib/tutorial.php]("http://www.fvwm.org/documentation/perllib/tutorial.php") - FVWM module writing tutorial
[http://www.linuxjournal.com/article/1236]("http://www.linuxjournal.com/article/1236") - Customize FVWM setup
[http://www.linux.com/feature/114067]("http://www.linux.com/feature/114067") - Customize FVWM setup even more
[http://www.fvwm.org/documentation/developers.php]("http://www.fvwm.org/documentation/developers.php") - From the FVWM developers themselves
[http://zensites.net/fvwm/guide/]("http://zensites.net/fvwm/guide/") - Great FVWM guide covering many topics
[http://www.x.org/docs/X11/xlib.pdf]("http://www.x.org/docs/X11/xlib.pdf") - Getting started with Xlib from x.org
[http://tronche.com/gui/x/xlib/]("http://tronche.com/gui/x/xlib/") - Xlib manual (Fantastic)

That should keep you busy for a while.  If you want to enlist my help, all you need to do is ask.  I'm sure the folks over on Programming Talk may have a few ideas of their own if you're interested.

---

### Post by peruvianfreak250 on 2008-08-21
> **lyceum said:**
> I do not consider this finished, but I have to stop for now. Let me know what improvements are needed. This is only the third time I have used Inkscape, so it is not prefect.

[IMG]http://www.whitetreeevolution.com/pictures/bird4.png[/IMG]

awesome!

---

### Post by SphereCat1 on 2008-08-21
Hi everybody! I'm with peruvianfreak250: awesome! I absolutely love it! This logo will strike fear into the hearts of other window manager devs! :lolflag:

Sorivenul: Thank you so much! You're right, that will definitely keep me busy for a while.

> If you want to enlist my help, all you need to do is ask.
In that case, welcome to the team! We need as many people like you as possible!

smartboyathome: I'll download FVWM-Crystal as soon as I'm done with dinner. Pancakes FTW!

SphereCat1

---

### Post by Sorivenul on 2008-08-21
SphereCat, let me know if you decide to go with FVWM-Crystal over FVWM.  From there we can work out a version to fork from/hack/rewrite.  Have fun with your pancakes.  Tabouli salad FTW!

My personal vote lies with FVWM standard.  Crystal depends on FVWM anyway, adding unneeded bloat at a much earlier stage of development when much will be added with the later creation of the rest of the system, table, etc.  Just my two cents, and as the project leader, it's ultimately your call.

---

### Post by SphereCat1 on 2008-08-22
You have a good point there, we need to keep this as small as possible... I'm still gonna download Crystal to check it out, but I'm thinking it would just be easier to build in our own transparency.

My laptop is totally out of commission at the moment, Hardy has a semi-known-but-unfixed issue with my graphics system... I posted on an older thread where someone had the same issue: [http://ubuntuforums.org/showthread.php?p=5642740]("http://ubuntuforums.org/showthread.php?p=5642740")

I'm downgrading until I get a reply. :|
SphereCat1

---

### Post by Sorivenul on 2008-08-22
Not a problem.  Crystal is good for light eye-candy, but still requires FVWM to be installed as a base. Transparency is possible to work in, though my experience on that end is limited - oh, well, something new to learn.  The version of Crystal in 7.10 or 7.04 should be nearly the same if not the same as in Hardy as far as your evaluation goes.  When you make a decision or if you have more questions, let me know.

---

### Post by SphereCat1 on 2008-08-22
Ok, does anyone know if the upgrade distro feature of update manager even works on PowerPC??? I know this is off topic, but It would be nice to have access to some newer repositories.

I may just burn a Fiesty CD.

---

### Post by Sorivenul on 2008-08-22
Worked for me on my Mac, but I ran an Intel, not PPC.  However, I would suspect it should work for you.

---

### Post by SphereCat1 on 2008-08-22
Well, I'm burning gutsy to a CD to see if it'll work, I hope it does, that way I can have everything I need upgraded for my road trip tomorrow. Five hours of coding!
I'm probably not going to install Crystal, I don't want to deal with dependencies at the moment.

Booting right now!
SphereCat1

P.S.: Gnomedex 8.0 is live right now on [live.pirillo.com]("http://live.pirillo.com/"). Check it out!

EDIT: It completely failed, I'm sticking with Dapper for now.

---

### Post by collinp on 2008-08-23
I saw that you got a website at sourceforge, and that is had no web page :b. I know quite a bit of HTML and CSS, and I was wondering if i could build your sourceforge webpage for you? Just tell me what you want and I can do it :D.

---

### Post by SphereCat1 on 2008-08-24
Thanks for voluentering Hellow! Feel free to design a website, I'm busy with everything else at the moment.

I'm working on getting FVWM up and running, and I got UDE to compile, so I'll let you know more when I get back.
SphereCat1

---

### Post by Sorivenul on 2008-08-24
Let me know which version of FVWM you decide to work with.  Sometimes the latest is not the best.  I'll do some research.

---

### Post by SphereCat1 on 2008-08-24
I have downloaded the latest version, it's not stable, but it has a LOT of new features. I've started reading through the code to get a general idea of the workings, but I wish I had my C books with me. At least it's well commented.

I'm also running whatever version was in the dapper repositories right now, and I'm messing with the configuration. It's really easy to work with the files, we need to keep that for our version. Probably a graphical configuration interface, too.

I'll try to get at least one more update up before I leave here.
SphereCat1

P.S.: I've read 3 of the six tutorials you linked to, I've downloaded them as PDFs, they've been awesome! Thanks so much! :)

---

### Post by Sorivenul on 2008-08-24
> **SphereCat1 said:**
> I have downloaded the latest version, it's not stable, but it has a LOT of new features. I've started reading through the code to get a general idea of the workings, but I wish I had my C books with me. At least it's well commented.

I'm also running whatever version was in the dapper repositories right now, and I'm messing with the configuration. It's really easy to work with the files, we need to keep that for our version. Probably a graphical configuration interface, too.

I'll try to get at least one more update up before I leave here.
SphereCat1

P.S.: I've read 3 of the six tutorials you linked to, I've downloaded them as PDFs, they've been awesome! Thanks so much! :)

I suggest the 2.4.20 or 2.4.0 release to work off of.  It's been a while since I've worked with FVWM myself and am in the process of installing/configuring at the moment myself.  I think we can work out an interface to easily modify those files, similar to fluxconf or obconf.  The code is relatively well commented as far as window managers go, so that will be a major help.

The xlib tutorials were indispensable to me with my other WM work.  I'm glad to pass on the knowledge.  

I'm doing some research and comparison on versions thanks to Giles Orr's great website.  I'll let you know what my benchmarks of the various versions are as I get things worked out.   

Also, before you leave or while you're gone it may be worthwhile to work out a list of "Project Goals", so we don't become just another DE/WM project.  What will make TWiMU different, possibly better than other environments?  Are we aiming for a balanced usage or one leaning more toward usability or speed?  How much bloat are we willing to add with the creation of the full DE?  These are just a few questions I've thought of the past day or so and will probably post more as time goes on.  It may be worthwhile to set up a developer mailing list over on SF to aid this process as more people join the team.  

Okay, I think that's all I have for now.

---

### Post by d0nut on 2008-08-25
> **SphereCat1 said:**
> Wow, lots of replies! I'll be back in the morning, the bird idea gave ME an idea.

SphereCat1

I also like the bird idea.  When I think of TWiMu, I think of "tweet" (the sound a bird makes)) and also "Emu" (a type of bird).  I'll be interested to see what you come up with!

---

### Post by michaelbogardus on 2008-08-25
> **Sorivenul said:**
> 
Also, before you leave or while you're gone it may be worthwhile to work out a list of "Project Goals", so we don't become just another DE/WM project.  What will make TWiMU different, possibly better than other environments?  Are we aiming for a balanced usage or one leaning more toward usability or speed?  How much bloat are we willing to add with the creation of the full DE?  These are just a few questions I've thought of the past day or so and will probably post more as time goes on.  It may be worthwhile to set up a developer mailing list over on SF to aid this process as more people join the team. 
Good point, seeing as many are getting ahead of themselves, in working more on the overall package, then what this actually does.

---

### Post by Sorivenul on 2008-08-26
> **michaelbogardus said:**
> Good point, seeing as many are getting ahead of themselves, in working more on the overall package, then what this actually does.

I think I'm full of good points most days.  I think SphereCat1, myself, and a couple others have a good grasp on the answers to my questions, I just think it would be good to write them down in an organized, easy-to-follow, easy-to-understand fashion.

After some testing I'm leaning more toward the 1.24r version of FVWM if you decide against Crystal.  Of the 2.x branch, I see 2.4.20 as the more promising release.  

I have some more interesting ideas involving the table, background/wallpaper, use of icons, etc when we finally get some of those questions from my last post answered.

---

### Post by SphereCat1 on 2008-08-26
Hi everybody, I'm officially back to the lab! (den.)

I'll work on a first draft of features and goals, that's a really good idea. Also, I've almost finished the tutorials, now I just have to learn C! :lolflag: Luckily, it IS well commented.

d0nut: Someone else I know mentioned an Emu, but they aren't an extremely good looking bird...

As far as versions, I'm currently running 2.5.14, it hasn't crashed once. Has a couple bugs, but otherwise it's pretty good. What are your reasons for 1.24? Just curious. Maybe an older version would be more flexible?

I'll get the first (very) rough draft up ASAP! :)
SphereCat1

P.S.: I went to my first Apple Store today! One word: SHINY!!!

---

### Post by damis648 on 2008-08-26
> **SphereCat1 said:**
> P.S.: I went to my first Apple Store today! One word: SHINY!!!

Yes, they have very good looking products. The store is well-designed too. On this project, I do not know C or anything like that, so I probably would not be much help in that department, but I would like to test your SVN releases and betas and such, so I am here for that. I also have a friend who is a **phenomenal** artist, he can draw anything more perfect than perfect. If you would like any sort of artwork, let me know, and I will see what I can do. Cheers!:popcorn:

---

### Post by Sorivenul on 2008-08-26
SphereCat1, glad you're back.

My reasoning for 1.24r would be it is more minimal.  In theory this works better as a base to expand upon and can probably support some of the additions made in the 2.x releases if we would wish.  Also, it the last version released by the originator of FVWM(1).  

Giles Orr has an interesting article on the 2.x series of FVWM that I think is worthwhile.  There are some interesting aspects of FVWM(2) that I would think very appropriate for this project.  The article is available [HERE]("http://gilesorr.com/papers/otherwm2003/x377.html"). Also, while you're there it may not be a bad time to check out more of the WM history, etc.  Also, a general WM review including both tracks of FVWM is available at freshmeat [HERE]("http://freshmeat.net/articles/view/639/").

I'd be interested in a full FVWM Wiki, which might not be a bad idea to include on the SF site.  I could definitely help this this aspect.  

Also as far as C goes, I'm trying to dig up some old tutorial I had to post here or send you.  I'm fairly proficient with C, though it's been a while since I've done major development, especially on a project of this magnitude.  Hit me up for advice and assistance. 

I think that's about it for now.  Oh, and be expecting a request on SF to add me (nql) to the team within the next day or so.

---

### Post by skyreeds on 2008-08-26
i'm also quite interested in your idea.
anything a new desktop manager is an innovative yet chanllenging job,where more people should join in.
my email: [email]skyreeds@gmail.com[/email]

---

### Post by SphereCat1 on 2008-08-27
Alright! The first draft of the features list is up on our newly created SourceForge wiki! ([twimu.wiki.sourceforge.net]("http://twimu.wiki.sourceforge.net/")) (It's in the sidebar.) :)

I've also created a page where new features can be [discussed]("http://twimu.wiki.sourceforge.net/SuggestedFeatures").

More after I get back from dinner.
SphereCat1

---

### Post by collinp on 2008-08-27
Sorry that it took me an *extremely *long time to reply, but I am getting to work on your website right now :). I have been busy with school and such, and I have not had much free time. Expect the website to be finished (with the information that I have) by this weekend, maybe earlier.

---

### Post by Sorivenul on 2008-08-27
SphereCat, I'm glad you have the first draft of the project goals posted.  It looks like FVWM is definitely the way to go.  To achieve your goals, I definitely think the 2.x series is the way to go - a lot of the work is already done.  If you want to work off of the latest development branch I'll download and get to work.  As far as extending functionality I'm studying Perl module additions amongst other things.  Also, the behavior of FVWM to minimize applications to an icon on the desktop might play to our favor in "placing" an application on the "table".  I'm also studying FVWM themes, as it has a history of being one of the most easily themed WMs out there.  Also, I just sent you a mail message on SourceForge requesting to be added to the team.

---

### Post by SphereCat1 on 2008-08-27
Hellow: Thanks for all the work! Don't worry, I understand, I'm starting school again in a week. :(

Sorivenul: You're now a developer on the project, and you can post news, edit the wiki, and you're a mod on the forums (which we'll eventually use...)
As far as extensions, I'm also slowly learning Python, so we're pretty well covered on that front, though Python support will have to be implemented first.

I've started on my C For Dummies book again, I'll let you know how it's going in the morning.
SphereCat1

P.S.: I'm still waiting to get complete control over the Backstep project. We don't really need it at this point, but it has that code for getting the thumbnails of windows, so we can add that to FVWM's desktop icons thing.

---

### Post by Sorivenul on 2008-08-27
> **SphereCat1 said:**
> Sorivenul: You're now a developer on the project, and you can post news, edit the wiki, and you're a mod on the forums (which we'll eventually use...)
Awesome, thanks!
> **SphereCat1 said:**
> As far as extensions, I'm also slowly learning Python, so we're pretty well covered on that front, though Python support will have to be implemented first.
Python support can be implemented, though a Perl module is already available for extensions from CPAN.  See information here: [http://www.byz.org/~randy/perl/X11::Fvwm/]("http://www.byz.org/~randy/perl/X11::Fvwm/")

---

### Post by collinp on 2008-08-27
Maybe you might want to take come code from Enlightenment, it looks pretty good and it may help you along with making your WM.

---

### Post by Sorivenul on 2008-08-27
> **Hellow said:**
> Maybe you might want to take come code from Enlightenment, it looks pretty good and it may help you along with making your WM.

Nice thought, though I don't think Enlightenment is compliant enough for our tastes, at least the e16 release isn't from included documentation.  FVWM is more easily extended and configured.  While e16/e17 have great effects and compositing potential, FVWM is easily extended and more suitable as a base WM underneath a DE, such as Sawfish formerly was for Gnome.  Will have to consider this more, though.  Thanks!

---

### Post by smartboyathome on 2008-08-28
I would say don't go with Enlightenment. Its in constant flux (e17 is), and E16 is over 10 years old. I would say stick with FVWM.

---

### Post by Sorivenul on 2008-08-28
> **smartboyathome said:**
> I would say don't go with Enlightenment. Its in constant flux (e17 is), and E16 is over 10 years old. I would say stick with FVWM.

Ha ha, thanks.  After a bit more looking at e16, I was about to come back and make this exact point.  And, yes, e17 is way too unstable to pull anything worthwhile from.  FVWM is a more than capable WM in the right hands, and with enough time.  This project isn't going to happen overnight.  No "Happy August 27th!  TWiMU 0.0.1 is released!".  Thanks for the input!

---

### Post by lyceum on 2008-08-28
> **Hellow said:**
> Sorry that it took me an *extremely *long time to reply, but I am getting to work on your website right now :). I have been busy with school and such, and I have not had much free time. Expect the website to be finished (with the information that I have) by this weekend, maybe earlier.

I am guessing by the reaction I got TWiMU will be using the logo I created, if that is so, let me know if you need a svg copy for the website. I am working on another project right now and still unpacking from moving, so I hope to make the final touches to the logo next week.

---

### Post by SphereCat1 on 2008-08-28
I'm happy to report that I've done nothing all day so far. :)

Currently I'm working on a theme for SphereCat1.com when it launches. It might be a while off yet, but hopefully it won't be too long. TWiMU will get it's very own spot there too, probably at projects.SphereCat1.com/twimu, although the layout isn't finalized yet.

Anyway, I'll let you know of any developments, as usual.
SphereCat1

---

### Post by Sorivenul on 2008-08-29
SphereCat1, I've downloaded the source for FVWM 2.5.26.  I'm moving forward with reading all the included documentation.  I will make notes, highlighting key points of interest to us, to stabilize, expand upon, strip, etc.  If there is a specific document format you would like me to use during the process or when I forward the finished "preliminary survey" to you, let me know.

---

### Post by SphereCat1 on 2008-08-29
The only format that will be required will be the English language. :D

Thanks for all the work, I'll start being useful here as soon as I get farther into my C books...

Pizza for dinner! Then C! Then sleep! :)
SphereCat1

---

### Post by Sorivenul on 2008-08-29
I can do English.  :)  Keep me updated on your C progress.  If you relatively simple questions, you can ask me, otherwise the Programming Talk forum might be the place to go.  We can probably also contact the FVWM maintainers if there is something specific we don't understand.

---

### Post by SphereCat1 on 2008-08-30
Sounds good to me! :)

---

### Post by lyceum on 2008-08-31
> **SphereCat1 said:**
> I'm happy to report that I've done nothing all day so far. :)

Currently I'm working on a theme for SphereCat1.com when it launches. It might be a while off yet, but hopefully it won't be too long. TWiMU will get it's very own spot there too, probably at projects.SphereCat1.com/twimu, although the layout isn't finalized yet.

Anyway, I'll let you know of any developments, as usual.
SphereCat1

Any art work you need help with, please let me know.

---

### Post by SphereCat1 on 2008-08-31
Hi everybody! I'm currently waiting on C for Dummies, 2nd Edition to arrive at my doorstep. Once that gets here, I can finally get started coding.

lyceum: I'll be happy to keep you posted. :)

Some bad news, however: I start school again in 2 DAYS! :( Sob...
SphereCat1

---

### Post by Sorivenul on 2008-08-31
Just occurred to me, but have you checked out the C programming links on LaRoza's site?

[http://laroza77.wikidot.com/c]("http://laroza77.wikidot.com/c")

A great place to get started while you wait for your book.  In fact, you may find you don't even need it.  :)

---

### Post by Tuxoid on 2008-08-31
I think it's that in recent times, Linux users and developers are talking much more about usability, but the issue that this particular may face is the fact the desktop metaphor only really facilitates the top of a work desk.

The top of a work desktop was traditional meant to be used to do any work that required paper. Therefore, to emulate something similar, In the late 1970's, Xerox created the Xerox Star Desktop. This was the first ever, full-fledged, Graphical User Interface (as NLS lacked some features to adequately emulate a desk).


Throughout the 1980's, and 1990's, companies and independent developers adopted and advanced the GUI (this includes Linux developers). Therefore, computers were capable of more than they were during the early days of the GUI, but due to the adoption of software like, media players, web browsers, and complex games, modern GUIs began to lack the emulation they once had of work desks.

This meant, to make a UI more desk-like, and still maintain the purity of the desktop metaphor, would require great lengths.

Generally, I think the desktop metaphor is a dying metaphor. To continue the progression of the GUI, I believe the desktop metaphor should be abandoned, for the sake of making it easier to make computers more user-friendly.

It's uncommon to see someone play music, or watch on a conventional desk, without some type of modern technology, that some have a possible difficulty understanding (like say an MP3 Player, or any portable video player).

Thusly, there is a larger difficulty in producing something usable, due to the lack of real-life habits around it.

---

### Post by Sorivenul on 2008-09-01
Tuxoid, thanks for the information.  Most of that I knew from my days learning Java and Xerox PARC. 

I would argue that the metaphor is changing, not dying.  

Many modern desktops, real desktops, are incorporating technology: TV screens, computers, intercoms, etc.  The same is also true in the reverse.  Digital desktops on computers are incorporating long-standing functional ideas: virtual desktops so when one gets dirty you can start with a clean one, sticky notes, drawers, etc.  Amiga's "workbench" style, had it stuck around, probably would have evolved into something amazing - it was already great.  

It really, in the end though, comes down to the target users.  When I want to be productive I opt for GNU Screen and a handfull of command-line applications.  Many others reach for Gnome, KDE, or Xfce.  Some are in the middle with the *Box WMs and others.  

I believe TWiMU will fill a niche, though where that will be remains to be seen.

---

### Post by SphereCat1 on 2008-09-04
Hi! Sorry I haven't posted in a couple days, school just started. Anyway, let's playyyyyyy: *Write Some Stuff About People's Posts!!!* Ahem. Sorry.

Tuxoid: Thanks very much for all the info! I'll talk more about that later.

Sorivenul: Maybe not so much a niche as a geeky thing to run...

SphereCat1

---

### Post by Sorivenul on 2008-09-06
Status Update:
SphereCat1, I'm still working on going over the documentation.  There's a lot included, and a lot to play with in the process.  Will send you the details when complete.

---

### Post by SphereCat1 on 2008-09-07
Hi everybody! Sorry for the short answer last time, I was in a hurry. Some stuff:

If you haven't played with Google Chrome, and have access to windows, DOWNLOAD IT NOW!!!!!!! It rules! I think once there's a Linux version we should think about including it with TWiMU.

I've been slowly adding features to the concept, I'll release a new "screenshot" soon. I'm still not done with the icons! Inkscape hasn't been cooperating. I'll have to update it.

One last thing: Please add features you'd like to see in TWiMU to the discussion page of [twimu.wiki.sourceforge.net/SuggestedFeatures]("http://twimu.wiki.sourceforge.net/SuggestedFeatures")! You will need a Sourceforge account. I'll post a pre-version of the Feature Draft once we have some ideas up there.

SphereCat1

P.S.: Thanks for all the help, Sorivenul! It's much appreciated. My C book should be here tomorrow.

EDIT: We now have control of the backstep project!

---

### Post by omega17 on 2008-09-07
> **SphereCat1 said:**
> Hi everybody! I'm new to Ubuntu, but I have some experience with Puppy Linux. Anyway, I want to try to write a new Window Manager, and I picked Ubuntu as my development platform because it comes pre-packed with so many tools.

The basic concept is kind of like the OS X dock in leopard: the desktop is a huge table that you can place icons and windows on, and it can be as big or small as you want.

There will also be a method of grouping items called Palettes, but I'm not exactly sure how they work yet.

Anyway, I'm creating this thread for any ideas or suggestions, just a general wish list. I'll make everything I can happen. This was going to be in programming, but I figured it's more about making things look good than anything else.

Post whatever comes to mind, I'm open to just about anything!
SphereCat1 :)
I have an few ideas:

Click any sound file it plays without opening any window
View any picture without opening any program
view a movie/video without opening any new window
edit text without opening a new program
edit pictures without opening a new program
edit video without opening a new program(?)
and do any task all in the window manager
Have a custom logo that you can change some where in the program

I relies(sp?) this is probably not doable with any single processor today.


Screenshot attached.

---

### Post by indecisive on 2008-09-08
How is Google Chrome any better than Epiphany with WebKit?  Google Chrome does not even pass the Acid3 test like Epiphany with WebKit!

---

### Post by SphereCat1 on 2008-09-08
Hi everybody! I've got an idea for another logo, I'll see if it goes anywhere interesting. More on that later.

omega17: Thanks for all the input! A built-in file viewer and simple photo editor would be cool, and could be much faster depending on your software of choice. Would the file viewer be kind of like OS X's cover flow thing, or something totally different?
I'm not sure a built-in video editor would be too useful, though, because it would have to be so stripped down that you'd end up launching the normal one anyway.

Indecisive: Actually, I don't think I've ever tried Epiphany, it looks a lot like Firefox. Probably because it uses the same code... Anyway, I just think Chrome's interface and speed are awesome! I have a very old computer, so fast is good. There are also rumors that it'll support Firefox Extensions!

Keep posting ideas! :)
SphereCat1

EDIT: If you want to direct someone to TWiMU, just tell them to go to [tinyurl.com/TWiMU]("http://tinyurl.com/TWiMU"). Cool!

---

### Post by Sorivenul on 2008-09-08
I'm not a fan of including anything other than the simple eye-candy and functionality we originally thought up.  

Though, if we *were* to force a browser on folks I would support Midori (also using WebKit).  A great little browser that really flies.  By the time TWiMU is done or almost complete it may even have stable Flash support as current support (which must be compiled in) is still somewhat unstable.  Epiphany is also great and deserves a spin if you haven't tried it.  

Thanks for the tinyurl link SphereCat1.

---

### Post by omega17 on 2008-09-08
> **SphereCat1 said:**
> 
omega17: Thanks for all the input! A built-in file viewer and simple photo editor would be cool, and could be much faster depending on your software of choice. Would the file viewer be kind of like OS X's cover flow thing, or something totally different?
I'm not sure a built-in video editor would be too useful, though, because it would have to be so stripped down that you'd end up launching the normal one anyway.

like OS X's cover flow? I don't think that would be a good idea(Copyrighted?) but some thing close to it.

Maybe tabbed like firefox? one tab to get to the text editor(click a file opens in a new tab) 
click a pic, opens in a new tab. then you can edit it
same with vid. Opens in a new tab, then you can click a button to open a app. in a new tab to edit.

new tab, internet
new tab, file
new tab, pic editor
new tab, music player/editor
ect.

-omega17

---

### Post by indecisive on 2008-09-09
Epiphany w/ WebKit does NOT use the same code as firefox.  It looks the same and is currently package with Gecko in the Ubuntu Repositories, but it is not at ALL the same as Firefox.  In my opinion, Epiphany w/ WebKit is better than Google Chrome, as it does not try to force unique toolkits upon the user.

---

### Post by SphereCat1 on 2008-09-09
Hi again! Sorry about that, indecisive, I misread the page. It just supports Firefox extensions. I'll download both browsers and try them out. Maybe we could mix a browser in with the file manager to make something like Konquerer (that might be spelled wrong...). :D
As far as Cover Flow, that was just an example. Maybe something like a Rolodex? Hmm... Tabs would be a good idea, though. We could also make a slightly larger package that includes basic programs like browsers, text editors, etc so people could get started right away.

I've got another logo ready, I'll make it in Inkscape and post it to see which one everyone likes the best.

In other news: My C for Dummies, 2nd Edition arrived yesterday, so I'll be able to be useful soon! :)
SphereCat1

---

### Post by Sorivenul on 2008-09-09
If we really want to throw something together quickly that can launch those types of programs, something like PerlOS 4 might fit the bill.  That application is basically a large Perl script used to launch other programs and Perl applications via a pseudo-desktop.  I'm sure something similar can be reimplemented in C to fit the "tabbed application/applet launcher" concept.  While a great idea, I don't see its implementation in TWiMU as necessary.  It seems almost more of its own project.  Right now, the focus, in my opinion, should be on getting the basics down first, then deciding on our "bloat".  Just my two cents.

---

### Post by indecisive on 2008-09-11
I don't mean to distract from you topic, but before I make a thread upon this, what do you all think of a desktop that is based on the Blender User Interface?  Also, I was thinking about making the Desktop in 3D view and organizing the icons or even elements within windows by AI?

---

### Post by indecisive on 2008-09-11
Both documents are hereby under the Gnu Free Documentation License.

---

### Post by Sorivenul on 2008-09-12
indecisive:
Your mock-up gives me ideas of where Symphony's Mezzo Desktop should have gone.  Your mock-up is realistic.  In fact, Mezzo almost does it already.  The idea I get from you that Mezzo doesn't do is "layer" the applications, however the minimized applications get iconified to the desktop as an up-to-date snapshot.  This functionality would be great for TWiMU to have, but imagine the icons you created on a virtual "table" instead of free-floating.  See SphereCat1's original mock-up for ideas and run with it:
[http://spherecat1.googlepages.com/tablewindowmanager.png]("http://spherecat1.googlepages.com/tablewindowmanager.png")

---

### Post by indecisive on 2008-09-12
The major difference between my desktop and TWiMU is that my desktop does NOT support overlapping windows, and EVERY pixel (or almost) is dedicated to a window.  This is also the way the Blender UI works.  It is much more efficient and resourceful, and from what I have read, it seems that TWiMU does support overlapping windows, and the other differences seem trivial.  I wonder if there is a way to use Python [which Blender is written (at least partially) in] and PyGTK to use the Blender UI for other applications...

---

### Post by Sorivenul on 2008-09-12
> **indecisive said:**
> I wonder if there is a way to use Python [which Blender is written (at least partially) in] and PyGTK to use the Blender UI for other applications...
The only way to tell is to hack the source code.
I just downloaded the Blender source and took a quick glance through the source directories.  While the main interface looks written in C and Python modules, it also looks like it would be fairly difficult to port the native Blender interface to other applications - at least beyond my scope.  It may be possible to reimplement the interface in a different way, based loosely on the current implementation.

---

### Post by omega17 on 2008-09-13
Okay, I was looking on the first page and saw the "Desk" kinda look. And a concern was that the "desk" would cover the apps. so I thought maybe it could open/close. like the Windows "Hide taskbar" function

When it's closed you would have the os-x like dock look, with a few important (self defined) Icons as a sort of "Quick launch" and you click an arrow and the full "Desk" opens.

---

### Post by SphereCat1 on 2008-09-14
Wow, good stuff happens when I'm not here for a while, maybe I should go missing more often... :D

Basing a DM on blender would yield very interesting results, I think you should go ahead and create a thread (if you haven't already), and keep us posted.

omega, the desk would sit behind all open windows, it's just a desktop on a tilt. Having a button to show the desktop might seriously slow you down. Although, it *would* be useful to have a few icons always visible... We'll have to think about this one, because I don't want to have a bar always on the screen.

When a window is maximized you'll be able to hit a key to show some window options, maybe a different key could show essential icons?

SphereCat1

P.S.: I'm going to make a couple new mock-ups soon, I promise! :)

---

### Post by ammikulka on 2008-09-18
so.. do you have any programming expierence? just curious what languages are you capable of? check into qt, im dowloading it now im good in c, c++. and c#, go there >> [http://trolltech.com/products/qt/](http://trolltech.com/products/qt/)

---

### Post by Sorivenul on 2008-09-18
> **ammikulka said:**
> so.. do you have any programming expierence? just curious what languages are you capable of? check into qt, im dowloading it now im good in c, c++. and c#, go there >> [http://trolltech.com/products/qt/](http://trolltech.com/products/qt/)
I've got some programming experience.  No official "industry" experience as of yet, but I've developed [AntiWM]("http://sourceforge.net/projects/antiwm") and [dwemo]("http://sourceforge.net/projects/dwemo"), two window managers for X.  Both are still active projects, and are done in C using Xlib (Xt), so a project like this is definitely within my grasp.  I'm currently working on a minimal application-launcher panel in PyGTK, akin to PyPanel, but with no menu, just access to the most commonly used applications.  I also know some Perl, and am learning Java and Scheme.  I'm not sure of SphereCat1's programming experience, but the willingness to learn and conceptualize is half the battle. 

As for using Qt, I don't think I ever will for any major project.  I'm not as much a fan of C++ as I am C, and Qt is native C++.  GTK, on the other hand is native C and works well for my developmental needs.  There are also possible licensing issues with Qt depending on project purpose and distribution.  GTK is a GPL-only toolkit, as far as I know, and somebody may correct me if I am wrong.  I have other reasons I prefer GTK over Qt, but I won't list them.  This thread is for constructive discussion for TWiMU, not for starting toolkit flamewars.  

Thanks for the offer for help, by the way.  If I were you, I would contact SphereCat1 and ask to be added to the project team on SourceForge.  Right now I'm still in the process of dissecting FVWM, and have not as much time right now as school has begun again.  Any help is welcome!

---

### Post by SphereCat1 on 2008-09-23
Hi everybody! I'm not dead! Yay! Ahem.

As for TWiMU, I'm having the same problem as Sorivenul. School is eating up most of my free time. Plus, my brain wont stop coming up with ideas. I've been drawing a concept phone during free time in class, and working on my website.

I'll let you know when interesting things happen.

SphereCat1

---

### Post by lanr01 on 2008-09-24
SphereCat1,
 
 Let me start by saying, I love this idea and can't wait to see how it turns out. I don't have much I can offer as far as helping as I know nothing about writing code.

  I am very new to linux, just over a week now ;-)

 But, I started running a BBS back in early 90 on an old 386 sx machine running dos and using qemm and deskview.. I tried the widows for a bit, and moved on to os2 warp for a couple of years. I think I still have it here somewhere.. do to work and other reasons, I have been stuck with windows xp for some time now.

 I love the humming bird. that was great. Looked great.. Kinda hope that is what you go with

I might be able to offer some idea's or beta test for ya, but that would be about it.

 Good luck and can't wait to see it done..

Rick
registered Linux user number 479504.

---

### Post by SphereCat1 on 2008-09-24
Thanks lan01! Chalk up another BETA tester.

---

### Post by xakh on 2008-09-26
do you need icons yet? I'm dying to know. for one, I have a cool icon for a space game if we include one, nicely orbiting something. Also, idea for an easter egg... if we were to add something like a game of marbles in there, that would roll on the table, just spitballing.

---

### Post by SphereCat1 on 2008-09-30
Hi! I've got good news, I have the 8th and the 17th off from school, so those days will be all-day-attempting-to-learn-C marathons! Can anyone say sugar? :D

xakh, good to hear from you again. I have been working on an icon theme, based on the ones in the original mockup. I've only gotten the first icon done, though, so I can send you both if you want. You'd probably be better suited to get it looking nice. :)

SphereCat1

BTW, if you want to know what I'm working on during most of the day, you can follow me on [twitter]("http://twitter.com/SphereCat1"). You can usually figure out when I'm working on TWiMU based on what I'm complaining about. :)

---

### Post by xakh on 2008-09-30
> **SphereCat1 said:**
> Hi! I've got good news, I have the 8th and the 17th off from school, so those days will be all-day-attempting-to-learn-C marathons! Can anyone say sugar? :D

xakh, good to hear from you again. I have been working on an icon theme, based on the ones in the original mockup. I've only gotten the first icon done, though, so I can send you both if you want. You'd probably be better suited to get it looking nice. :)

SphereCat1

BTW, if you want to know what I'm working on during most of the day, you can follow me on [twitter]("http://twitter.com/SphereCat1"). You can usually figure out when I'm working on TWiMU based on what I'm complaining about. :)
Sounds good to me!

---

### Post by SphereCat1 on 2008-10-10
zakh: Sorry it took so long, but [here]("http://SphereCat1.googlepages.com/TWiMUicons.zip") are the parts of the iconset. For now if you could just TWiMUize the icons in the "Temp Icons for TWiMU" folder, that would be great.

Hopefully you get a general idea of the style I'm going for by the one I finished. (The finished one is the base for a status overlay. Like Number of E-mail, time remaining, etc.) Just a little bit more flattened, and slightly more calm colors.

I also included the "shiny" overlay for the icons, the instructions on how to use it are in the SVG along with it. (Mostly so I wouldn't forget, but you should be able to figure out what they mean. :D)

I'm working in Inkscape, but any SVG editor should work.

Thanks for the help! :)
SphereCat1

---

### Post by celticbhoy on 2008-10-10
Hi Catman first post here, but I have been watching from the outside for a while. I like your general concepts, but I think you are going to have to nail down a more complete set of rules to bring all the concepts together. Like everyone else who has shown an interest I have my own ideas of what would be best. If you layout a more exacting plan you might get more help.

Just my ten bobs worth

---

### Post by xakh on 2008-10-10
ummm, on the icons, why are there so many windows logos?

---

### Post by SphereCat1 on 2008-10-11
Oh, :D sorry zakh, forgot to mention that. I got the icons from StyleXP, so you can skip like the Windows logo, Internet Explorer, etc. For example, on the Program Files one, you can just draw the box without a logo. You don't even need to worry about the Windows Folder one or the IE one.

Thanks again for your help!

celticbhoy: We're working on that on the TWiMU wiki, if you go [here]("http://twimu.wiki.sourceforge.net/message/list/SuggestedFeatures"), you can suggest changes to the feature draft which is [here]("http://twimu.wiki.sourceforge.net/FeaturesList").

SphereCat1

---

### Post by celticbhoy on 2008-10-13
Was just messing around and I was thinking of your idea for a round menu type thing, when I checked out the background selector for LG3D. I think something like that with app icons would work well

---

### Post by SphereCat1 on 2008-10-19
Hi all! I just had a really awesome idea for a master control panel. I'll make a "screenshot" and post it soon.

BTW: celticbhoy: That is cool looking indeed... :)

SphereCat1

---

### Post by celticbhoy on 2008-10-19
yeah quite neat, but i think it would have to be sudo 3d or would eat into resources too much. Look forward to your next mock up

---

### Post by SphereCat1 on 2008-10-24
I've been looking for cool ideas around the web, and where should Google lead me but back to FVWM-Crystal! It has a really cool feature called the Quake console, which is just a terminal that pops out of the top of the screen when you press Ctrl+`. (I think it's Ctrl...)

I think we could expand this idea. Mockups are on their way! :D

SphereCat1

---

### Post by urukrama on 2008-10-24
> **SphereCat1 said:**
> I've been looking for cool ideas around the web, and where should Google lead me but back to FVWM-Crystal! It has a really cool feature called the Quake console, which is just a terminal that popps out of the top of the screen when you press Ctrl+`. (I think it's Ctrl...)

There are several applications that do that. Have a look at Tilda, Guake or Yakuake.

---

### Post by lapor on 2008-10-24
I have read all 17 pages and I am very excited about TWiMU.
I don't have any ideas about programming but I can be a beta tester. Want to help somehow.

keep on going.

---

### Post by SphereCat1 on 2008-10-25
urukarama: Thanks for the info! I'll definitely look into those. 

lapor: Awesome! Yet another beta tester!

The new mockup is halfway done! :)
SphereCat1

---

### Post by omega17 on 2008-10-25
I have beta tested many games and programs, including Toontown & Pirates of the Caribbean. If you still have room, please sign me up as a beta tester.

---

### Post by SphereCat1 on 2008-10-25
omega, we have an infinite amount of beta tester space. :D

SphereCat1

---

### Post by crazyness003 on 2008-11-03
Hey SphereCar1, crazyness here. Just wanted to compliment on the project. This is no small task. I know you're in need of as much help as you can get, but unfortunately i know nothing/very little of coding. But I will offer to help with coding if you have an idea, its a language that can be learned...depending on the language. I can recruit the help of others.

As for tester, i see you have a torrent of them, so i'll offer help in that field too if you dont mind.

Graphics...you seem to have that covered.

I did take a look at that [BumpTop]("http://bumptop.com/"), but they seem to refuse to make a Linux version. So its up to you to outdo them OVER9000 times (no pressure) and prove that Linux IS the future.

Cheers, good luck, and i hope to see that next mockup soon.

---

### Post by crazyness003 on 2008-11-06
Hello. Just wanted to know how things go. I hope the project isn't abandoned, it sounds awexome!
In my wait for a new mockup, i decided to boot into 'doze and install BumpTop beta15 on it. Initially, it looks cool, but gets old real fast. The physics responses are kinda slow (compared to compiz effects running in linux)

My opinion: sub-par (and not in the good way). im not too impressed. I hope TWiMU can outdo.

Still waiting to see what it might look like tho.

---

### Post by Giant Speck on 2008-11-07
> **crazyness003 said:**
> Hello. Just wanted to know how things go. I hope the project isn't abandoned, it sounds awexome!
In my wait for a new mockup, i decided to boot into 'doze and install BumpTop beta15 on it. Initially, it looks cool, but gets old real fast. The physics responses are kinda slow (compared to compiz effects running in linux)

I think I'd get a little nauseous using that.  Having to look down and into my computer screen.  Meh.  It's like looking at weird-angle photographs taken out a window twenty stories above a busy street.

---

### Post by Sorivenul on 2008-11-07
> **Giant Speck said:**
> I think I'd get a little nauseous using that.  Having to look down and into my computer screen.  Meh.  It's like looking at weird-angle photographs taken out a window twenty stories above a busy street.
Agreed.  I don't mind the "slanted" table feature, but the "walls" and strange angles outside of the "table" are too much to stomach.

---

### Post by crazyness003 on 2008-11-07
> **Giant Speck said:**
> I think I'd get a little nauseous using that. Having to look down and into my computer screen. Meh. It's like looking at weird-angle photographs taken out a window twenty stories above a busy street.
> **Sorivenul said:**
> Agreed.  I don't mind the "slanted" table feature, but the "walls" and strange angles outside of the "table" are too much to stomach.

I know. I just wanted to try it a bit. Someone mentioned it at the begining of this thread. It's concept is okay, but implementation is kinda poor. The physics, graphics, and angles are not that fantastic. And it takes quite a while to load the whole thing. 

As of right now, not for widespread use. Im gonna keep it just to do testing and see if they end up improving. Liaison, if you will.

---

### Post by SphereCat1 on 2008-11-07
Hi everybody!

crazyness003, it's not abandoned, I'm just lazy! :biggrin: Bumptop looks interesting, I'm signed up for the beta, so I'm just waiting for an invite. I do agree that looking into your monitor would be weird, though.

I'm having a bit of concept trouble with the new mockup, but I will post something soon. :)

SphereCat1

---

### Post by s3kt0r on 2008-11-07
Yet another one that read all the thread pages and dudes, you made a believer out of me. :)

Keep going, if you need beta testers, provide the links openly, people know when a good project needs support.

Subscribin' to this thread also.

greetings

---

### Post by crazyness003 on 2008-11-08
> **s3kt0r said:**
> ...greetings
  welcome...from the unofficial welcomer.

> **SphereCat1 said:**
> ...it's not abandoned...I'm having a bit of concept trouble with the new mockup, but I will post something soon....

Well, thats good news. I had a crazy idea, but i dont even know if its softwarely possible: 

My current background would function very well if it had some dots float around, slowly just orbiting the center, in an eleptical, sort of perspective-like way. These dots be representations of icons or links.
The attached are my current BG (the first one is what my desktop would look like. I have a dual, widescreen setup, so the darkend areas on the top and bottom would not show). The second is the original (if anyone wants to borrow it). 

Imagine if some of the stars actually rotated in realtime...slowly enough to be able to hover over them. Once on hover, have the icon associated with that object replace the "star" (as to not confuse anyone if sonething is a file or folder)...I may need to illustrate this with storyboards or a video, but i hope my description will suffice for now.

Again, just an idea...that is the phase this project it in right now, no?

Anyway, i hope to see your mockup soon. I wanna get an updated whiff of whats cooking.

ps:  bumptop...im not impressed. its a not very resource-intensive, but its slow on response time (as i've mentioned earlier). I dont think anyone would actually buy that to use, just for decoration. Now, gpl and source; That would be nice.

[over][out]

---

### Post by Sorivenul on 2008-11-08
@crazyness003:
On my end, I'm busy performing various hacks on FVWM, playing with combing code from Crystal, amongst other things.  I don't have a lot of time to devote to the full rewrite, as I have school, work, and my family to take care of.  In what little time I have had, I've thrown together a couple of projects that are linked to in my wiki (see my signature).

EDIT:
I got my first "cup" by my avatar finally!  :D

---

### Post by crazyness003 on 2008-11-08
> **Sorivenul said:**
> I got my first "cup" by my avatar finally!  :D
sweet. congrats!

---

### Post by SphereCat1 on 2008-11-09
SphereCat1, reporting live from in front of his screen: (Sorry, couldn't resist that one... :))

s3kt0r: Thanks for joining in!

crazyness003: Interesting idea...And I might even have a place for it! More on that later.

Sorivenul: good to hear that you're being much more productive than I am, and congrats on the coffee cup!

The mockup issues have been resolved, and I'll try to complete it today! If not it will probably be here sometime after 3:00 tomorrow. :D

SphereCat1

---

### Post by SphereCat1 on 2008-11-12
Sorry it's late!

[http://spherecat1.googlepages.com/TWiMUControlCenter.png]("http://spherecat1.googlepages.com/TWiMUControlCenter.png")
(It's attached too.)

Some quick play-by-play, as usual:
- First look at the actual window manager! Glass outlines with variable title bars, this one's big. They probably shrink when maximized to give the program as much of the screen as possible.
- Obviously this is the system's Control Center, not much to say about that yet.
- The blue line on the left side of the title bar opens a window menu.
- The red circle replaces all three default buttons. When you hold down the mouse over it, another circle grows around it with thirds for minimize, maximize, and close. Drag over the action you want to perform.

I may post more later, but I have to go to dinner now. Bye! :)
SphereCat1

---

### Post by crazyness003 on 2008-11-12
> **SphereCat1 said:**
> Sorry it's late!

[http://spherecat1.googlepages.com/TWiMUControlCenter.png](http://spherecat1.googlepages.com/TWiMUControlCenter.png)
(It's attached too.)

Some quick play-by-play, as usual:
- First look at the actual window manager! Glass outlines with variable title bars, this one's big. They probably shrink when maximized to give the program as much of the screen as possible.
- Obviously this is the system's Control Center, not much to say about that yet.
- The blue line on the left side of the title bar opens a window menu.
- The red circle replaces all three default buttons. When you hold down the mouse over it, another circle grows around it with thirds for minimize, maximize, and close. Drag over the action you want to perform.

I may post more later, but I have to go to dinner now. Bye! :)
SphereCat1

thats interesting. a glass effect would be nice on the window borders. and maybe a dark theme aswell ( i cant stand light themes)

its looking good

---

### Post by damis648 on 2008-11-12
I actually had a great idea... as long as you're still planning a desk-like thing, I though about how papers might be moved around a desk. I though that maybe when you minimize a window, it move over and down into a "pocket" in your desktop (VERY rough example attached, but the name would be on the top of the window, and the window would shrink to fit the pocket). I do not know how difficult this would be, but it seems very nice. If we can get a very easy way to view all windows, this could be very efficient and we would lose the need for a "taskbar". What do you all think?

---

### Post by crazyness003 on 2008-11-12
> **damis648 said:**
> I actually had a great idea... as long as you're still planning a desk-like thing, I though about how papers might be moved around a desk. I though that maybe when you minimize a window, it move over and down into a "pocket" in your desktop (VERY rough example attached, but the name would be on the top of the window, and the window would shrink to fit the pocket). I do not know how difficult this would be, but it seems very nice. If we can get a very easy way to view all windows, this could be very efficient and we would lose the need for a "taskbar". What do you all think?

you can get crazy creative with something like that. I've had an idea for about 2 years for a way to "minimize" windows without the lame button-in-the-bar approach.

I'll see if i can get a screenie of that. just for fun.

---

### Post by DJ-Dark on 2008-11-12
OMG thats so awesome! Love the idea! you need to come up with a really creative name for it.

I think it will be great!

---

### Post by Sorivenul on 2008-11-12
> **damis648 said:**
> I actually had a great idea... as long as you're still planning a desk-like thing, I though about how papers might be moved around a desk. I though that maybe when you minimize a window, it move over and down into a "pocket" in your desktop (VERY rough example attached, but the name would be on the top of the window, and the window would shrink to fit the pocket). I do not know how difficult this would be, but it seems very nice. If we can get a very easy way to view all windows, this could be very efficient and we would lose the need for a "taskbar". What do you all think?
I dig it.  Like true desktop "folders".  May be fairly easy to implement, especially using FVWM as a base.

> **DJ-Dark said:**
> OMG thats so awesome! Love the idea! you need to come up with a really creative name for it.
It has one: TWiMU.

---

### Post by s3kt0r on 2008-11-13
> **damis648 said:**
> I actually had a great idea... as long as you're still planning a desk-like thing, I though about how papers might be moved around a desk. I though that maybe when you minimize a window, it move over and down into a "pocket" in your desktop (VERY rough example attached, but the name would be on the top of the window, and the window would shrink to fit the pocket). I do not know how difficult this would be, but it seems very nice. If we can get a very easy way to view all windows, this could be very efficient and we would lose the need for a "taskbar". What do you all think?

Cool idea.How would we bring back windows from minimized state? Still dig the idea, though.

---

### Post by UtopiaTheory on 2008-11-21
Hey TWiMU folks!  I've read this entire thread and I've also gone through the SF page.  Add me as a developer.  I can work in C, C++, python, perl, etc.  Let me know what you need me to help with.  A few ideas:

 -In regards to your circular menu that comes up around your mouse.  I think it would be cool to have variable menu systems.  For example, right-click gives you one type of menu, hold right-click for x number of milliseconds gives you another type of menu, etc.  I think a stripped version of the round menu with just the usual stuff could show up on a simple right-click.  A much more robust round menu with many more options(sub-menus) could appear with a longer held right-click.

 -A cheezy idea.  When you select multiple icons and drag them, they drag out like they are all on a string or a chain.  I'll work on a mock up of that to explain better.  hehe.

 -Desk Drawers.  If you're going to use the desktop analogy, you might as well go all out.  You could have subfolders of the "Desktop" folder show up as "drawers".  Not sure how this would look graphically, but it's just a thought.

Keep me posted.  my email is tom (at) utopiatheory (dot) com

---

### Post by UtopiaTheory on 2008-11-21
Okay...Here's another idea:

For the round menu thing, why not just use a universal screenlet?  I'll do a mockup of a round menu and add the art to the background of a test screenlet.  Then I'll strip all of the options out so we have a clean starting point.  The reason I like universal screenlets is they'll work in any WM or DE.  That and they are written in python...and I loves me some python!  :)

---

### Post by SphereCat1 on 2008-11-21
Welcome to the thread, UtopiaTheory! I really like the "icon chain" idea, it would make drag & drop a bit more visually intuitive. Maybe the chain could pull the icons together if you hover over a folder for a few seconds, too. It would show that all the icons will go in. Just a thought, I came up with that literally as I started typing this reply.

As far as the pocket idea goes, I love it. Maybe it could function as a way to organize different projects you're working on. You could "attach" windows to a folder, and have a button to pop them in or out when you want to work on them. I'll work on a mockup. :)

As for Universal Applets/Screenlets, I don't know how well that would work as a menu, but go ahead and put something together, maybe you'll change my mind!

I also discovered a cool feature of FVWM where if you middle click or press backspace when over a desktop menu's title, it turns into a window that always stays open. It's a cool feature, and could be very useful if used properly.

Sorry this post was all over the place! ;)
SphereCat1

P.S.: I've got an idea for themes in TWiMU, I'll post it later too.

---

### Post by UtopiaTheory on 2008-11-21
Let me know when you get me added as a developer.  Do you guys have any code yet?

---

### Post by SphereCat1 on 2008-11-21
What's your sourceforge username?

---

### Post by UtopiaTheory on 2008-11-22
sorry...SF username is tom_duffy

---

### Post by crazyness003 on 2008-11-22
alright, a dev! sweet.

Im sorry if i seem uneducated (but in this particular field, im still in kindergarten) but is a python menu better? See, i dont know the different advantages/disadvantages of each language for the fvwm menu would be. I dont even know what fvwm looks like (or what it even means!!). Any installation instructions (im using gnome right now)?

At any rate, i like this. its a good progression from 'talking about it' to 'planning' (yes there is a difference). I wish i could help with some of the coding/scripting. I know some ActionScript, but im sure thats a completely different ballpark.

As for this menu-thing, its a great idea. You have access to it no matter where your mouse is (instead of pointing to a fixed button on screen). +1 for productivity. Also keep in mind aesthetics. many users seem to like something look good, as opposed to it being better (and most importantly working better).
I hope to see an alpha in a year or less:)

---

### Post by Sorivenul on 2008-11-22
> **crazyness003 said:**
> See, i dont know the different advantages/disadvantages of each language for the fvwm menu would be. I dont even know what fvwm looks like (or what it even means!!). Any installation instructions (im using gnome right now)?
Links to FVWM screenshots:
[Desktop screenshots (with configurations)]("http://www.fvwm.org/screenshots/desktops/")
[Menu screenshots (with configurations)]("http://www.fvwm.org/screenshots/menus/")
[Desktop screenshots]("http://www.lynucs.org/?fvwm")

As far as languages go, there are many advantages/disadvantages to each language.  FVWM is written in C.  Python is extensible in C.  Python can be embedded in C.  There are a whole mess of debates in the Programming Talk subforum about why to love/hate Python/C/C++/Lisp/Scheme/Perl as well as some good links in the stickies to get you started on your own.

As far as trying the base FVWM, which is really excellent:
```
sudo apt-get install fvwm
```

---

### Post by tariquepark on 2008-11-22
Hi all,
another entire thread reader here and i gotta say i am super impressed:)
i would also like to help where i can as long as it has nothing to do with code or graphics lol so testing for me too :) But i have 3 PCs to play with, with xubuntu7.04 and ubuntu8.10 both dual boot /xp and i can install any OS you like cept mac for testing if you need

now i have 2 ideas:
the DM startup thingy, maybe you could animate the bird icon instead? the whole progress bar n circle stuffs been done i reckon!
and possibly use the same sort of thing for the right click menu as well?
it would sort of theme it all together from boot to shutdown.

anyway its great to see lots of fresh new ideas coming out instead of the same stuff hashed out again :)
cheers

---

### Post by SphereCat1 on 2008-11-22
UtopiaTheory: you're added! :)

tariquepark: Welcome, and thanks for volunteering!

As far as the python menu, I don't know about a universal applet, but a python menu system would allow for a lot of customization, which would be cool!

As far as an alpha, I want lees than that, but I need to finish learning C first. I'll work on that today also. I also finally got around to downloading an SFTP client on my internet machine, so we can get a website up whenever! Designs, anyone?

One more: Just a thought, but what if we include a JavaScript interpreter for user scripts? I know most people hate JavaScript, but it's easy to learn and could work something like AppleScript.

SphereCat1

---

### Post by SphereCat1 on 2008-11-22
Update: A temporary website is up! Also, I used the logo I've been playing with. It's an early version, but let me know what you think!

[twimu.sourceforge.net]("http://twimu.sourceforge.net/")

SphereCat1

---

### Post by UtopiaTheory on 2008-11-22
Hey, 

Glad to see a site up!  Okay, the reason that I mentioned universal screenlets is because, like you said, python allows for a whole lot of customization.  It is also easier to write tutorials for non-programmers to customize using python.  I don't mind writing python menus from scratch...I just thought that a universal screenlet would be a good pre-made template to start from.  Python is quite easily embedded into C and C++, so it should not be a problem.

Tom

---

### Post by SphereCat1 on 2008-11-23
Ah! I see where you're coming from now, good idea! :)

---

### Post by lapor on 2008-11-23
Nice. The site is up.
I just wanted to ask you, why didn't you use logo that was introduced some pages ago? I think it was on page 9.

---

### Post by SphereCat1 on 2008-11-23
No particular reason. I've been playing with this one, and wanted to see what people thought of it. :)

SphereCat1

---

### Post by crazyness003 on 2008-11-23
i think the logo needs a bit more work. Very...blocky.
As for python, im kinda interested, all of a sudden. esp the part about > "  It is also easier to write tutorials for non-programmers to customize using python"
Any suggestions on where i should start to maximize productivity (and learning curve)

---

### Post by celticbhoy on 2008-11-23
Like the text part of the logo on site - the bird in the nest, not so good.

---

### Post by Sorivenul on 2008-11-23
> **crazyness003 said:**
> As for python, im kinda interested, all of a sudden. Any suggestions on where i should start to maximize productivity (and learning curve)
LaRoza had an affinity and affection for Python, as do many other Forum members, myself included.  See [LaRoza'a Wiki Page on Python]("http://laroza77.wikidot.com/python") for a good starting place.
After you have a little experience you may want to play with PyTacToe, which [has a thread here]("http://ubuntuforums.org/showthread.php?t=958634"), and is [hosted on Launchpad]("https://code.launchpad.net/pyctactoe").
I have a couple of small Python/Tk applications available as well, see the "Projects" section of my Wiki and look for PySumpas and fourBar.  
I have more resources for you, but what I just listed should be plenty to get anybody started.

---

### Post by lyceum on 2008-11-24
> **lapor said:**
> Nice. The site is up.
I just wanted to ask you, why didn't you use logo that was introduced some pages ago? I think it was on page 9.

> **SphereCat1 said:**
> No particular reason. I've been playing with this one, and wanted to see what people thought of it. :)

SphereCat1

Speaking of that icon, I have not yet gotten around to perfecting it (I really felt no need as you were talking about making your own). Let me know if it is something that needs to be done for this. I really like that image, so if you do not want to use it I will stash it away for something else.

:guitar:

-edit-

I guess my ego jumped to conclusions there. My logo idea is post #88 on page 5. I did not see one on page 9. Either way, you are still welcome to use it. It has a Creative Commons licence.

---

### Post by lapor on 2008-11-24
Yeah, you are right. It is on page 5. 
My mistake :)

---

### Post by UtopiaTheory on 2008-11-24
Okay, so we have 21 pages in this thread and no code to speak of.  Let's get started.  Have we agreed on a version of FVWM to base this on?  Maybe we should create an SVN on sourceforge so we are all working on the same code?  Let me know, because I want to help get this going!

Tom

---

### Post by Sorivenul on 2008-11-24
> **UtopiaTheory said:**
> Okay, so we have 21 pages in this thread and no code to speak of.  Let's get started.  Have we agreed on a version of FVWM to base this on?  Maybe we should create an SVN on sourceforge so we are all working on the same code?  Let me know, because I want to help get this going!

Tom
You are welcome to talk to SphereCat1 about starting an SVN repository on SourceForge, though I personally am against this.

We do not need code at this stage.  Instead we need a solid foundation.  

Without well formed ideas and plans, without direction, a project loses focus and becomes lost amongst the myriad of open source projects available.  Before going forward:

1.) A version of FVWM must be decided on as a base.
2.) Those working on coding the project must understand the workings of Xlib, the standard C library, and the FVWM code in particular.
3.) Understanding of how to properly configure FVWM is a necessity.
4.) Widgets and panels and bells and whistles are fine, but some discretion must be had - create the base and let others extend the functionality.

I personally see no reason to create an SVN repository for some time as we are still missing notes and documentation specific to TWiMU on important sections of FVWM.

---

### Post by tariquepark on 2008-11-25
hi all 
i'm with Sorivenul on that 
"
We do not need code at this stage. Instead we need a solid foundation.

Without well formed ideas and plans, without direction, a project loses focus and becomes lost amongst the myriad of open source projects available."
:)

---

### Post by CJ Master on 2008-11-25
I'm really excited about this project, and have read all the pages! If your still interested, I'd gladly beta-test when the project comes out. (I'm guess 10,000 years. M I RITE?! :P)
I love the screenyshot on page one or two, can't remember. It's very creative.

---

### Post by crazyness003 on 2008-11-25
Well, first we need some sort of checklist. I dont know whats gonna be in the checklist, but we should start with the FVWM source, and what we're gonna need to modify in order to get the results we need. Then come the fun part of creating the configurations menus along with the GUI design for those menus (or dialogs or whatever). All the things that need to be done, before we get into creating themes and whatnot.

My first to do is to downlad whatever version we're gonna base this offa.
2. learn the WM inside out
3. try to understant the configuration files
4. Get some understanding of python and maybe create a program or two (im gonna try py-tac-toe)
5. we'll see from there.

my todo list.

---

### Post by calrogman on 2008-11-25
I have very little coding experience, the most advanced thing I can do is write a python program that creates a list, randomizes it and prints the first entry to the command-line, about 6 lines of code.  However I don't use my laptop for work related anything and just use it for browsing the net, so I have no fear of breaking my Linux so would happily beta-test!
:)

---

### Post by SphereCat1 on 2008-11-25
I should just take a week off and let the conversation run wild, see what you guys come up with! :D

lyceum: Please, keep working on your logo if you want! This one was just an idea, and I don't consider it nearly ready to use. Someone mentioned that the bird needed some work, and I completely agree. That was my first attempt at making something from real life in Inkscape.

I agree with Sorivenul, torique, and crazyness here, we aren't organized enough yet to even attempt coding something. I officially designate Sorivenul the sanity-keeper of this thread. :) We do need to start working on things, though. I'm going to do another post a bit later on this subject.

CJ-Master and calrogman: Welcome to the tester pool! We need an official page on the wiki with a list of testers. I'll get to work on that also.

I have read back through the entire thread to get a new perspective and to try to catch anything I missed, so I'm also following up a few unanswered leads.

More news later tonight!
SphereCat1

---

### Post by crazyness003 on 2008-11-25
first thing's first: which version of FVWM are we gonna use. is it gonna be an older, stable-er one or the newest, ROXOR , 'ouch i cut myself' one. Or is it gonna be FVWM-Crystal

The latest stabel FVWM is 2.4.20
The latest unstable one is 2.5.26

2.5.16 has inproved support for 64bit (which, btw, is what i use! so keep that in mind)
See [http://www.fvwm.org/news](http://www.fvwm.org/news)

I cant seem to find any useful info on -crystal, other than it allows transparancies (duh)
also, it uses subversion (svn) to control the revisions.

Im gonna go ahead and install FVWM 2.5.26 just to see ho unstable it is (and how fast i can crash it)
EDIT: 2.5.26-1 is in the Ubuntu Interpid Universe Repos

---

### Post by jenkinbr on 2008-11-25
I have no coding experiance in python, C, Perl, or some of the others, and only minimal C++.

I haven't read the whole thread, but I would possibly be willing to test this out and report bugs once this thing gets off the ground and into alpha.

---

### Post by CJ Master on 2008-11-25
You want ideas? Let me re-direct you to your old mock-up.

[img]http://spherecat1.googlepages.com/tablewindowmanager.png[/img]

Note that this is all in my opinion, you don't have to use my suggestions, I'm just throwing it out there.

Alright, first things first. Throw out those icons on the side. They're ugly and can be betterly implimented.

...While we're at it remove those little docks you put in the top-middle screen. We can figure out how to impliment those later. But right now, we're aiming for eye-candy with lots of sugar-coating to get people to try it out in the first place. But I digress, let us continue.

So now all we have left is that little table with the cute little icons on it.

What I propose, now, is to add this (looking like its a bit behind, and not connecting) nifty little thing I call a pinboard.

[IMG]http://i146.photobucket.com/albums/r252/CJ_Master/Pinboard1.png[/IMG]

Of course, it'd be skinned to the desktop to look natural. How it would work is that instead of Minimizing applications, you'd 'post' the icons to the pinboard. You could also post applications or not currently opened files on there, making it one click away from opening your favourite games and documents! :)

My vision for the application menu would have be like this:

Gnome
Style
Menu
On
This
Side
...........|Matching
...........|Apps
...........|On
...........|This
...........|Side.

So the gnome style menu would have buttons like "Acessorys, Games," etc, the matching apps on this side would be the submenu. For example, I'd click on "Acessorys" on the 'gnome style menu' side, and on the right side it'd show me all the acessories I have.

Oh and one little point, when I first click on the applications button, it'd be nice if it showed me a list of my most used apps first off.




...So... there's my ideas! Hope you liked them, be sure to tell me if any of them don't make any sense or conflict something else.

---

### Post by crazyness003 on 2008-11-26
nice! i can alsmot understnad the pinborad part, but how exactly does that go with the tabletop? you're gonna have to prettymuch 'reely' mock it up for me.

As for FVWM. wow that this is simplistic! I have no idea how to do anythign 'cept for left-click and try to ruffle through the menu.

Well, at leased we're onto something now. Take that...other..guy-person...thats not...make-designing a....WM...possibly.

---

### Post by CJ Master on 2008-11-26
well I'm SUPER bad at mockups and the such.... so bear with this aweful mockup.

[IMG]http://i146.photobucket.com/albums/r252/CJ_Master/Mockup.png[/IMG]

Alright... #1 Is where all the applications are going to be shown. They can be moved all around, and you can even choose to 'fold' them (think shading a window) so a windows an inch high, just the description bar (aka "Mozilla Firefox".)

#2 Is the general pinboard area. **No windows can move here.** Like how in ubuntu theres the "Applications, places, and system" things in the top left corner? Well you can't move an app over there. Same concept.

#3 Is an application that was pinned. The person can just click on that icon and it'd re-apear, just like how minimising with ubuntu taskbar works.

#4 Is the applications menu, already explained.

#5 Is just there to show you a currently running window.

Hope that helps!

Edit: Making that mockup and this post took about 40 minutes. :P

---

### Post by Sorivenul on 2008-11-26
> **crazyness003 said:**
> As for FVWM. wow that this is simplistic! I have no idea how to do anythign 'cept for left-click and try to ruffle through the menu.
[FVWM Beginners Guide]("http://www.zensites.net/fvwm/guide/intro.html") - Good resource. Follow the links at the bottom of the page to continue.
[FVWM Advanced Topics]("http://zensites.net/fvwm/guide/advanced.html") - This section is closer to what we may use.  Again, follow links at page bottom.
[FVWM Theme Packs]("http://www.as.ua.edu/~flux/fvwm/") - For your viewing pleasure.

On a separate note, we should look into Forum hosting off of these forums.  While I love the community feedback, I don't want TWiMU to turn into another "Ryder/Borderless Linux" or other projects that are born here and just as quickly fade away.

---

### Post by crazyness003 on 2008-11-26
@ CJ Master
Ok, I get it now. Eventhough its gonna get more polished, its still makes sense. (thanks for that, and sorry you used up that much time)

@ Sourivenul
Thats man. I was just goign through some old discussions about FVWM and how -Crystal is not FVWM and whatever. Still, that WM is FAST! I can get simple thjings done like open FF, but no close button? No right-click! wow.

Im gonna look into the guides at another time, its already 0100 here, and i need to gets me'sleeps.
Again thanks, im gonna learn the crap outta this WM!


then off to Python-land!
(that sounds like a bad...you know; nevermind :D

---

### Post by CJ Master on 2008-11-26
Oh definantly no problem - I rather enjoyed myself.

Here's a second mockup, (Took me like half an hour to an hour. :P) this one introducing another idea I thought up of on the bottom.

[IMG]http://i146.photobucket.com/albums/r252/CJ_Master/Mockup-new.png[/IMG]

I added neat buttons to the window (from left to right, roll the window, pin the window, maximise the window, and close the window.

The bottom part is basically a HQ... I'm half decided if thats a good idea or not. :confused:

Edit: Btw notice the black area around the window, its a bit of eye-candy, might be a good idea to toy around with.

---

### Post by calrogman on 2008-11-26
I like your mock-up CJ Master, but it's a little bit... vertical.

I'm not entirely sure how it would fit on a widescreen display, like my laptops 1280*800 screen.

:-?

---

### Post by CJ Master on 2008-11-26
> **calrogman said:**
> I like your mock-up CJ Master, but it's a little bit... vertical.

I'm not entirely sure how it would fit on a widescreen display, like my laptops 1280*800 screen.

:-?

There's the problem...

I'll see if I can't make a more 'reasonable' mockup. I'm sure theres some better way of implementing the bottom bar.

---

### Post by crazyness003 on 2008-11-26
Hello. Im writting from a very...not-good-working, but still usable enough FVWM environment! w00t. That config file is MADNESS. I dont even know how to take a screenshot.

Anyway, @ CJ Master, im gonna try to make one "emulate" what you're trying to portray using whatever knowlege i have of Flash. Im gonna get started on it now.

I see this working, since FVWM is EXTREMELY Configurable! (There should also be a Tablet PC edition of TWiMU, since tablets should use a different UI design. This i can test)

Off to see the wizard...

---

### Post by CJ Master on 2008-11-26
Mockup on flash?! AWESOME! Can't wait! Thats a big favor for me if you can.

Oh, here's version two of my preious failure. :P

[IMG]http://i146.photobucket.com/albums/r252/CJ_Master/Mockup2.png[/IMG]

Btw, question, how are you using a flash creator on ubuntu? Is there an ubuntu version? Better yet, is there a free version?

---

### Post by SphereCat1 on 2008-11-26
Hi everybody! I have really exciting news! (And congrats to Sorivenul for predicting the future.) Today, I have the great pleasure of announcing: The TWiMU FORuMS! Yes! You read right! We are now awesome enough to have our very own forums!

Your mission now is to post all of your ideas, comments, and random other stuff until I get back. Then we'll start organizing the forums into more precise categories.

[Check it out right now!]("http://apps.sourceforge.net/phpbb/twimu")
SphereCat1

P.S.: Great Job CJ Master! I'll do a post about all the new stuff later.

---

### Post by CJ Master on 2008-11-26
Thanks! Btw - can you make your sourceforge forum open to posts by guests? I tend to prefer to not register at places.

---

### Post by SphereCat1 on 2008-11-26
I suppose I could, but wouldn't you rather be able to keep track of your great ideas? Besides, guests can't start topics or anything like that. I'll consider it. :)

---

### Post by calrogman on 2008-11-27
@CJ Master,
What about opening the applications-thing in a window, using a button in the widgets area?  This would make a lot more sense than having it always visible and it would also allow us to move it around.  This would also mean the display wouldn't have to be so tall.

---

### Post by crazyness003 on 2008-11-27
Hey Everyone [Check it out right now!]("http://apps.sourceforge.net/phpbb/twimu") (seriously. I think you need a SourceForge.net account to register...but im not sure). Make sure you drop by.

@ CJ Master: No, unfortunately, Flash only works in 'doze. Wine works (kinda) but i cant stand the instability, so I just installed a VM of XP, just to get to those hard-to-reach apps.
There is a FOSS, but all it is, is an .swf compiler (not the actual program).
And yes, im gonna try to make it "interactive", but i think its just gonna be animated (havent used Flash in a while).

@ O-Cat (get it ;D) I already dropped a line or two on the TWiMU forum. You'll see me there.

As for development: FVWM is the best option. Whoever chose this: awesome. Customization is insane! Add Python on top of that, and you got yourself some TWiMU!

Keep up the good work everyone!

---

### Post by CJ Master on 2008-11-27
> **calrogman said:**
> @CJ Master,
What about opening the applications-thing in a window, using a button in the widgets area?  This would make a lot more sense than having it always visible and it would also allow us to move it around.  This would also mean the display wouldn't have to be so tall.

That's actually a good idea, but there's the problem of the pinboard, which should always be up top there, easy to access in my opinion. Applications window is the same size as the pinboard so I'd figure it'd be logical to put it in there.

Also, pinboard also eliminates the need for docks, or to a certain extent, applications menu simply because you can pin practically anything on it. (Think: Put some clipboard text on there, a google map, and a random picture, all while having your pinned apps and documents up.)

Can't wait for development!:guitar:

---

### Post by crazyness003 on 2008-11-27
talk about bad luck. I just lost my entire mockup. Thats what i get for not saving + letting someone who dosnt understand anything when they're faced with a computer problem. I guess powerbutton = good. Still, my fault tho. no save; no...dave(?)

wow. Literally all day- gone at the speed of light.

well. i guess that flash mockup is gonna be a bit delayed. Happy thanksgiving to everyone!

---

### Post by CJ Master on 2008-11-27
> **crazyness003 said:**
> talk about bad luck. I just lost my entire mockup. Thats what i get for not saving + letting someone who dosnt understand anything when they're faced with a computer problem. I guess powerbutton = good. Still, my fault tho. no save; no...dave(?)

wow. Literally all day- gone at the speed of light.

well. i guess that flash mockup is gonna be a bit delayed. Happy thanksgiving to everyone!

Wow... Feel sorry for you bud. It's happened several times to me before too... before i learned to save every 10 minutes ;)

---

### Post by collinp on 2008-11-28
Havent been involved with this for a while, but I feel I need to make this post.

We need structure. Structure as in teams of devs to handle individual parts of the OS, basically a list of whom is going to do what and whom is going to assist them. We need a place other than this thread to post work that people do. Things like that.

P.S. I can still design you that website if needed. It wont be all too advanced, simply HTML/CSS.

---

### Post by lyceum on 2008-11-28
> **SphereCat1 said:**
> lyceum: Please, keep working on your logo if you want! This one was just an idea, and I don't consider it nearly ready to use. Someone mentioned that the bird needed some work, and I completely agree. That was my first attempt at making something from real life in Inkscape.

SphereCat1

I will see if I can get it done over the holidays. All I am going to do is kill the extra shadows and fix the lower part wing. After that, it will be free to be modified by anyone, but I will be calling it done. If you want different colors or any other specific changes, let me know now.

Thanks! 

:guitar:

---

### Post by crazyness003 on 2008-11-28
> **Hellow said:**
> Havent been involved with this for a while, but I feel I need to make this post.

We need structure. Structure as in teams of devs to handle individual parts of the OS, basically a list of whom is going to do what and whom is going to assist them. We need a place other than this thread to post work that people do. Things like that.

P.S. I can still design you that website if needed. It wont be all too advanced, simply HTML/CSS.
we already have a place-holder of a website  somewhere on SourceForge. As for a place to post other than here
[TWiMU Forum is Open for Business...kinda]("http://apps.sourceforge.net/phpbb/twimu")
Wicked awesome, huh?

As for structure, we're still spilling ideas, but if you're nut much an an idea person, take a t look at [www.fvwm.org]("http://www.fvwm.org") and download it (you can also get it from the repos. see below), so you can get some feeling on how much customisations can go into FVWM (btw: TWiMU is gonna be based off FVWM, thats why im mentioning it).

Have fun, and please be shure to drop by the TWiMU forum

or

Take a look at some Python scripting, and try to learn how to do anythign with it. You might not learn enough to actually program, but it still might come in handy.
I believe LaRoza had some awesome HowTo's for Python.

Ubuntu download for FVWM ```
sudo apt-get install fvwm
```Not sure which repos must be anabled, but most liekly the "universe" one

@ CJ Master: Lesson Learned. Although, my redoing it, i got some better ideas. I guess total loss it good once in a while. :)

---

### Post by CJ Master on 2008-11-28
Hah, awesome, so how soon do you think it'll be done? Btw - did you ever get it interactive or is it animated?

---

### Post by calrogman on 2008-11-28
> **CJ Master said:**
> That's actually a good idea, but there's the problem of the pinboard, which should always be up top there, easy to access in my opinion. Applications window is the same size as the pinboard so I'd figure it'd be logical to put it in there.

Also, pinboard also eliminates the need for docks, or to a certain extent, applications menu simply because you can pin practically anything on it. (Think: Put some clipboard text on there, a google map, and a random picture, all while having your pinned apps and documents up.)

Can't wait for development!:guitar:


What about having the applications menu and pinboard integrated into the widgets area?  Perhaps the widgets area could be tabbed, and you could have the pinboard and applications menu on separate tabs!

---

### Post by crazyness003 on 2008-11-28
it was semi-interactive. There was 1 window, and you could move it around, minimize it and "close" it.
Also the "Pinboard" idea, i modified it a little...

But its not gonna get done today. I gots real (cough...cough) work to do. Stupid office work.

@ Calrogman: Thats what i did to the mockup i lost. only it was still in the position that CJ master had it in. That widgets area dosnt suit mee too much.

I'll just have to get through this first. I'll be done by the end of the weekend (hopefully)

---

### Post by CJ Master on 2008-11-28
> **calrogman said:**
> What about having the applications menu and pinboard integrated into the widgets area?  Perhaps the widgets area could be tabbed, and you could have the pinboard and applications menu on separate tabs!

I think I see what your saying, but I don't get it. All it'd do is move the space into the bottom, and it'd also be harder to see the widgets.

---

### Post by calrogman on 2008-11-28
I was thinking you could split the widgets area in half and have the pinboard/applications menu on one half with widgets on the other.

---

### Post by CJ Master on 2008-11-28
I suppose so... but wouldn't that be really tiny? O_o

---

### Post by crazyness003 on 2008-11-29
Heres a VERY crude flash mockup. I only made it to show some of the aspects youd see if it was real. The "window" is semi-interactive. The buttons on the top-right work. Thats it tho.

Now, i havent used flash in a while, and was never really that good at AS2.0, so this is the best i can do (if any of you guys think otherwise ;)) The moving FF icon represents how things would scale when they get toward the back, then rescale when they get to the front, while being dragged. Thats why i spent so long. I was trying to figure out the code to actually make it interactive, but then decided to just animate it, it got too late.

Give it a look. Im guessing you gotta open it in a flash enabled browser.

[Untitled-1.swf](http://www.fileden.com/files/20190/Untitled-1.swf)

Make sure you laugh first, then comment back. I friggin hate flash so much, probably why i bought the damn thing :D

Sorry CJ Master. I ran outta time to put the pinboard up. just use your imagination.

---

### Post by CJ Master on 2008-11-29
*laughs*

J/K, a lot better then I could've done.

The thing is, you can drag your window anywhere, not just on the desktop, which I don't know... just doesn't seem to fit..

Also It seems like the back  part shouldn't be connected. >.<

Oh well, i'll talk more about it tomorow, too sleepy atm ;)

---

### Post by tariquepark on 2008-11-29
crazyness003 thats just so cool :)
just a thought though, the grid pattern, would it be better in a 3d perspective view?
by this i mean, picture a box, square on from one side, and take away the front and top panels
now draw the grid inside the boxx, stand back and see what the grid looks like?
but i dont know about the wasted screen with this method?
maybe the windows will still sit in front of the unused desktop area?
Hmmmmmmmmmm :)

---

### Post by crazyness003 on 2008-11-29
@ CJ Master: I know, i know. LYAO. Thats how my first rendition was. Separated. Im gonna remake that again, but sometime in the future. I just wanted to see what everyone else thought of this approach. As for the windows...im not sure if what you're saying would work. I can try to emulate that effect which you speak of, but i gotta figure out some AS...which is kinda pointless, because i wanna start learning FVWM-Config and Python (is there a difference between Py and AS besides the fact that Py is actual programming and AS is just scripting?). I'll see what i can do. All this has gotta wait till next week tho.

@tariqepark: The grid pattern that i made was all designed and made in flash. Thats the colsest i can get to 3D without whipping out a 3D vector program (the only i know of is...well i dont know. 3ds max cant be used since...i know know how to use it. But i see what your saying. And check-out [www.bumptop.com](www.bumptop.com), and see if thats kinda what your talking about. I didnt like it that muchl (i've played with the beta a little in XP). I may be able to emulate that, but like i said, time is limited, and i wanna dedicate as much of it to FVWM-Config and Python as possible.

If you like, take a screenie of the swf and do some GIMPing, or i can upload the .fla file for you're modifying pleasure. But you need [Adobe Flash (authoring)]("https://www.adobe.com/cfusion/tdrc/index.cfm?product=flash&loc=en") to see/modify it. CS4 (v.10) is the latest version, and i've never touched it.

On a personal note, CS3 (v.9) dissapointed me. Thats why i stuck with Flash8 (v.8)

Have fun y'alls!

---

### Post by cammin on 2008-11-30
That bouncing FF icon just makes me want to scale down the TWiBrowser window, roll it up, then use it as a paddle to play 3d pong.

---

### Post by jenkinbr on 2008-12-01
> **crazyness003 said:**
> Heres a VERY crude flash mockup. I only made it to show some of the aspects youd see if it was real. The "window" is semi-interactive. The buttons on the top-right work. Thats it tho.

Now, i havent used flash in a while, and was never really that good at AS2.0, so this is the best i can do (if any of you guys think otherwise ;)) The moving FF icon represents how things would scale when they get toward the back, then rescale when they get to the front, while being dragged. Thats why i spent so long. I was trying to figure out the code to actually make it interactive, but then decided to just animate it, it got too late.

Give it a look. Im guessing you gotta open it in a flash enabled browser.

[Untitled-1.swf](http://www.fileden.com/files/20190/Untitled-1.swf)

Make sure you laugh first, then comment back. I friggin hate flash so much, probably why i bought the damn thing :D

Sorry CJ Master. I ran outta time to put the pinboard up. just use your imagination.

Nice, looks halfway decent.  Oh, I'm supoposed to :lolflag:  I hate flash too, but It made for a decent mock-up.

> **cammin said:**
> That bouncing FF icon just makes me want to scale down the TWiBrowser window, roll it up, then use it as a paddle to play 3d pong.

You mean like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=94877&stc=1&d=1228164492[/IMG]
:lolflag: What is that bouncing firefox thing for anyways?

---

### Post by crazyness003 on 2008-12-01
It supposed to represent how the icons scale the further "back" they are placed. I was trying to script the icon on the lower-right, so that when you drag it around (btw it is draggable), it would scale in accordance to the _y:position. As i said, I tried. Unfortnately, i dont have flash on my laptop, its only installed on my desktop (about 150 miles away, atm). so whence the weekend comes, i might give it a crack again. see if i can get it right.

I'll also make different version, experimenting with the BG.

Anyway, enjoy the FFicon pong.

---

### Post by SphereCat1 on 2008-12-05
Hi! Sorry I've been gone so long, everybody, I just got my iMac and I've been setting it up.

I love the flash mockup, that's almost exactly how it looks in my mind. (Except the one in my mind is a bit shinier... :))

Anyways, I may be absent for a couple more days while I get everything back into a routine, so please, continue with what you're doing!

SphereCat1

P.S.: Someone please create a "mockups" thread on the TWiMU FORuMS and add that one! We need to start transitioning. :D

---

### Post by crazyness003 on 2008-12-05
im on it!

please direct your attention to [http://apps.sourceforge.net/phpbb/twimu/](http://apps.sourceforge.net/phpbb/twimu/)

Im gonna put this in my sig. I need to take out the  [How to pick up and carry your iMac G5]("http://support.apple.com/kb/HT2466?viewlocale=en_US") joke i put in there a while ago (so here it be, a monument on how highly Apple thinks of its consumers, and how bright one or more of those consumers are). Okay, back to business.

GO HERE [http://apps.sourceforge.net/phpbb/twimu/](http://apps.sourceforge.net/phpbb/twimu/) and bookmark!

---

### Post by ThomasAdam on 2008-12-06
> **Sorivenul said:**
> My personal vote lies with FVWM standard.  Crystal depends on FVWM anyway, adding unneeded bloat at a much earlier stage of development when much will be added with the later creation of the rest of the system, table, etc.  Just my two cents, and as the project leader, it's ultimately your call.


"Unneeded bloat"?  Err, no.  FVWM-Crystl is just a configuration framework for FVWM.

-- Thomas Adam

---

### Post by ThomasAdam on 2008-12-06
> **Sorivenul said:**
> URL="http://www.byz.org/~randy/perl/X11::Fvwm/"]http://www.byz.org/~randy/perl/X11::Fvwm/[/URL]

No, no, no.  See "perllib" in the source of FVWM for further information.  This module is obsolete.

-- Thomas Adam

---

### Post by ThomasAdam on 2008-12-06
> **Sorivenul said:**
> I suggest the 2.4.20 or 2.4.0 release to work off of.  

Right -- I'm going to put on a semi-official hat and say this:

Please don't.

Please use FVWM 2.5.X.  Don't be fooled by the "unstable" tag, since it really isn't unstable.  It's been in development for a long time, and has a lot of features.  Having read your proposal list on your SF site, you've already lost out, since FVWM 2.4.X is not EWMH compliant, only the 2.5.X version has support for that.

If you want help with any FVWM internals, let me know and I'll help you -- c,f, that with the support you can get from the FVWM forums ([http://fvwm.lair.be](http://fvwm.lair.be)) -- a URL missing from your original set of links.

I've also seen a smattering of really old URLs being referenced in the course of this thread too -- this is worrying since it seems to me to be a little slap-dash without any thought to what's being read.

I think some vetting is in order here -- if you're going to use FVWM or are thinking of doing so -- run your thoughts by me, it will save you a lot of time and effort.

-- Thomas Adam

---

### Post by Sorivenul on 2008-12-06
This is my last post in this thread before I officially move my posts to the TWiMU forums.

We will use FVWM 2.5.26, listed on the website as latest "unstable".  It is the most up-to-date, and is far from "unstable".  It is easily accessible, and plenty of support can be found for it. It is also the version I am working off of for documentation, TWiMU specific configuration details and modifications, and more.

See you all at the new forum.

---

### Post by CJ Master on 2008-12-15
So..... how are things progressing? Have you gotten any programing done?

Btw, I'd recommended you edit your first post.

---

### Post by SphereCat1 on 2008-12-20
CJ-Master: Done.

If you've read this far, please countinue at the [TWiMU Forums]("http://apps.sourceforge.net/phpbb/twimu"), hosted on Sourceforge. This thread will be mostly ignored.

SphereCat1

---

### Post by calrogman on 2009-04-04
[SIZE="5"]Huge bump![/SIZE]

How are people going to know about the TWiMU forums if they can't find this thread?

---

### Post by lyceum on 2009-04-04
> **calrogman said:**
> [SIZE="5"]Huge bump![/SIZE]

How are people going to know about the TWiMU forums if they can't find this thread?

Is anything even happening with this? I thought it was over.

---

### Post by tariquepark on 2009-04-04
hi there,
yes the project is still going you can find it here
[https://sourceforge.net/projects/twimu/](https://sourceforge.net/projects/twimu/)

cheers

---

### Post by SphereCat1 on 2009-04-05
We're still working on it, albeit slowly, over at the [new forums]("http://apps.sourceforge.net/phpbb/twimu").

Thanks for the bump, that's a good point. :)
SphereCat1

---

### Post by calrogman on 2009-04-05
> **SphereCat1 said:**
> Thanks for the bump, that's a good point. :)

Your welcome!  ;)

---

### Post by calrogman on 2009-06-21
Is anyone still alive out there?

---

### Post by DeadSuperHero on 2009-06-21
Yeah, I've been eyeing this project for a while. How is it coming along?

---

### Post by SphereCat1 on 2009-06-21
Wow, people really like this project! I am trying to start all my old projects back up, I'll let you know. :D

SphereCat1

---

### Post by calrogman on 2009-08-05
> **SphereCat1 said:**
> I'll let you know. :D

When?

bump_for_answers

---

### Post by Copernicus1234 on 2009-08-05
This sounds way too ambitious but I wish you good luck. A good looking window manager would be awesome and OS X is the best looking one so I like your decision to try and mimic it. :)

---

### Post by SphereCat1 on 2009-08-05
Unfortunately I have to agree that it was way too ambitious. :)

calrogman: The best way to find out when would be to follow me on Twitter, I'm @SphereCat1. I know that sounds like a plug, because it is!

---

