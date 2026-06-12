---
title: "Open Source implementation of the OS X API?"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by waspinator on 2008-06-17
Hi,

I would like to move away from my Mac to Ubuntu, but there are some applications I still like to use on my Mac (iLife ...)

Is there a project like WINE but for OS X's API?

Basically what I want to do is install OS X apps in Ubuntu just like I can install Windows apps using WINE.

Waspinator

---

### Post by phidia on 2008-06-17
There use to be a MOL (Mac On Linux) emulator-like program but that was for PPC not intel macs. You could do something slightly different than what you're asking and run vmware fusion (it's not free) I haven't used their product but they claim this:
> Does VMware Fusion support Linux, Solaris, and FreeBSD?

    Yes, VMware Fusion offers full support for more than 60 operating systems including a wide variety of Linux, FreeBSD, and Solaris distributions. See the Getting Started Guide for more details.
SO you would have your mac plus linux too without rebooting.

---

### Post by mrsteveman1 on 2008-06-17
What wine does is perform some binary magic so you can run existing binaries, and implements substantial amounts of both the Win32 API and even the NT kernel.

There is in fact an open source implementation of the older nextstep APIs called Gnustep but i have no idea how relevant that would be, because Apple has developed things quite a bit and added a lot on top of the old openstep stuff, in particular most apps make use of the Carbon APIs which aren't related to openstep at all.

For now, no there is no way to run OS X programs as-is on any other platform without running all of OS X inside virtualization.

The open source apps that are on OS X can however be ported, but some of them rely heavily on native APIs on OS X so they would change quite a bit. I would love to be using Adium on my other systems instead of pidgin or kopete.

---

### Post by cyberdork33 on 2008-06-17
> **waspinator said:**
> Is there a project like WINE but for OS X's API?
So that's a no.

---

### Post by waspinator on 2008-06-17
Hmm. That's too bad. I was hoping that there would at least be an alpha version of this project, since linux has pretty much anything you can think of, just not finished.

Maybe as OSX becomes more popular there will be a greater inscentive to make a 'Wine' for it.

---

### Post by cyberdork33 on 2008-06-17
> **waspinator said:**
> Maybe as OSX becomes more popular there will be a greater inscentive to make a 'Wine' for it.
It is a possibility, but you have to look at all the time that people have been working on wine, and think that it probably will be a long way off before something is workable, even if the project was started. Plus, believe it or not, MS used to be a little more open about how their stuff worked, at least enough to where you could write software to do something similar... Most of the higher GUI-related libraries and frameworks in OS X are very closed, and would be hard to duplicate. Much of the actual Base OS is open (Darwin), but OS X apps require much more than just Darwin to run.

---

### Post by mrsteveman1 on 2008-06-17
Most of Wines effort has been in duplicating 15 year old bugs that applications depend on to work correctly, in fact thats where a lot of Microsofts development effort goes as well, duplicating bugs in older versions of windows so apps still work on newer versions. 

The OS X APIs aren't as old (Cocoa isn't old, carbon is at least clean and modern but still an old API) so perhaps a group could implement most of them in a reasonable amount of time without having to duplicate bugs. I'm not familiar with how the Wine project went about duplicating functionality, but I'm sure anyone who looked at the source for windows (its available yes) couldn't then work on a project to copy the functionality, it would be tainted code at best and at worst might subject the project (like wine) to copyright violation claims.

The SDK for some of the frameworks in OS X are available just like on the Windows side, and having just looked over the license for the development tools (which includes SDKs for leopard and tiger) i don't see anything that would seem to restrict people from trying to re-implement the APIs, but i have no doubt apple wouldn't like it and would go after people for trying.

I think a lot of the effort on Wine was because people were anxious to flee windows both because of security problems and concerns over its monopoly position in the market, the same is not true of OS X, people are fleeing Windows TO OS X at the moment so there might not be as much demand for the ability to run apps people depend on on the OS X platform, elsewhere.

---

### Post by waspinator on 2008-06-18
That's too bad. I guess I'll have to stick with leopard. Installing Ubuntu was a pain anyway. Hopefully they'll make that part easier at least.

---

### Post by axelman on 2008-09-17
I'd like to know if there's a way to use existing cocoa API implementation inside linux, just the way you can use Windows propietary DLLs inside Wine.

---

### Post by cyberdork33 on 2008-09-17
> **axelman said:**
> I'd like to know if there's a way to use existing cocoa API implementation inside linux, just the way you can use Windows propietary DLLs inside Wine.

I don't think so, and you should really open a new thread for a new question (I know it is sorta on topic, but this thread is quite old...)

---

