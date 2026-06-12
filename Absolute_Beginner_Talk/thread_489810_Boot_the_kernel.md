---
title: "Boot the kernel"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2007-07-01
What is the absolute minimum setup needed to boot a linux kernel to a command line?

---

### Post by starcraft.man on 2007-07-01
> **ecs_pf5 said:**
> What is the absolute minimum setup needed to boot a linux kernel to a command line?

Huh? All you want is the console? I hope you know what your doing...

I know the absolute minimum for running graphical Ubuntu is 256 MB RAM (any machine should have that, if not I advise you upgrade to it if possible), console only would be significantly less than that I suppose. Any p3 or up machine should handle it just fine. The rest can be generic, long as the mobo is something well supported like intel the integrated graphics/sound (or separate video card should work). Ubuntu isn't very demanding (and usually runs well on old machines)... unlike a certain new Windows OS.

---

### Post by ecs_pf5 on 2007-07-01
Thanks starcraft. I'm just playing about with stuff really, I have Ubuntu 7.04 running okay & am generally exploring linux in general.

I wanted to try my hand at understanding the absolute centre of it all by making up a very tiny minimal 'distro' of my own, comprising the boot machinery (grub & some config files?), a kernel, and whatever else would be needed to just fire it up in fullscreen terminal mode. Kinda like DOS. No GUI machinery or apps.

I'm just learning by playing with lego bricks as it were :p

So in addition to actual machine specs, I'm hoping to discover what files etc might be needed just to boot into console.

Yeah I have noticed Ubuntu runs a lot quicker than Vista on my machine.

---

### Post by starcraft.man on 2007-07-01
> **ecs_pf5 said:**
> Thanks starcraft. I'm just playing about with stuff really, I have Ubuntu 7.04 running okay & am generally exploring linux in general.

I wanted to try my hand at understanding the absolute centre of it all by making up a very tiny minimal 'distro' of my own, comprising the boot machinery (grub & some config files?), a kernel, and whatever else would be needed to just fire it up in fullscreen terminal mode. Kinda like DOS. No GUI machinery or apps.

I'm just learning by playing with lego bricks as it were :p

So in addition to actual machine specs, I'm hoping to discover what files etc might be needed just to boot into console.

[Linux Command]("http://www.linuxcommand.org/") is a good site to understand the basic commands, scripting and then more advanced commands listed in the man pages. 

As for constructing a distro from base files, I can't help there... I'm just a knowledgeable user, not a developer. I believe [these applications]("http://linuxappfinder.com/development/bootlivecdcreators") may be what you want. They will let you customize a distro (i.e. if you the files or ISO, not sure how it works, it lets you repackage or pick the ones you want). Read up on it, I can't help with it. Good luck.

Edit: You may wanna upgrade your RAM to at least 2GB to get better performance out of Vista (if you still want to use it or game), that seems to me to be the weakest point of your rig (assuming specs in sig are yours). IMO, Vista should not be run on any systems with less than 2, I know it can work on 1 but Vista is a serious RAM hog and caches tonnes in order to just work. As for Radeon... bleh. Hope ya don't have any trouble in Ubuntu with that...

---

### Post by ecs_pf5 on 2007-07-01
dfsbuild looks interesting, thanks for that.

In DOS for example, you need a boot sector on the disk, then you need (I think) io.sys, autoexec.bat, maybe config.sys, and command.com

With those 4 or 5 items, that's all you need. sure it won't do much but it will boot to a basic A:\ prompt.

That's all I'm trying to do, but in linux. Just to help get my head round it from the bottom up as it were.

the dfsbuild you pointed me to looks like the right sort of thing to investigate for that. Cheers :)

---

### Post by starcraft.man on 2007-07-01
> **ecs_pf5 said:**
> dfsbuild looks interesting, thanks for that.

In DOS for example, you need a boot sector on the disk, then you need (I think) io.sys, autoexec.bat, maybe config.sys, and command.com

With those 4 or 5 items, that's all you need. sure it won't do much but it will boot to a basic A:\ prompt.

That's all I'm trying to do, but in linux. Just to help get my head round it from the bottom up as it were.

the dfsbuild you pointed me to looks like the right sort of thing to investigate for that. Cheers :)

No problem, I just find it easier to pull up one of the console emulators like Gnome Terminal or Konsole (gnome and kde respective defaults). Not to mention there is always recovery mode (second option under your kernel in GRUB list) that will drop you in a minimal console environment with all commands at your disposal and root powers (its mostly meant for system recovery). 

Anyway, good luck with that.

---

### Post by DBStevens on 2007-07-01
DSL works just fine in 128MB sharing some ram for video, you should be able to get a command line system under 32 MB

 [Yep it is DSL]("http://www.damnsmalllinux.org/")

---

