---
title: "Fresh custom install questions"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by infinite regress on 2008-01-05
Hi everyone,

I'm new to linux, and have been working on getting ubuntu working on my old-ish laptop.
It runs xp fine, so when I install gutsy and find that it is very very sluggish = sad. I'm running with 256 RAM, so I want to reinstall with a lighter system.

I want to install from a command-line system, so i can only install the light apps. Got a bit confused... What's all this business with file managers and windows managers and desktop enviroments, GNOME, GDE, etc?

After looking at the low memory systems docs, at [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems), these are the components i need to install, (I can mix and match?)
[LIST]
[*]_Windows manager_: IceWM or Fluxbox
[*]_File manager_: xfe or Rox filer
[*]_Display manager_: GDM/KDM/XDM
[*]_Terminal_: xterm
[/LIST]

Is there anything else I am missing? Will this work?

so basically, I can run: ```
sudo aptitude install xorg fluxbox rox-filer xdm, 
``` and on reboot that'll get me into a running GUI?

I'm not quite sure why Ubuntu is so slow (takes ~half minute to load up opera), I'm thinking it may be my graphics drivers not up-to-date? I've got a intel 82855/852 GM, Apparently, libgl1-mesa-dri is up to date, so that's not the problem... Any ideas?

Thanks for your help guys...

---

### Post by Alx c on 2008-01-05
You will surely need to install openoffice. You may whant to install and old version for it to go fast. An other thing you can do is install xubuntu which is ubuntu but for slower computers (the graphics are worse but it goes fast)

---

### Post by Sef on 2008-01-05
> I'm not quite sure why Ubuntu is so slow (takes ~half minute to load up opera), I'm thinking it may be my graphics drivers not up-to-date?

256 mb ram is the minimum to run Ubuntu.  If you doubled it to 512 mb ram, it would run much faster.  With your graphics card, it depends if it has a separate memory or uses ram.

---

