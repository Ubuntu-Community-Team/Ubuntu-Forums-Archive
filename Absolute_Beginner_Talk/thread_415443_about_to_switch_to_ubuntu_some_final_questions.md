---
title: "about to switch to ubuntu some final questions"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-04-20
this may have been answered to death but I still want to make sure before I switch.
I know most windows software has Linux alternatives and I don't have a problem with that.
As a matter of fact I am using open office and firefox on my windows machine so I am assuming that linux version is not going to be that different. However I do have a thing for
photoshop and I was wondering if it is possible to emulate it in linux, and if yes will the performance be so low that I won't even want to use it. I used gimp before and to be honest I highly dislike it.

I am running the live cd at the moment still going over things and one thing I noticed that I dont like too much is the interface, and by that I mean the brown orange colors. Is it possible to change it to something like blue or black or something?

The reason I am switching is because I am letting go of XP and I highly dislike Vista and MAC. (I am also assuming that the hard drive installation is going to be much faster than the live cd)

And another question, although this is not as important, but can I emulate source engine games? (such as counter strike source, half life 2, etc)

Thanks, I appreciate the help.

---

### Post by LaRoza on 2007-04-20
The GIMP is great for graphics and there is a version which emulated photoshop, I hear.

You would be able to play many games, for Wine as the emulator, see 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

You can change the background to any picture, pattern, gradient or want. You can get other desktops, including Gnome (the default), KDE, Beryl, Compiz, and many others which are highly customizable.

---

### Post by marko_4454 on 2007-04-20
I dont really know what you mean by "source engine" games. But the games you mentioned can be ran by using a program cedega. While there is a free version, its hard to compile and setup. You can also pay for an easy version which is 15 dlls minimum. Its 5 dlls per month for at least 3 months (or support for extra games).
Just look into cedega before making the transition. You can always dual boot when playing games.

---

### Post by Nythain on 2007-04-20
up to photoshop 7 is well run in CodeWeavers CrossOver... though its commercial software... on the up side, its based on wine, wich is free and reportedly runs higher versions of photoshop well according to some users on this forum... so id say look into those two products and hopefully others can help you more

---

### Post by Gmbrdilos on 2007-04-20
by source engine games I mean games created by valve corporation (examples are counter strike source and half life 2)

I was thinking of making a dual boot too. I have a 80gig Hard drive which is entirely partioned for windows, can I add a partion for ubuntu without entirely killing windows?

---

### Post by silverglade00 on 2007-04-20
If you like a blue theme as I do, you might want to install blubuntu from the repos. I like it a lot.

---

### Post by LaRoza on 2007-04-20
People seems to have no trouble dual-booting with XP.

You can use the installation disk to resize the partition and install Ubuntu alongside Windows.

---

### Post by Nythain on 2007-04-20
if you have enough free space on the partition you could defrag, then use a program like partition magic or whatever windows users use now a days... resize teh 80 gig down to something like 40 or 50 or maybe even 60, depending on how much space you want for linux... then, start the install of ubuntu, during the partition phase either tell it to auto partion only the free space or tell it you want to manually edit the partioning and do it yourself depending on how comfortable you are with that... then continue the install... grub by defualt should pick up windows and add it to its boot list, and voila, dual booted system...

---

### Post by Gmbrdilos on 2007-04-20
is blubuntu like a program for ubuntu or is entirely different version of linux?

and is there like a tutorial somewhere that can guide me step by step on how to set up the dual boot?

---

### Post by microsoft92sucks on 2007-04-20
Once its on the Hard Drive it will run faster then ur xp did. And there are alot of thing alot like paint im not sure about photo shop but probly and u can change the background to any thing. I swithced about 2 weeks ago and i love Ubuntu so much more besides the fact that I HATE m$ Linux is just better. Im sure youll be Happy with a switch.

---

### Post by marko_4454 on 2007-04-20
You can do it, but I would suggest you following a guide in this forum. 
The only possible problem that may happen is that Windows overwrites your MBR and GRUB stops working (forcing you to reinstall GRUB).
Besides that, I think its pretty much straight forward.
Good Luck!

---

### Post by jclmusic on 2007-04-20
try gimpshop or run it in wine.

---

### Post by Gmbrdilos on 2007-04-20
also one thing that I remembered that I have a tv tuner card, The manufacturer website only provides software and drivers for windows, is there a way to find out if the card is compatible with ubuntu?

---

### Post by crimesaucer on 2007-04-20
If you are wondering how GIMP is, then you can always install it in your Windows from Filehippo. I can't afford photoshop and didn't want to get a pirated version, so I would use GIMP on Windows Xp before I ever tried Linux.

Wine supposedly works for most versions of photoshop, I haven't tried yet since I don't have a copy of photoshop.

---

### Post by LaRoza on 2007-04-20
There are step-by-step instructions on the forum.

Here's a quick breakdown:

1. Defrag your hard disk with XP.
2. You can either create a partition yourself, using any tool, including the Windows tool, or you can resize the partition with the installation disk.
3. You then install Ubuntu to the new partition.

Ubuntu's resizing tool is graphical and easy to use.

It is best to back up any files you have in case the resizing causes data to be lost, which is not probable, but could happen.

If you do not need XP, you could just overwrite it too.

---

### Post by marko_4454 on 2007-04-20
> **Gmbrdilos said:**
> also one thing that I remembered that I have a tv tuner card, The manufacturer website only provides software and drivers for windows, is there a way to find out if the card is compatible with ubuntu?

what TV Tuner is this?
I have an ATI one PowerTheater 550 (I believe) and It doesnt work....Support for TV Tuner drivers is not that great.
Just from my experience.

---

### Post by Gmbrdilos on 2007-04-20
yeah I did install gimp on windows but I dont like it.
my main concern at the moment is if my tv tuner will work.

---

### Post by Gmbrdilos on 2007-04-20
my tv tuner is an nVidia NVTV by XFX

---

### Post by msandersen on 2007-04-20
To clarify: [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29") is not an Emulator (seriously, that's what the acronym stands for) is a tool that replicates the Windows API, with the intent of eventually running any Windows program under Unix-like systems like Linux. At this point, it is a feature-complete Beta, but software support is still spotty, especially for larger apps and games; 
The tradeoff  is a considerable performance loss, so it's best to have power to spare for anything like Photoshop. Also, they look and behave like Wndows 95 apps, ie chunky grey. Experimental theme support is very poor at present. It does run Photoshop, though not sure up to what version, I think 7. When I tried it with Photoshop 7, performance was not great on my admittedly old 1Ghz machine, and I definitely didn't consider it acceptable performance.

[Crossover Linux]("http://en.wikipedia.org/wiki/CrossOver") is a commercial implementation of Wine, originally to give full MS Office support in a slick package. The repertoir has since expanded, hence a name change from its original title Crossover Office.

[Cedega]("http://en.wikipedia.org/wiki/Cedega") is the commercial fork of Wine focusing on making various Windows games play under Linux. The main problem with Windows games under Wine is the DirectX API for 3D games, hence their effort on this front.

Although I have not tried, I believe most Steam-based games run under the vanilla Wine project.
There are some sites for tweaking Wine o run various apps and Games, though I don't remember them off the top of my head. There is a Games forum here.

Personally I'm not a great Gimp fan either, I suppose part is being used to (and spoilt by) Photoshop. There is a hack originally made by a Mac user who was used to Photoshop, called GimpShop, which emulates the Photoshop menu layout. 
Apps like Photoshop,  Illustrator and Dreamweaver etc, is why I'm considering a Mac now my main machine has gone to the Great CPU in the Sky. A case of the best tools for the job, expensive though they are.

---

### Post by Gmbrdilos on 2007-04-20
after some googling I kinda got the impression that it is possible to run my current tv tuner under linux, so I am gonna give it a try. Farewell windows.

Thanks guys, I apreciate your help.

---

### Post by msandersen on 2007-04-20
The trouble with Gimp and other GTK apps on Windows, is that GTK seriously suck performance-wise and stick out like a sore thumb there. A native Windows version would be much preferable, and I might have liked Gimp better as a result. But there are a number of other extremely annoying things about it that I can't put up with. GimpShop on Windows is seriously buggy, and looks too hacky. Don't know if there's a Linux version. Running the Windows version through Wine would be an extremely bad idea. I would prefer a properly-maintained official version. 
Much is promised for Gimp 2.6 that would make it worth keeping an eye on, if only they could sort out the annoyances.

---

### Post by msandersen on 2007-04-20
> **Gmbrdilos said:**
> is blubuntu like a program for ubuntu or is entirely different version of linux?

and is there like a tutorial somewhere that can guide me step by step on how to set up the dual boot?
Blubuntu is a theme pack, much as you can switch between Luna and Silver on Win XP (and many others, unofficially), while also beingable to tweak the individual components, like Icons, Window borders, Wallpaper, Startup Screens, etc.

Have a look at [Gnome-Look]("http://gnome-look.org/").

---

### Post by nu2this on 2007-04-21
> **Gmbrdilos said:**
> is blubuntu like a program for ubuntu or is entirely different version of linux?

and is there like a tutorial somewhere that can guide me step by step on how to set up the dual boot?
For a step by step try here [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)   
Its' written for 6.06 but the basic steps are still the same. As to the blubuntu I thought I saw that it's installed from Synaptic.

---

### Post by Tundro Walker on 2007-04-21
Can you change the screen color?  Yeah, that, and the tool-bar / panels, the applets on the panels, the wallpaper (even using transparent wallpapers like the [HelloKitty Ubuntu]("http://www.chipx86.com/blog/?p=189") one I use in my screenshot which let your background colors show through), the icons, the window borders/theme, the fonts...

You'll go stir crazy by all the stuff you can change.  In fact, it's one reason why a lot of folks dig the command-line, because while everyone's GUI is tweaked to all get out, at least the command-line normally looks and acts consistently the same.

(Ah, jeez...tossing in a screenshot has just turned this into a 100 page, "show us your screen!" post...LOL!)

As for Photoshop, haven't heard good things about it and Linux compatibility.  Folks say GIMP is comparable, but there's still a few things Photoshop can do that GIMP can't.

Folks in this linked post get a bit livid, but do voice alternatives...

[http://ubuntuforums.org/showthread.php?t=276306&highlight=gimp+photoshop](http://ubuntuforums.org/showthread.php?t=276306&highlight=gimp+photoshop)

---

