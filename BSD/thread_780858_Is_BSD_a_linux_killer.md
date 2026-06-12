---
title: "Is *BSD a linux killer?"
date: 2008-05-03
forum: BSD
---

### Post by gamergod131 on 2008-05-03
Now I don't know much about linux, bsd, or unix OS' in general, however almost  everything that I have read is that the BSD kernel is much faster, and more stable than the linux kernel is. I heard linux apps faster than on linux natively, and the hardware it supports works perfectly. Besides the smaller hardware compatibility list, is there even a reason to run linux anymore if your hardware supports bsd? 

PS-I have tried ubuntu and openSUSE and am loving them both(besides my lexmark printer not being supported). I have tried pc-bsd, but the lack of my wifi support made me do a clean ubuntu install.

---

### Post by cardinals_fan on 2008-05-03
I like BSD more, if that's what you mean.

---

### Post by CREEPING DEATH on 2008-05-03
It's faster, more stable, and the hardware and desktop support sucks.  By default, it uses a non-journaling file system so if you lose power you lose data.  It's usually 2 years - or more - behind Linux as far as driver support goes.
Both BSD hardcore guys I know (both are network admins) use Linux on their desktop and laptop machines.

CD

---

### Post by cardinals_fan on 2008-05-04
> **CREEPING DEATH said:**
> It's faster, more stable, and the hardware and desktop support sucks.  By default, it uses a non-journaling file system so if you lose power you lose data.  It's usually 2 years - or more - behind Linux as far as driver support goes.
Both BSD hardcore guys I know (both are network admins) use Linux on their desktop and laptop machines.

CD
Interesting.  Hardware support is one of the reasons I'm using BSD more these days - my wireless card works 'out of the box', unlike on Linux where it takes some witchcraft to get it running.

---

### Post by SunnyRabbiera on 2008-05-04
Well it depends, BSD has a lot of potential but for the most part yes there are a few things that are behind on BSD.
I have nothing against BSD, its a great OS though I would never suggest it to a newcomer because of stuff a newcommer might come looking for (like flash though soon that might no longer be a problem with flash practically going open source)
I heard PC-BSD is rock solid and pretty easy, and it could be a contender once things are sorted out.

---

### Post by lespaul_rentals on 2008-05-05
The BSDs are far better in many ways.  The projects are more efficient and produce higher-quality code.  Not only are FreeBSD and OpenBSD rock solid, but there is also a lot of innovation in the way of NetBSD, which aims to run on almost any device, and DragonflyBSD, a newer BSD.  However, with only 4 BSD projects out there, each with their own focus, a lot more gets done.  Just look at Theo de Raadt.  He's a genius and his team of developers writes amazing, stable code.  He is responsible for OpenSSH (which I **guarantee** you use in some way, shape, or form) as well as many other security applications used in both BSD and Linux.  He has literally dedicated his life to the open-source movement.  You probably have him to thank for a few hardware drivers as well.

GNU/Linux has its place as well.  It's built on a great kernel and some of the applications out there are fantastic.  However, a lot of the projects seem a bit shaky at the foundations.

---

### Post by cardinals_fan on 2008-05-05
> **lespaul_rentals said:**
> You probably have him to thank for a few hardware drivers as well.

True enough.  I will worship him for the rum driver :)

---

### Post by Ptero-4 on 2008-05-06
Lets see.

Linux.

Supports more hardware.
Support more and better filesystems.
Is more cool (read: more flashy and shiny).

BSD.

Is more (aarrgh) "professional" (read: boring looking, less flashy and shiny).
Support "perfect" what few hardware it does support.

---

### Post by tw3k on 2008-05-06
simply, no.

---

### Post by cardinals_fan on 2008-05-06
> **Ptero-4 said:**
> Lets see.

Linux.

Supports more hardware.
Support more and better filesystems.
Is more cool (read: more flashy and shiny).

BSD.

Is more (aarrgh) "professional" (read: boring looking, less flashy and shiny).
Support "perfect" what few hardware it does support.
I like both, but how can you grade the OS on 'flashy-shiny'.  That's the role of the window manager

---

### Post by SunnyRabbiera on 2008-05-06
But one thing I have yet to see is something as breakout for BSD as Ubuntu is for Linux, plus there is one tool I dont think I can live without these days:
apt.
Sure PCBSD has some tools in it that look interesting, but I am far too used to the debian way of things.
Heck out of all the installers and systems I have used I dont think anything beats apt in terms of its ability to update packages on its own, its library and its general ease of use... I even think its easier then windows executables, which I understand the PCBSD installers work like.

By the way any of you know how to get PCBSD to run in virtualbox?

---

### Post by lespaul_rentals on 2008-05-06
> **Ptero-4 said:**
> Lets see.

Linux.

Supports more hardware.
Support more and better filesystems.
Is more cool (read: more flashy and shiny).

BSD.

Is more (aarrgh) "professional" (read: boring looking, less flashy and shiny).
Support "perfect" what few hardware it does support.

Let's see.

That post makes Ptero-4 sound like he knows nothing of which he speaks.

> **SunnyRabbiera said:**
> But one thing I have yet to see is something as breakout for BSD as Ubuntu is for Linux, plus there is one tool I dont think I can live without these days:
apt.
Sure PCBSD has some tools in it that look interesting, but I am far too used to the debian way of things.
Heck out of all the installers and systems I have used I dont think anything beats apt in terms of its ability to update packages on its own, its library and its general ease of use... I even think its easier then windows executables, which I understand the PCBSD installers work like.

FreeBSD is intended to work in the server environment, and to be honest is think FreeBSD **is** the "breakout" for BSD.  For server admins who want to set up a server and just leave it running with no issues (an appliance operating system, if you will) OpenBSD will fill the space.  There's a BSD for everything, and you know when you install one you're going to have a stable, reliable operating system that just works, no matter what you have in mind for it.  Home desktop?  Yes.  Home file server?  Yes.  Enterprise server?  Yes.  There's nothing you can't do with the BSDs, and the code that is put into the operating systems is of high quality -- far more consistent than Linux.

APT is fantastic, Sunny.  I totally agree with you there.  You need look no further than APT to fall on your face in worship for the Debian team.  It is a very smart package manager, and when coupled with a repository the size of Debian or Ubuntu's, it makes for a great package manager.

I will say this, however.  FreeBSD has something almost as good in the pkg_add system, and with the option of ports, I really don't see any reason to not try something new.  You can modify your make.conf file so everytime it compiles a new port, you are getting an application made to run at it's top performance on your hardware.  This means that spending 5 extra minutes can make for a far more stable and customizable server.

---

### Post by lespaul_rentals on 2008-05-06
*ignore*

---

### Post by cardinals_fan on 2008-05-06
Pkgsrc is nice too :)

---

### Post by lespaul_rentals on 2008-05-07
> **cardinals_fan said:**
> Pkgsrc is nice too :)

+1.

---

### Post by Ptero-4 on 2008-05-08
> **cardinals_fan said:**
> I like both, but how can you grade the OS on 'flashy-shiny'.  That's the role of the window manager

I was actually talking about the stuff that happens both before (at boot, before X11 is started) and after (from the moment X11 is shutoff up until the PC is turned off) you actually get to your desktop. So no the windowmanager have nothing to do in that. It's the job of the bootloader and kernel/userland apps that run during the boot and shutdown sequences that define if the OS boots/shutdown with a graphical screen (like SuSE, Mandriva, PCLinux, Elive, Zenwalk, etc) or shows kernel text (like BSD and earlier linux distros circa 1995).

P.D: I use both (you can't see it since the "OS" section of the user data haven't been ported to the new forum software yet, but I had Xubuntu and FreeBSD marked in my user data).

---

### Post by lespaul_rentals on 2008-05-08
> **Ptero-4 said:**
> I was actually talking about the stuff that happens both before (at boot, before X11 is started) and after (from the moment X11 is shutoff up until the PC is turned off) you actually get to your desktop. So no the windowmanager have nothing to do in that. It's the job of the bootloader and kernel/userland apps that run during the boot and shutdown sequences that define if the OS boots/shutdown with a graphical screen (like SuSE, Mandriva, PCLinux, Elive, Zenwalk, etc) or shows kernel text (like BSD and earlier linux distros circa 1995).

I personally like the scrolling text during boot.  It lets me know what's going on far more than a progress bar that mysteriously freezes.

---

### Post by MONODA on 2008-05-08
hmm... I might give FreeBSD a try, does it work well on laptops? or would desltop BSD or PC BSD be better for me? I dont mind trying to get it to work.

---

### Post by lespaul_rentals on 2008-05-08
> **MONODA said:**
> hmm... I might give FreeBSD a try, does it work well on laptops? or would desltop BSD or PC BSD be better for me? I dont mind trying to get it to work.

The hardware support is about 80% of what Linux has.  It will probably work, though.  If anything doesn't, it will be the wireless most likely.  And give it a try, it's fun.  :)

---

### Post by MONODA on 2008-05-08
it sounds good, does it work with grub? I dont want to erase my arch.
EDIT: also, what configuration will I need to do to get a working system? is that all explained in the documentation?
EDIT2: one last thing, is freebsd rolling release? Thank you so much :D

---

### Post by lespaul_rentals on 2008-05-08
> **MONODA said:**
> it sounds good, does it work with grub? I dont want to erase my arch.
EDIT: also, what configuration will I need to do to get a working system? is that all explained in the documentation?

I think you can install GRUB during the installation.  FreeBSD also has its own bootloader.  I think it gives you a choice between the two.

The documentation in FreeBSD is fantastic.  If you are comfortable with the Linux command-line you should have no problem learning FreeBSD.

If you want some more information, I wrote a little review here: [http://ubuntuforums.org/showthread.php?t=758029](http://ubuntuforums.org/showthread.php?t=758029)

---

### Post by MONODA on 2008-05-08
thank you so much, Just one more thing, is it rolling release? (I think I am asking for too much XD)

---

### Post by lespaul_rentals on 2008-05-08
> **MONODA said:**
> thank you so much, Just one more thing, is it rolling release? (I think I am asking for too much XD)

Yes.

---

### Post by MONODA on 2008-05-08
sweet!

---

### Post by sujoy on 2008-05-08
I brought a FreeBSD7 DVD from college library (came with a magazine). It will be exiting to finally lay hands on a UNIX system :)

---

### Post by Ptero-4 on 2008-05-09
> **MONODA said:**
> hmm... I might give FreeBSD a try, does it work well on laptops? or would desltop BSD or PC BSD be better for me? I dont mind trying to get it to work.

On laptops wifi and acpi might give trouble.

---

### Post by fuzzyk.k on 2008-05-09
i personally dnt think its a linux killer it all depends on what a user is lookin for in a system:)

---

### Post by MONODA on 2008-05-09
I just installed FreeBSD 7 but am having some problems, here is my post:
[http://ubuntuforums.org/showthread.php?p=4916898#post4916898](http://ubuntuforums.org/showthread.php?p=4916898#post4916898)
thanks a lot

---

### Post by spectrevk on 2008-05-15
This seems like a good place to ask this.

Recently I started using Ubuntu, which caused quite a few problems at first, but I finally wrangled it into more or less working condition, with a few remaining quibbles. That said, I'm an adventurous guy, and the near-constant crowing of BSD people got me wondering about it. My situation is this:

I am not a programmer. I am a writer, and I have some technical acumen, but for the most part, what I want is a working laptop, ideally running open-source software, that lets me watch video files, use the internet, and store files. I'd like for all of the hardware on my laptop to work, preferably out of the box. The laptop in question is a Compaq Presario V5000. I recently downloaded a few BSD distros, including PC BSD. What I want to know is whether this is likely to work well, of if I'm setting myself up for another week of inoperability while I attempt to find help (I don't hold much hope here, as the response of most BSD communities seems to either be silence or elitist scolding). The other thing I'd like to know is if there is any good reason why someone like me would want to switch to BSD. It's more secure, but I've never had security problems in linux, and neither has anyone I know. If it's faster, that's something, but I'm also concerned about power management. It's more "stable", but what does that really translate into when most of the stuff I'm using is in a desktop environment like Gnome, so I'm at the mercy of Gnome's stability more than BSD's?

---

### Post by cardinals_fan on 2008-05-15
> **spectrevk said:**
> This seems like a good place to ask this.

Recently I started using Ubuntu, which caused quite a few problems at first, but I finally wrangled it into more or less working condition, with a few remaining quibbles. That said, I'm an adventurous guy, and the near-constant crowing of BSD people got me wondering about it. My situation is this:

Where have you heard near-constant crowing?  Most BSD users are very quiet...

Regardless, you might want to try DesktopBSD.  It's pretty easy to install/use, and you have access to the full FreeBSD ports collection.  It has a preconfigured KDE gui.  Will it be better?  Maybe.  I have found most BSDs to be more stable then most Linuxes, but there are disadvantages.  Most help is through mailing lists, though forums like BSDnexus are improving.  So my advice is this: try DesktopBSD on a spare partition.  If you don't like it, return to Ubuntu and maybe try some other Linux distros like Zenwalk.

---

### Post by spectrevk on 2008-05-15
> **cardinals_fan said:**
> Where have you heard near-constant crowing?  Most BSD users are very quiet...

Regardless, you might want to try DesktopBSD.  It's pretty easy to install/use, and you have access to the full FreeBSD ports collection.  It has a preconfigured KDE gui.  Will it be better?  Maybe.  I have found most BSDs to be more stable then most Linuxes, but there are disadvantages.  Most help is through mailing lists, though forums like BSDnexus are improving.  So my advice is this: try DesktopBSD on a spare partition.  If you don't like it, return to Ubuntu and maybe try some other Linux distros like Zenwalk.

What are the benefits of DesktopBSD versus PCBSD? I thought they both were more graphical, simpler BSDs. And assuming that I'm in a desktop environment, what would the difference be versus a linux distro? Faster performance?

---

### Post by cardinals_fan on 2008-05-15
> **spectrevk said:**
> What are the benefits of DesktopBSD versus PCBSD? I thought they both were more graphical, simpler BSDs. And assuming that I'm in a desktop environment, what would the difference be versus a linux distro? Faster performance?
PC-BSD uses its own PBI package management system, which I strongly dislike.  DesktopBSD is really just FreeBSD with a GUI preconfigured.  This means that you can take advantage of the extensive FreeBSD ports collection.

I am a huge fan of the various BSDs and use them on my desktop.  For you, though, I don't know whether they're better than Linux.  They're somewhat more 'hands-on', and I've found them to be significantly more stable.  Your experiences may vary.

---

### Post by cammin on 2008-05-15
PC-BSD uses FreeBSD ports and packages too. PBI's are just an extra option.

---

### Post by cardinals_fan on 2008-05-15
> **cammin said:**
> PC-BSD uses FreeBSD ports and packages too. PBI's are just an extra option.
I just checked.  Apparently this is an option.  I still prefer DesktopBSD though :)

---

### Post by spectrevk on 2008-05-16
I heard that Desktop BSD had a Live disc, but I can't seem to find one on their site.

---

### Post by cardinals_fan on 2008-05-16
> **spectrevk said:**
> I heard that Desktop BSD had a Live disc, but I can't seem to find one on their site.
Isn't the regular CD download live?

---

### Post by chachawpi on 2008-05-16
> **cardinals_fan said:**
> Isn't the regular CD download live?

Yes it is.  When you boot up you have the option of choosing "Live" or "Install."

---

### Post by tbrminsanity on 2008-05-16
BSD has its place but I highly doubt that either Linux or BSD will ever kill each other.  Both have their niche markets and co-exist quite nicely.  I run Linux as my desktop but if I wanted to have a dedicated server (especially a web server) I would seriously consider BSD.  I was looking into doing a project where you would create an install disk that would first ask what kernel the user wanted, then the desktop environment, and finally what overall packages they want.  It would have to be Debian based as that or Gentoo are the only organizations that can mix and match the BSD kernel and Linux kernel with Gnome, KDE, ... .  The only thing stopping me from starting this project is I can't see a real need for it.  Debian and Gentoo already offer Linux based and BSD based install disks.  The only extra thing I could do is tailor the install disk for businesses for either desktops or servers.

---

### Post by dspari1 on 2008-05-22
I've tried PC-BSD, but when all said is done, Linux and BSD are pretty much the same thing(KDE is KDE) especially if you avoid using the command line like the plague.

---

### Post by chachawpi on 2008-05-24
> **dspari1 said:**
> I've tried PC-BSD, but when all said is done, Linux and BSD are pretty much the same thing(KDE is KDE) especially if you avoid using the command line like the plague.
How can you use *nix and avoid the command line?  Blasphemy!

---

### Post by tbrminsanity on 2008-05-26
Even if you do use a CLI, the different variations are very slight.    Unix is Unix is Unix.  The main differences between the various Unix OSs are technical and not very noticeable from the UI (which is a good thing).

---

### Post by CrazyArcher on 2008-06-03
No way BSD will be a Linux killer. Those 2 OS families are both awesome, but each one has its own niche. IMO regular desktop users don't have to compile their programs from source. Desktop systems tend to be very dynamic: programs get installed, programs get erased, so APT way of dealing with things is the most convinient. Not that Linux takes from you the ability to compile stuff on your machine, but it's not the way normal people tend to work. :D
BSD is probably the best system out for some static system, that is set up once and for all, running forever at the very optimal configuration. If I had to choose an OS for a server or for some dedicated number-crunching machine, I'd go for BSD.

---

### Post by cardinals_fan on 2008-06-03
> **CrazyArcher said:**
> No way BSD will be a Linux killer. Those 2 OS families are both awesome, but each one has its own niche. IMO regular desktop users don't have to compile their programs from source. Desktop systems tend to be very dynamic: programs get installed, programs get erased, so APT way of dealing with things is the most convinient. Not that Linux takes from you the ability to compile stuff on your machine, but it's not the way normal people tend to work. :D
BSD is probably the best system out for some static system, that is set up once and for all, running forever at the very optimal configuration. If I had to choose an OS for a server or for some dedicated number-crunching machine, I'd go for BSD.
BSDs have packaging systems too...

---

### Post by tbrminsanity on 2008-06-03
It would be a real pain the the butt, but you can use any UNIX kernel with the GNU tools (Gnome, and such) and almost any packaging system (RPMs, debs, tarballs, etc).  You would of course get tons of conflicts as your system would be patchwork at best, but it is possible.  That being said most of the BSD distros are doing all they can to integrate Linux programs onto their system.  I wouldn't be supprised that in the future you see companies like Debian having a LiveCD that lets you choose your kernel as part of the install process.

---

### Post by techmarks on 2008-06-03
With FreeBSD you use the Ports Collection to install or remove the programmes.

It's quite easy for the most part.
You can install binary packages which install quite fast or you 
can build from source which is not hard, but can take a long time.

The Ports Collection makes it simple to build from source because 
the make files and dependencies are preconfigured for you.

Switch to the right directory and then issue the command;

# make install clean

then just wait.

Most of the Linux software can be used on FreeBSD.

Linux is an easier install no doubt, with FreeBSD you have to be willing to configure files to get the system just right.

I'm using Xfce for the desktop, and can say that FreeBSD works very nicely for a desktop system.  Again you just have to work a little harder to get everything just right, but not much.

---

### Post by Hevoos on 2008-06-04
When flash begins working, mozilla won't crash every now and then and it detects my DVD drive it may become a Linux killer for me. 
I haven't tried it as a server yet, but I think it is better on some server specific tasks.

Linux just has so many more apps and hardware support it's not very likely for it to become a linux killer,
 especially now when even Linux is not so popular (with the majority of people that is).

---

