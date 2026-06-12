---
title: "Ubuntu Teething Problems (multiboot and monitors)"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by NMGeko on 2006-12-10
ok.
im new to ubuntu, like, this afternoon new.
as for linux, ive avoided it for a while, but i want to at least know how to use it even if its just to teach people who use their computers for internet browsers and constantly want me to fix their virus problems.

but aside from that, i installed ubuntu and run into two main problems.
i know its bad to just post without really trying to fix it yourself, but ive looked around for about half an hour now, and due to not really knowing what im doing on here anyway, and the INSANE amount of information, ive given up. i need some direction.

Problem 1:
i have 3 operating systems on here, Ubuntu of course, Xp pro, and Vista(rc1).
now, i want a working bootloader!
grub has taken over my MBR but i dont mind, the thing i dont like is that to boot into vista or xp i need to go to the option about "windows vista/loghorn" which then brings up my old vista bootloader. Thats pretty crap. I dont care what i use, i just want to have them all accessible from the one menu, and i dont want to totally screw over my MBR in the process.

Problem 2:
This is a notebook that i usually run in dual monitor. the main screen is a 1440x900 widescreen and the secondary 1280x1024 run off the radeon mobility 9600. WHen i first cranked this up, only the second monitor worked and i couldnt find any option to enable the other. i rebooted with it unplugged and the main monitor kicked in but only at 1024x768. when i changed the res up to 1440x900 (which it detected all by itself and seemed happy about) it went crazy and there was a lot of graphical artifacts. its hard to describe, but it wasnt right, if i made a box on the far right of the screen, a half interlaced version would appear on the left of my screen as well. wierd. 1024x768 seems to be the highest resolution that doesnt do any of this. it makes it really hard to search for a solution when its hard enough just to describe the problem!

looking forward to some guidance and apologies on the long post...

Gavin

---

### Post by CatKiller on 2006-12-10
Welcome to the community!

Problem 1:
The GRUB menu can be edited with the command ```
gksudo gedit /boot/grub/menu.lst
``` (that's **l** as in lower-case L, if you aren't copy-n-pasting). You could add an entry in there for Vista, but it is common practise to chain-load bootloaders in this way, so there's no guarantee that Vista will have its own bootloader on its partition. Interchange XP for Vista in the previous sentence, depending on whose bootloader it is that you're selecting from the GRUB menu at the moment.

It may just be a case of specifying the other partition in menu.lst as well, though. I've not had to do it, myself.

Problem 2:
Sounds to me like a refresh rate issue with the higher resolution, although I've seen similar things from the monitor image being misaligned on the screen.

Dual monitors can be tricky to set up, and how you do it depends on how your machine is physically set up. There's [TwinView]("http://www.ubuntuforums.org/showthread.php?p=1773584") (nVidia's solution for a dual-head card), "[Big Desktop]("http://www.ubuntuforums.org/showthread.php?p=1773544")" (Ati's solution for same), [MergedFB]("http://www.ubuntuforums.org/showthread.php?p=1773710") and [Xinerama]("http://www.ubuntuforums.org/showthread.php?p=1773624"), which is a more general solution. I don't have that much experience of any of these - I use a [Dual Screen]("http://doc.gwos.org/index.php/DualMonitors") setup.

EDIT: I've just noticed that you're using integrated Ati graphics. Ati's drivers are generally regarded as not being as good as nVidia's equivalent, but you might find that installing Ati's [proprietary drivers]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") might help to some extent.

Good luck!

---

### Post by rsambuca on 2006-12-10
I am almost positive that the Vista bootloader is not on its own partition.  The only way I know how to get around the jumping from the grub loader to the vista loader is to install ubuntu first, XP second - and add ubuntu to the XP boot.ini file.  Then install Vista, and it uses the XP boot.ini file for its own bootloader.

---

