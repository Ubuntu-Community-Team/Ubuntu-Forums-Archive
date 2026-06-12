---
title: "Installing stuff..."
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-09-13
Some programs are available through synaptic, like Inkscape, and some I just 
download and run from the directory, like blender3d. But there are also
those where the tar.gz contains a usr directory with subfolders that is meant to be
copied into the /usr folder.
Now, it is possible to install that through getting root access and copying the files
manually, but it feels a little clumsy, and is a source of problems when one want to
uninstall something.

So to the actual question: Is there any command/program to automate this?

---

### Post by tonysathre on 2005-09-13
are u actually compiling the program with ./configure, make, make install, make clean?

---

### Post by red_Marvin on 2005-09-13
The programs I talk about come with binaries, or so it seems, because I can run them...

---

### Post by tonysathre on 2005-09-13
i think u need to compile them like i said, try that, if that dont work post back, and what do u asctually want to automate, moving those file around? if you compile them it will put all the files where they need to be

---

### Post by red_Marvin on 2005-09-13
I have programming as a sort of hobby, and AFAIK the term "compiling" means
produce executables/binaries from source.
Since I can run the program without problems that means executables/binaries
is already compiled and included.

It just needs to be moved into the right places (AFAIK)

What I ask for is if anyone knows any program that can automate this movement
and perhaps keep an uninstall database.

If you mean something other by compiling than what I stated please elaborate.

---

### Post by wmcbrine on 2005-09-13
I think you'll have to tell us the actual program(s) in question. It's an unusual way to distribute Linux binaries, so there's no general solution. Such packages typically come with an installer, though (often .bin or .sh, particularly install.sh). Uninstallation is another question.

---

### Post by tonysathre on 2005-09-13
i have never heard of a program that does this for u except synaptic, i myself have never had to do that, maybe i just dont follow what u mean by having to move files around manually, after downloading something, i always just compiled them by doing ./configure make make install make clean and all the files just get put where they need to be.

all binaries are stored in /usr/bin, usr/sbin and /bin and /sbin, maybe try putting the binaries in /usr/bin all in one directory so they can easily be deleted.

is every file that u downloaded with the archive a binary?

---

### Post by red_Marvin on 2005-09-13
I'm just speaking in general, and it is possible that I'm making a mountain out of a
molehill.
I think the game metal blob solid is distributed that way, but no promises.

---

### Post by tonysathre on 2005-09-13
sorry but i dont know what to tell u because everything that i have ever downloaded had to be compiled before i could use it, and this resolves all the problems that u seem to be having, maybe try finding an archive that needs compiling

---

### Post by red_Marvin on 2005-09-13
Ah-Ha! Now I return with solid facts. ^_^
When I downloaded the blobwars: motal blob solid generic i386 linux rpm 
(pre-compiled) the package contains a folder named "." with the subfolder "usr"
which contains the folders "games" and "share" (which in turn contain...). Now,
I clearly recognize these folders from the /usr directory and I therefor copied all files
to that directory (This required root/su access) and lo and behold, the game worked
It even appeared in the games section of the Gnome menu.

This is what I meant...

---

### Post by tonysathre on 2005-09-13
excellent work, sorry i wasnt more help

---

### Post by red_Marvin on 2005-09-13
Oh, I didn't do that now, but before, (I've had one re installation of ubuntu between)
but I downloaded the rpm just to check.

---

### Post by tageiru on 2005-09-13
[QUOTE=red_Marvin]Ah-Ha! Now I return with solid facts. ^_^
When I downloaded the blobwars: motal blob solid generic i386 linux rpm 
(pre-compiled) the package contains a folder named "." with the subfolder "usr"
which contains the folders "games" and "share" (which in turn contain...). Now,
I clearly recognize these folders from the /usr directory and I therefor copied all files
to that directory (This required root/su access) and lo and behold, the game worked
It even appeared in the games section of the Gnome menu.

This is what I meant...[/QUOTE]
Be _very_ careful about blindingly copying stuff into the filesystem tree. You might end up destroying your ubuntu installation.

Also, an rpm is a package for red hat and its derivatives (ubuntu is not a red hat derivative). It might not be enough to copy its contents into the ubuntu filesystem tree since a rpm package also includes scripts that gets run before and after it is installed. There is an application for converting rpm packages into deb packages (which ubuntu use) called alien. But keep in mind that an rpm is ment for a red hat derivate and it might not work at all in ubuntu.

The safest course of action is to always use packages ment for ubuntu.

---

### Post by wmcbrine on 2005-09-13
[QUOTE=red_Marvin]rpm[/QUOTE]Ah, RPM. That was all you needed to say.

RPMs are really intended for RPM-based distros: Red Hat/Fedora, Mandrake/Mandrive, SuSE, etc. Ubuntu is part of the other great family of distros that use prepackaged binaries, the Debian group. Ideally, you should find a DEB file instead of an RPM. No, scratch that -- *ideally,* you should download and install the package via Synaptic, or apt. But if that's not possible, you can use a program called "alien" to convert RPM to DEB, and then use dpkg to (try to) install the resulting DEB.

---

### Post by aysiu on 2005-09-13
[QUOTE=wmcbrine] you can use a program called "alien" to convert RPM to DEB, and then use dpkg to (try to) install the resulting DEB.[/QUOTE] Or you can use alien to just install the rpm. For example, if your RPM is called program.rpm, just type this in the terminal ```
sudo alien -i program.rpm
```.

---

### Post by red_Marvin on 2005-09-13
Ah, so that might be the problem then, wrong format heh.

Well, I *am* quite the noob, and I always go for the trial and error method :p

---

### Post by sneax on 2005-09-13
[QUOTE=wmcbrine]I think you'll have to tell us the actual program(s) in question. It's an unusual way to distribute Linux binaries, so there's no general solution. Such packages typically come with an installer, though (often .bin or .sh, particularly install.sh). Uninstallation is another question.[/QUOTE]

Limewire doesn't. I just put it in 
/home/user/progs/limewire
and I just run it from there. It works as far as I know, there's no installer (for linux there's just a RunLime.sh in it). This is probably not the best solution (I'm fairly new) but it works and it seems clean to me!

---

### Post by aysiu on 2005-09-13
[QUOTE=sneax]Limewire doesn't. I just put it in 
/home/user/progs/limewire
and I just run it from there. It works as far as I know, there's no installer (for linux there's just a RunLime.sh in it). This is probably not the best solution (I'm fairly new) but it works and it seems clean to me![/QUOTE] Try following these instructions:

[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

and then these instructions:

[http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire)

---

### Post by cvmostert on 2005-10-30
thanx for the info on alien -i, worked fine for me with xdvdshrink. After installing dvdauther, i am currently shrinking a dvd... hope it turns out fine.
:-)

---

### Post by BLTicklemonster on 2005-12-11
Instead of limewire, try this: [http://www.ubuntuforums.org/showthread.php?t=80638](http://www.ubuntuforums.org/showthread.php?t=80638) theres even a how to install from .rpm posted on page two.

---

### Post by Bartender on 2005-12-11
Hey, is this the same BLT Ticklemonster who said he was done with Linux a week ago?  
If so, I'm glad to see you back.  I'd been learning from your most excellent replies and was sorry to read your farewell message.

Welcome back, BLT

---

### Post by BLTicklemonster on 2005-12-11
Yeah, it's me. I can't leave well enough alone, lol. Thanks.

---

