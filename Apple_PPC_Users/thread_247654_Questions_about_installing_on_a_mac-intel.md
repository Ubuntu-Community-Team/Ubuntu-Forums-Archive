---
title: "Questions about installing on a mac-intel"
date: 2006-08-30
forum: Apple PPC Users
---

### Post by GhandiBurger on 2006-08-30
I recenlty got a MacBook and wanted to triple boot with OS X, XP Pro, and of course, Ubuntu. I found this how to: [http://www.ubuntuforums.org/showthread.php?t=187465&highlight=triple+boot+macbook]("http://www.ubuntuforums.org/showthread.php?t=187465&highlight=triple+boot+macbook")

I would just like to know that if the Ubuntu install fails or doens't work that all my os x files will still be recoverable using my install CDs. BAsically what I am asking is that will one messed up partition affect a working partition. Also, does it help that I have refit installed? I did the first half of that how to in order to install XP and to prep for Ubuntu. Feedback would be gretaly appreciated.

---

### Post by Dullin on 2006-08-31
The messed up partition will not mess up the other ones.

As for having rEFIt installed ... it saves you a step in the guide i guess ;-)

---

### Post by hajk on 2006-08-31
> **GhandiBurger said:**
> I recenlty got a MacBook and wanted to triple boot with OS X, XP Pro, and of course, Ubuntu. I found this how to: [http://www.ubuntuforums.org/showthread.php?t=187465&highlight=triple+boot+macbook]("http://www.ubuntuforums.org/showthread.php?t=187465&highlight=triple+boot+macbook")

I would just like to know that if the Ubuntu install fails or doens't work that all my os x files will still be recoverable using my install CDs. BAsically what I am asking is that will one messed up partition affect a working partition. Also, does it help that I have refit installed? I did the first half of that how to in order to install XP and to prep for Ubuntu. Feedback would be gretaly appreciated.

One way to know for sure that messing with EFI/GPT partitioning is not going to affect your OS X functionality is to install Windows XP and Ubuntu in their own Parallels VMs. I had a dual boot setup (also using rEFIt), but I've now reverted back to 100% Macintosh HD, installed Parallels and Ubuntu in it. It works wonderfully, only downside is EUR 70 for buying Parallels... I have made some notes on the various install/uninstall options that may interest you, see [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk").

---

### Post by frigaut on 2006-09-01
> **hajk said:**
> One way to know for sure that messing with EFI/GPT partitioning is not going to affect your OS X functionality is to install Windows XP and Ubuntu in their own Parallels VMs. I had a dual boot setup (also using rEFIt), but I've now reverted back to 100% Macintosh HD, installed Parallels and Ubuntu in it. It works wonderfully, only downside is EUR 70 for buying Parallels... I have made some notes on the various install/uninstall options that may interest you, see [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk").

Parallel is great. However, you can't do everything with it. I also installed XP and Fedora with parallel but ended up configuring my MacBook Pro in triple boot anyway (OSX/Ubuntu/XP). Partly for fun, but partly because you can't do some stuff with parallel: mostly you can't benefit from graphic hardware acceleration, which prevents you from running games within XP (what else would you use windows for?) and running eye candy Xgl within linux.

---

### Post by entangled on 2006-09-01
> **hajk said:**
> ... installed Parallels and Ubuntu in it. It works wonderfully, ...

I have a mac mini solo with 1 GB. I have installed and used ubuntu 6.0.6 dual boot and ubuntu was very good, at least as quick as OSX, but it would not play internal sound (a minor inconvenience), nor would it recognize Bluetooth mouse and keyboard.
I thought parallels would be a better way, and use a bit less of my 60 GB disk. It installs very easily and now my ubuntu guest plays internal sound, and does Bluetooth mouse and keyboard (all via OSX). 
However, I find a major problem with mouse movement. It lags and is jerky. Not completely unusable but feels bad.
Parallels had the same mouse problem with a Windows guest until I installed the tools for windows.
It seems we need the same kind of parallels tools installation for X windows systems - or am I the only one to have annoying mouse problems with ubuntu?

---

### Post by hajk on 2006-09-01
Yes, the trackpad on my MacBook is a little jerky when running Ubuntu in a Parallels VM. Turning the sensitivity of the mouse way down in System - Preferences - Mouse helps a bit, though.

---

