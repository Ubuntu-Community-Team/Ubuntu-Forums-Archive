---
title: "Newbie help (probably simple and daft questions)"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by dean_brfc on 2007-05-24
Hello everyone,

I've just installed Feisty Fawn (dual-booting with XP) with the intention of it becoming my main OS, but I'm having a few teething problems which I'd like to get over.

I'll ask the simple one first: I've downloaded aMSN and I'm trying to install it. The file I have is named amsn-o.97RC1-1.tcl84.x86.package, I've changed the permissions to allow it to execute, but it only gets as far as "TCL Scripting Language" then fails. I assume I have to install something else, but my Googling hasn't found out what.

Secondly, I'm have the seemingly rather common low-resolution problem. I have an ATI Radeon 9200 graphics card, but it will only display in 1024x768 and I'd like it higher. Also, things like the Chess game won't let me go into 3D mode. I've tried a few solutions from Google (manually editing the xorg.conf file, installing fglrx (whatever that is)) but they've all resulted in blue screens at the start up and me having to restore the original xorg.conf file.

Any help would be greatly appreciated. These problems aside, I do already prefer the feel of Ubuntu as opposed to Windows despite only having it a few days.

---

### Post by starcraft.man on 2007-05-24
Easy fix for aMSN, you don't need to use that.... much easier using Deb packages.

[Link.]("http://ubuntuforums.org/showthread.php?t=416062&highlight=new+aMSN") There are 4 debs in the first post you need, then scroll down till a poster called luizfar, download the second link. Then install them (they depend on each other so double click them until you find the right order).

Uhhhh, as to second problem, ATI is a headache... Have you tried [Envy?]("http://www.albertomilone.com/nvidia_scripts1.html") Download the latest stable version (0.9.3) and double click to install it. Then go Applications > System Tools > Envy. Click automatically install ATI, then answer yes to everything... it should work, if not then there must be something extra you need to do to get your card to work (and me being an nvidia user would not know >.>).

Hope that helps, have fun. :)

---

### Post by Rhubarb on 2007-05-24
Applications --> Internet --> Gaim internet messenger
This works fine for msn chat.

---

### Post by cborga1985 on 2007-05-24
> **Rhubarb said:**
> Applications --> Internet --> Gaim internet messenger
This works fine for msn chat.

yep i use pidgin (formerly Gaim) for everything

---

### Post by dean_brfc on 2007-05-24
> **starcraft.man said:**
> Uhhhh, as to second problem, ATI is a headache... Have you tried [Envy?]("http://www.albertomilone.com/nvidia_scripts1.html") Download the latest stable version (0.9.3) and double click to install it. Then go Applications > System Tools > Envy. Click automatically install ATI, then answer yes to everything... it should work, if not then there must be something extra you need to do to get your card to work (and me being an nvidia user would not know >.>).
I've just tried doing that and I get a black window with the following message:

ENVY ERROR: ATI's legacy driver does not support your operating system.

Thanks for the suggestions for messenger by the way, I didn't realise Ubuntu had one installed already so I've ditched plans to install aMSN.

---

