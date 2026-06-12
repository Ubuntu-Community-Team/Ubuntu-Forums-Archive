---
title: "Another Window Manager vs. Desktop Environment question"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-07-30
Well, I understand the basic stuff that these two do: Window Managers take care of displaying windows, borders, window buttons, etc. Desktop Environments make sure that you get an integrated desktop experience through its applications, desktop architecture, etc.

I also understand that GNOME, KDE, Xfce, and GNUstep are real Desktop Environments, while fluxbox, openbox, fvwm, and windowmaker are just Window Managers.

What I don't understand is this: when a distro says that it's using a specific window manager, does it mean that there's no desktop environment installed? Does this mean that the distro is less "integrated" compared to a distro that has a desktop manager AND a window manager? For example, DSL (Damn Small Linux) uses Fluxbox, while dyne:bolic uses WindowMaker. 

What does it really mean when a distro has a full desktop environment and when a distro is just using a window manager?

Thanks for any clarifications. There are just some things in Linux that I'm still ignorant about. :D

---

### Post by 5-HT on 2006-07-30
While I won't pretend to be anywhere near knowledgeable on the subject, I'll try to take a stab at this...

For the most part it depends on which window manager (WM) the distro is using, if/how the distro has customized it (some distros will customize a WM/DE by adding extra utilities/features), and if you could easily install a different WM or desktop environment (DE).

To complicate matters, you can use different window managers in desktop environments. For example, while GNOME uses Metacity it's a trivial matter to switch Metacity for Openbox. Furthermore, once you make the switch all of GNOME's nice GUI utilities are still available.

To answer one of your questions: if a distro is advertising using a particular WM then it is pretty safe to conclude there is no default DE - though it does not necessarily mean that you couldn't install your preferred DE.

As a very loose rule, DE's tend to have some extra bells and whistles in terms of utilities for configuring network connections, printers, etc and services such as automounting, etc at possible cost of increased footprints (compare Fluxbox with GNOME). However, if you are comparing the GUI utilities in KDE to GNOME you can see the line is simply a matter of degree.

The one point I'd like to stress is that while any particular distro may have a default WM/DE, the big question is whether you could easily install your preferred WM/DE.

---

### Post by jpkotta on 2006-07-30
Well, first off, *all* desktop enviroments use a window manager.  Due to the modular nature of Unix, default DE WMs can be swapped in favor of another.  You can use FVWM as GNOME's WM or Fluxbox as KDE's.

As for whether things are "integrated", well, that's something that varies from distro to distro.  But in general you can expect that using the default GUI, whether DE or WM, will be relatively integrated.  For example, I used to use Mandrake (Mandriva), and it had the same default theme for GNOME, KDE, and a handful of WMs, so in a sense, they were all integrated.

BTW, is integration really a good thing?  If you're talking about look and feel, then sure, it's good (albeit superfluous).  If you're talking about everything being connected and working together, then maybe.  Because it's very hard to get everything working together properly.  A lot of what I dislike about Windows is the irresponsibly tight integration.  I've had IE crash at work, and it takes the whole Explorer (i.e. the taskbar, desktop icons, etc.) down with it.

---

### Post by Jucato on 2006-07-30
(NOTE: I'll be using DE = desktop environment, and WM = window manager. :D)

Thanks for the ideas. I know that some distros allow switching between DE's or WM's. But most of those that allow this, are those that have DE's already. It's like when you log in to a fluxbox session, you're just using Floxbox as the WM over the GNOME DE.

I'm still a bit confused, regarding the "practical" aspects of a distro running only a window manager, and no desktop environment. 

@jpkotta: In my mind, the "integration" offered by DE's come in different levels.
- Look'n'feel: GNOME/KDE apps look similar in color, icons, fonts, etc.
- Libraries: GNOME/KDE use GNOME/KDE libs. They don't mix. Even if you install KDE apps on GNOME, those KDE apps will still use KDE libs.
- architecture/components and communication: The GNOME apps communicate among themselves in a unique and "integrated" manner, and KDE apps do the same. Also, GNOME and KDE also have different architecture/components (Bonobo/KParts, DBUS/DCOP, etc.)

So do distros with only WMs miss out on these stuff?

---

### Post by ProjectGod on 2006-07-30
hmmm while were on the topic what's a really cool, light, highly configurable window manager? i don't really like metacity. or icewm or xfcewm.

---

### Post by tturrisi on 2006-07-30
> **ProjectGod said:**
> hmmm while were on the topic what's a really cool, light, highly configurable window manager? i don't really like metacity. or icewm or xfcewm.
[http://xwinman.org/](http://xwinman.org/)

the basics re de's & wm's
[http://xwinman.org/intro.php](http://xwinman.org/intro.php)

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> I also understand that GNOME, KDE, Xfce, and GNUstep are real Desktop Environments, while fluxbox, openbox, fvwm, and windowmaker are just Window Managers.

No, GNUstep is **no** desktop environment -- it is a framework for desktop application **development**.

One of these applications is GWorkspace ( [http://http://www.gnustep.it/enrico/gworkspace/]("http://http://www.gnustep.it/enrico/gworkspace/") ) that is a desktop environment.

---

### Post by Buffalo Soldier on 2006-07-31
> **cbv said:**
> One of these applications is GWorkspace ( [http://http://www.gnustep.it/enrico/gworkspace/]("http://http://www.gnustep.it/enrico/gworkspace/") ) that is a desktop environment.
I guess it should be [http://www.gnustep.it/enrico/gworkspace/](http://www.gnustep.it/enrico/gworkspace/)

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> 
@jpkotta: In my mind, the "integration" offered by DE's come in different levels.
- Look'n'feel: GNOME/KDE apps look similar in color, icons, fonts, etc.
- Libraries: GNOME/KDE use GNOME/KDE libs. They don't mix. Even if you install KDE apps on GNOME, those KDE apps will still use KDE libs.
- architecture/components and communication: The GNOME apps communicate among themselves in a unique and "integrated" manner, and KDE apps do the same. Also, GNOME and KDE also have different architecture/components (Bonobo/KParts, DBUS/DCOP, etc.)


I guess the confusion regarding GNUstep being a desktop environment (rather than a development environment) comes from the fact that all of the above is already integrated within the libraries that come with GNUstep.

That is, all applications based on GNUstep will look the same, no matter which theme you're using, and are able to automatically communicate with each other (due to the fact that this functionality is part of the basic API and doesn't require any special/additional library).

So, with GNUstep(-based applications), to use features that usually are part of a desktop environment, you would only have to run two GNUstep-based applications, say GNUMail and TextEdit.

GWorkspace, as mentioned above, will just give you a nice desktop (you can use to put documents on), a dock (to keep frequently used applications easily available) and a filesystem explorer -- but no additional functionality (like, say, inter-process communication, or themes) you wouldn't already have without it. Because that comes with GNUstep already and is available as soon as you create, compile and run an application.

---

### Post by cbv on 2006-07-31
> **Buffalo Soldier said:**
> I guess it should be [http://www.gnustep.it/enrico/gworkspace/](http://www.gnustep.it/enrico/gworkspace/)

Oops, yes, sorry, my fault.

---

### Post by Jucato on 2006-07-31
Oh, sorry for the mix up with GNUstep. The WindowMaker called it a Desktop Environment, so I just presumed :(

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> Oh, sorry for the mix up with GNUstep. The WindowMaker called it a Desktop Environment, so I just presumed :(

Window Maker has not much to do with GNUstep. Not any more that is.

At one point in time it was supposed to be the window manager of choice for the GNUstep project (much as GNUstep was the development environment of choice for the GNU operating system, way back when).

For various reasons, Window Maker instead got WINGS (WINGS is not GNUstep) and the paths (and interests of the makers) of GNUstep and Window Maker diverged. However, Window Maker still best supports GNUstep-based applications.

---

### Post by Jucato on 2006-07-31
I see, thanks for pointing that out. :D

I guess that's one less Desktop Environement for Linux.

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> I see, thanks for pointing that out. :D

I guess that's one less Desktop Environement for Linux.

Uhm? Why?

Install the GNUstep libraries, run Window Maker and GWorkspace and voila, you have a desktop environment.
Technically, it really isn't (compared to KDE or GNOME), however you will not notice, because everything you expect from a desktop environment **is** there.

---

### Post by Jucato on 2006-07-31
Well if you put it that way. I was just thinking about a desktop environment that is technically really a desktop environment (KDE, GNOME, Xfce). But like what you said, most users won't know/see the difference. GNUstep has captured my attention quite a bit. It's nice to see another possible alternative out there. To bad it didn't develop into a "real", "full", desktop environment to rival KDE, GNOME, and Xfce. And it's basically in Objective-C, which is a totally new monster to me. I've always heard of C and C++, so please forgive me if I'm a both curious and doubtful about it... (even if it's used in Mac OS X?)

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> Well if you put it that way. I was just thinking about a desktop environment that is technically really a desktop environment (KDE, GNOME, Xfce). But like what you said, most users won't know/see the difference. GNUstep has captured my attention quite a bit. It's nice to see another possible alternative out there. To bad it didn't develop into a "real", "full", desktop environment to rival KDE, GNOME, and Xfce.

GNUstep has a low profile, true. As said before, at one point in time (and actually for quite some time) it has been the environment of choice for a GNU operating system, but for various reasons it never took off. One reason may be that "weird" Objective-C dialect.

However, due to the different approach of implementation, GNUstep has far more potential than KDE or GNOME. For one, because a lot of functionality is part of GNUstep and therefor automatically available without the need of any additional libraries or daemons. Another would be the development tools that are part of GNUstep that allow a *very* rapid development. With Gorm, you can write an image viewer (ok, ok) in about 5 minutes max.

> And it's basically in Objective-C, which is a totally new monster to me. I've always heard of C and C++, so please forgive me if I'm a both curious and doubtful about it... (even if it's used in Mac OS X?)

Objective-C is, but GNUstep isn't, though Apple's OSX (or rather Apple's Cocoa) and GNUstep share the same API.

They both are based on the OpenStep API (OPENSTEP would be the implementation) created by NeXT and Sun. So there's a lot of similarities between Cocoa and GNUstep insofar that you can develop an application on Linux under GNUstep, then take the source over to OSX and recompile et voila, it works. No need to use any foreign (to OSX) libraries, like KDE or GNOME, which require a lot of pre-configuration, like X11...

---

### Post by Jucato on 2006-07-31
> **cbv said:**
> GNUstep has a low profile, true. As said before, at one point in time (and actually for quite some time) it has been the environment of choice for a GNU operating system, but for various reasons it never took off. One reason may be that "weird" Objective-C dialect.

However, due to the different approach of implementation, GNUstep has far more potential than KDE or GNOME. For one, because a lot of functionality is part of GNUstep and therefor automatically available without the need of any additional libraries or daemons. Another would be the development tools that are part of GNUstep that allow a *very* rapid development. With Gorm, you can write an image viewer (ok, ok) in about 5 minutes max.

Objective-C is, but GNUstep isn't, though Apple's OSX (or rather Apple's Cocoa) and GNUstep share the same API.

They both are based on the OpenStep API (OPENSTEP would be the implementation) created by NeXT and Sun. So there's a lot of similarities between Cocoa and GNUstep insofar that you can develop an application on Linux under GNUstep, then take the source over to OSX and recompile et voila, it works. No need to use any foreign (to OSX) libraries, like KDE or GNOME, which require a lot of pre-configuration, like X11...

So GNUstep has more potential to be a cross-platform/cross-DE (something that works on both GNOME and KDE?) desktop environment/development kit? Interesting.

Now if only it used C++ (or even C) instead...
Although if you will take appearances into consideration, the screenshots of GNUstep (and WindowMaker) look a bit... old style?

---

### Post by kabus on 2006-07-31
> **Fenyx said:**
> 
Thanks for the ideas. I know that some distros allow switching between DE's or WM's. But most of those that allow this, are those that have DE's already. It's like when you log in to a fluxbox session, you're just using Floxbox as the WM over the GNOME DE.


No, it is perfectly possible to use a WM without a DE.
DE is basically just a fancy name for a WM plus a few default applications that have some degree of integration with the rest of the environment (either technically or because they follow interface guidelines), plus GUI config tools for various system settings, plus some system services that might take care of things like auto-mounting.

If you can do without all that stuff you just use a WM that gives you basic desktop functionality (open/close applications, move windows, etc). 
Then you can add the DE like features you actually need through third-party apps. For Example, most WMs don't provide their own way of setting a desktop wallpaper, so if you want one you use a tool like feh.

The difference between DE and WM is more philosophical than technical, much like the difference between Linux distros: Some distros just give  you a base system you can build upon while others give you a full desktop install that includes everything an 'average' user might need.
The former is easier for new users, the latter usually results in a leaner system. The same goes for DE vs WM.

Another interesting point about WMs is that at least some of them are more adventurous than the two big DEs and are experimenting with interface designs that divert from the omnipresent WIMP paradigm. Examples of this are Ion3, wmii and ratpoison.

---

### Post by Jucato on 2006-07-31
Thanks kabus! That clarifies things a bit.

Thanks for mentioning some other WMs. One thing I've noticed about these WMs is that they look very minimalistic. To me, they actually look quite old, like predating Windows 3.1. So far, the only WMs I've seen that are a bit more "modern" are KWin, Metacity, Enlightenment, and Mezzo. I wonder why the WM trend seems to go in that direction. (I might be wrong... I hope I am)

---

### Post by kabus on 2006-07-31
> **Fenyx said:**
> 
Thanks for mentioning some other WMs. One thing I've noticed about these WMs is that they look very minimalistic. To me, they actually look quite old, like predating Windows 3.1. So far, the only WMs I've seen that are a bit more "modern" are KWin, Metacity, Enlightenment, and Mezzo. I wonder why the WM trend seems to go in that direction. (I might be wrong... I hope I am)

The WMs I mentioned are all designed by people who are very disillusioned with the current trends in interface design and they purposefully chose to go in a extremely minimal direction. This is less true of the various *box WMs, but even they are rather minimal because, well, that's kinda the point of these standalone WMs: less ressources wasted and more flexibility for advanced users.
There's also an aesthetic dimension to this: I find my minimal desktop a lot easier on the eye than a fully blinged out Gnome, but not many people seem to agree with me. :smile: 
But if you like stuff like Kwin and Compiz don't fear, you're definitely with the majority of users there.

---

### Post by cbv on 2006-07-31
> **Fenyx said:**
> So GNUstep has more potential to be a cross-platform/cross-DE (something that works on both GNOME and KDE?) desktop environment/development kit? Interesting.

Of course you can install and use KDE and GNOME on a Mac.
But to run any of their applications, you need additional stuff, like an X11 server. Even if you use OroborOSX (a spin of off oroborus, that acts as a root-less window manager on OSX) GNOME- and KDE-based applications look and feel... different.

Using GNUstep-based applications, it's as simple as write your application, compile it either on Linux (with GNUstep installed) or on a Mac (using Cocoa, the default API) and run it. No need to do anything else. Plus, GNUstep-based applications integrate neatly in OSX' look'n'feel -- because the API of GNUstep and Cocoa are closely related.

> Now if only it used C++ (or even C) instead...

Objective-C really is C -- and a bit more. The only difference between C and Objective-C is just a handful of new identifiers, plus a new syntax, that is based on Smalltalk, to describe objects and what to do with them.

Learning Objective-C is a matter of less than a day, if you know C.

> Although if you will take appearances into consideration, the screenshots of GNUstep (and WindowMaker) look a bit... old style?

Window Maker clones the look of NeXTSTEP, which is also the *default* look for GNUstep. However, you can theme GNUstep to your taste. My setup is frequently confused with OSX... (I'm not using Window Maker)

---

### Post by Jucato on 2006-07-31
@kabus: I don't use Compiz (yet). What I do like about KWin is that almost every part of it is customizable, although some are only customizable depending on what window decoration is being used. So I guess there's no sort of middle ground between the standalone WMs and DE-based WMs (Metacity/KWin). So if I wanted to make something like fluxbox look sort of "modern", I'm out of luck.

@cbv: I've read about how Objective-C is a very strict superset of C. But I'm more of a C++ person (I think).

Are you using GNUstep? I know this is quite off-topic, but could you post a screenshot of your "setup"? I'm really quite intrigued. :D

---

