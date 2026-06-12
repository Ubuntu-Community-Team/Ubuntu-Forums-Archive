---
title: "First-time Installer of Rosegarden and how do you tell about VRAM?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by nayo on 2007-01-17
OK.  I am loving Ubuntu.  I just installed it and was able to show the Nelson Mandela video to friends.  Within 15 minutes I had 3 new converts.

Anyway, I am still a newbie, a proto-newbie perhaps, and I have a few questions as I proudly type from my "Dawn of Ubuntu" screen.  

Anyway, in version 6.06 LTS:

a.  is KDE 3.x and Qt3 included, whatever they may be? I need too know because I am keen to install Rosegarden and the web site says these two are needed.

b. How do I know if my li'l bit of 32 MB VRAM is recognized?

c.  Rosegarden has 4 install files with differing extensions, etc.  How do I install actually and completely for this case.  I'm just a little overwhelmed, but am actually more psyched to get started in Rosegarden.

Thanks for everything in here and know that you guys (dual gender) must have done an awesome job with the installer, etc. if even I could do it.

---

### Post by eric71 on 2007-01-18
Rosegarden is available in Ubuntu's Universe repository.  You just need to open Synaptic, enable the Universe repository, and reload the package lists. You should then be ble to search for "rosegarden" with synaptic and select it for installation.  Synaptic will automatically install the Qt3 and KDE components necessary.

---

### Post by nayo on 2007-01-18
awesome, I think I did it

now no icons will appear tho even tho Rosegarden runs in alt + F2

and this might be another thread I guess, but should I assume that the VRAM is all being used?

Thanks!

---

### Post by Littleweseth on 2007-01-18
You might have to update the menus manually - I don't know about gnome-panel, but openbox's menus won't show new programs until I run a command.

Try running 'gksudo update-menus' in your run dialog, or just 'sudo update-menus' from a terminal.

---

### Post by eric71 on 2007-01-18
I have recently installed Feisty Herd 2, after using Kubuntu Edgy for awhile, mainly to get Rosegarden 1.4.0.  In Gnome Rosegarden did not appear in my menu.  Just Something weird about the Rosegarden package I guess.  In KDE it appears in the menu fine.  In Gnome I just created a launcher for it and added it to the menu with the menu editor.  The icon was a pain to find.  It's somewhere in the HighColor icons folder in /usr/share/icons, not in usr/share/pixmaps where most other icons seem to be kept these days.

p.s. I'm not too familiar with vram, but to make sure your system is optimized for memory access and preemtion, check out this information:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by Enverex on 2007-01-18
Argh, why do people buy into this myth. You do NOT need KDE to run Qt based apps just like you DON'T need Gnome to run GTK apps.

---

### Post by eric71 on 2007-01-18
Nobody here said you did.  The original poster was asking about Rosegarden, a KDE app in Gnome, where it happens to run fine.  Just need a few KDE libraries and QT3 installed.  The only problem is this particular package does not create a menu entry in Gnome, whereas it does in KDE. This is an abberation rather than the norm.

---

### Post by Enverex on 2007-01-18
> **eric71 said:**
> Nobody here said you did.

> **nayo said:**
> is KDE 3.x and Qt3 included, whatever they may be? I need too know because I am keen to install Rosegarden and the web site says **these two are needed.**

;) 

I wasn't referring to this thread that much though, I've seen many threads where people thought they couldn't use App X because it was a Qt based app and they assumed you needed to be using KDE. I wasn't shouting, it just seems like people are being unnecessarily restricted artificially due to some odd myth.

---

