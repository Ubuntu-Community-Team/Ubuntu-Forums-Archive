---
title: "Catch 22 when installing downloaded packages"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2006-08-15
I was downloading dependencies for Bochs and for the second time got the problem: bochs_2.2.5-1_i386 needs bochs-wx_2.2.5-1_i386 to be installed, and the latter needs the former, so I can't install either. I came across te same situation before with licq. I will appreciate your help, despite the question might be stupid.

---

### Post by az on 2006-08-15
> **NT4.0 said:**
> I was downloading dependencies for Bochs and for the second time got the problem: bochs_2.2.5-1_i386 needs bochs-wx_2.2.5-1_i386 to be installed, and the latter needs the former, so I can't install either. I came across te same situation before with licq. I will appreciate your help, despite the question might be stupid.

1.  Is Bochs still maintained?
2.  Why are you downloading and installing by hand?  Any package manager should handle these dependencies for you.

---

### Post by NT4.0 on 2006-08-15
I was searching for any kind of virtual pc program, and Bochs seemed good... looks like it is maintained, though I paid little attention to it at that time.

I would hate installing the programs just by letting the package manager do all the work since I need to have the software collection on my own media so that I could make up the working system in a short time when I reinstall the OS or install it on a different computer (plus, reformatting will erase all the stuff so I will have to repeat the job after reinstallation). Second, I have dial-up and without knowing the size of the download I can't maintain the process (10 megs is already something I would think of before downloading).

---

### Post by mcduck on 2006-08-15
> **NT4.0 said:**
> I was searching for any kind of virtual pc program, and Bochs seemed good... looks like it is maintained, though I paid little attention to it at that time.

I would hate installing the programs just by letting the package manager do all the work since I need to have the software collection on my own media so that I could make up the working system in a short time when I reinstall the OS or install it on a different computer (plus, reformatting will erase all the stuff so I will have to repeat the job after reinstallation). Second, I have dial-up and without knowing the size of the download I can't maintain the process (10 megs is already something I would think of before downloading).
to install those packages by hand you just need to install both at the same time:
'sudo dpkg -i package1.deb package2.deb'

But I'd recommend the package manager too. It will tell you how much you need to download so that shouldn't be a problem. And it caches all installed package files to /var/cache/apt/archives, so if you afterwards copy everything from there to a CD you won't need to download them again. You can just copy files from the CD to your desktop and run 'sudo dpkg -i *.deb' to install them all :)

---

### Post by NT4.0 on 2006-08-15
Thanks! The console showed me some errors but the programs does start. I liked the command-line way of handling packages. Does it mean I can install as many packages as I want in this way (e.g. a whole bunch of Totem plugins just by doing sudo dpkg -i pack1 pack2 [...] packN ?

---

### Post by eccentricity on 2006-08-15
> **mcduck said:**
> to install those packages by hand you just need to install both at the same time:
'sudo dpkg -i package1.deb package2.deb'

But I'd recommend the package manager too. It will tell you how much you need to download so that shouldn't be a problem. And it caches all installed package files to /var/cache/apt/archives, so if you afterwards copy everything from there to a CD you won't need to download them again. You can just copy files from the CD to your desktop and run 'sudo dpkg -i *.deb' to install them all :)

I'm glad you mentioned this. I have a bunch of emulators on CD that are in .tar format for general linux. 

[http://www.fenner.info/emulation/index.html](http://www.fenner.info/emulation/index.html) 

quoted from above website --->aranym, atari5200, atari800, atariplusplus, autoprobe, dgen, dosbox, fceu,gngeo, hatari, mednafen, mupen64, neopocott, o2em, openmsx, qemu, 

Those are just an example from that website above that I want to have installed on ubuntu. I don't know how to install through the package manager nor do I know if you even can do it through that. Any help is appreciated, thanks :D 

-Ryan

---

