---
title: "installing windows program in wine"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Happy2try on 2007-11-06
I was hoping that someone could explain to me a little better on what kind of windows programs can be installed with wine. I have been trying to research online what kind of programs can be used in wine and the most common answer seems to be that wine can install "simple" programs. 

What is considered a "simple" program?

I have seen reviews of people installing AutoCad which I don't see how that is considered a "simple" program.

I would much appreciate if someone could explain what kind of programs can be considered for installing with wine???

---

### Post by Pumalite on 2007-11-06
[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

---

### Post by AndyCooll on 2007-11-06
You can try installing any Windows based program to run under Wine. Some programs work others don't. It doesn't just have to be simple apps, full-blown games often run fine. Obviously the more complicated the app, the more aspects of Windows dll's etc that need translating, the more likely that an app won't run (hence the view that simple apps are more likely to work).

What apps exactly do you want to run?

:cool:

---

### Post by Happy2try on 2007-11-06
I was trying different programs to see how it worked and what kind of windows programs I could get away with on Ubuntu.

Some of the programs were things like FreeCall (Skype type application) and Joost (online streaming Media software), even tried my luck with Windows live Desktop (just to see if it would work).

It appears to install, runs through the setup installation and find in wine browser. I can see the applications in the main menu and in the wine C: drive. When I try to run the installed application every program comes up with some kind of error( e.g.. 'can not parse ini'.., or 'crashed due to unexpected error', 'can't run program.exe' (which I can find in the installed dir),...)

So now I'm trying to figure out if it is a bad wine installation or not using wine properly or if the programs are just not compatible.

Any suggestions are greatly appreciated!!!

---

### Post by balak on 2007-11-06
You can take a look at the crossover office compatibility list:
[http://www.codeweavers.com/compatibility/](http://www.codeweavers.com/compatibility/)

They use wine and most (if not all) of their changes are fed back into the wine repository.

---

### Post by Happy2try on 2007-11-07
Thanks for the links. Interesting enough but it seems using programs cross-platform is still a child in development. It seems the big focuse is on just getting the most common programs like MS Office and such to run seemless. I'm sure they will make it happen just not quite ready for all yet.

It is not that big of a deal for me because there is enough linux programs that can do all that same that work brilliant. And for those couple of programs that you just can't get away from for whatever reason there is always VmWare or Virtual Box to run the Windows enviroment.

Never the less I'm extremely pleased with the Ubuntu distro on how user-friendly it has become. Was working with Fedora a couple yrs back and it was alot of work to get some of the things to run smoothly or compatibility.

---

### Post by carlosjuero on 2007-11-07
> **Happy2try said:**
> I was trying different programs to see how it worked and what kind of windows programs I could get away with on Ubuntu.

Some of the programs were things like FreeCall (Skype type application) and Joost (online streaming Media software), even tried my luck with Windows live Desktop (just to see if it would work).

It appears to install, runs through the setup installation and find in wine browser. I can see the applications in the main menu and in the wine C: drive. When I try to run the installed application every program comes up with some kind of error( e.g.. 'can not parse ini'.., or 'crashed due to unexpected error', 'can't run program.exe' (which I can find in the installed dir),...)

So now I'm trying to figure out if it is a bad wine installation or not using wine properly or if the programs are just not compatible.

Any suggestions are greatly appreciated!!!
Just a note on Joost (I have played with it in Windows): I think the WINE compatibility comes down to how Joost handles DirectX and uses some .NET runtimes; Hopefully the Joost team will listen to those on their forums asking for a Linux version - only time will tell though (Joost is actually a pretty darn good idea, I just hope they can get over the Linux hump :D)

---

### Post by Deacon_X on 2008-03-10
I am having trouble with installing Autocad.  I can get to the install screen but it told me i needed to install IE 5.01 or later so i used ies4linux and installed IE6.  But this thing keeps telling me i need to install IE before the install can complete.  I know i should just use it on my windows box but i need it on my laptop and i refuse to run windows on my laptop.  Any help is appreciated.

---

