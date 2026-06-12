---
title: "First Experience With Linux (Ubuntu): What do i think."
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by kwanbis on 2006-01-20
Hi,

first of all, i would like to say that i'm not a Microsoft fanboy, in fact i generalilly dislike it, and i love the open source movement in general, and Linux in particular (or GNU/Linux as others like to call it). I'm also a linux newbie, so maybe many of the things i would say could sound nonsence to more advanced users, or even plain wrong. 

I have used DOS, Windows (since 3.0), OS/2. I also had used a lot of non PC computers: Ti-994/a, Commodore 128, and Amiga 500.

I started trying Linux in the past, testing redhat, suse, mandrake, redmond linux, linspire, gentoo, etc., but i was never too ready to switch, or too impressed.

Last weekend my ThinkPad hd broke, o i had to reinstall, and tried Ubuntu's DVD, that i had downloaded before.

I must say that i was pretty impressed at first, that it detected all of my hardware, and installed a pretty good selection of hardware. I even went to synaptic, and updated the system. All good. 

Problem started when i wanted to do things not allready pre-done by the ubuntu/debian community.

I wanted to install Firefox 1.5, and found out i have to do a lot of steps (detailed on the wiki), that i could understand, and do, but where very unnatural.

I then wanted to install java 1.5, and again, had to do a lot of steps just to install it.

Never mind the things i had to do to install an ati driver, and many other things.

As i said, i have used computers a lot before, so i can do most of the things, but i get the feeling that any normal user would be oberhelmed with such dificult taks.

Why can't i just download a firefox installer and run it? why can't i just download a java installer and run it? why can't i just download an ati driver and do a simple installation? why is so dificult to do normal things?

Its so easy to install something in windows, and even easier in OSX, that i wonder what is the problem with Linux.

I have since then re-installed Windows 2000 on my thinkpad, but i also installed VMWare, so i can continue testing Linux.

I think it is incredible what has been done so far, almost for free, the freedom linux gives, the stability, performance, and choice, but i still wonder why these things keep happening, and why aren't fixed.

I'm still convinced that my next pc would be a mac, as i think OSX has the best of both worlds, but i hoppe one day linux would solve this issues.

---

### Post by earobinson on 2006-01-20
> Why can't i just download a firefox installer and run it? why can't i just download a java installer and run it? why can't i just download an ati driver and do a simple installation? why can'why is so dificult to do normal things?
The answer to this question is because an installer has not been made yet. In windows when you dl the firefox installer that has been compiled, and made. But no one made a installer for firefox so it is hard. If some one had made an installer then you could just dl the program and do a sudo dpkg -i firefox_installer_name.deb and just that one line would install everything.

So the answer is that there is more support for windows and os/x and therefor porgrams get compiled faster.

Hope this answers your question.

NOTE 01: you can install firefox 1.5 buy using the backports.
NOTE 02: this is not a ubuntu support issue so it should not be in the support section instead it should be in the community chat, I have msged the mods to have It moved.

---

### Post by jon_z on 2006-01-20
Firefox and the plugins can be easily installed via automatix:

[GNOME]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix")
[KDE]("http://ubuntuforums.org/showthread.php?t=105343")

If you have an ATI video card, mlomker has made an excelent guide [here]("http://ubuntuforums.org/showthread.php?p=408111")

With the video card, even with windows, you still have to install drivers to get full potential use of the card, the windows drivers just provide enough to get the screen resolution up a little bit, just like this.. Installing the ATI drivers will unlock *ALMOST* full potential of your video card. Based on my ATI Radeon 9600XT, I have almost 95% functionality.  Think of switching to linux like learning how to drive an automobile...You didn't learn how to do it in 1 day, thats for sure.. things have to be learned in stride.. And the only way to learn is to expierence..  When people started with windows, it was foriegn to them...Its like some sports, one example I can provide from expierence is throwing javelin, I learned one technique from my first coach...I now have a much higher level coach and things seem foriegn to me..It is still throwing a spear just as you are still using a computer, things are different but _can_ be learned.  hope this is a help.  Don't think of it as more difficult, think of it as you have more control over what goes on.  With Windows, you choose the directory thats about it of where a program is installed, in *Nix, you have MUCH more flexibility of what you can do with programs.

---

### Post by Jolva on 2006-01-20
Correct me if I'm wrong (and I'm only guessing) but aren't there a lack of "installers" because there's so many different flavors of Linux Distributions? Creating an executable program for Windows XP is one thing, but creating a one click installer that works on hundreds of slightly different operating systems must be much more tricky right?

BTW, I installed Fireworks effortlessly using Synaptic package manager. ;)

---

### Post by jon_z on 2006-01-20
the different version of linux's are not identical by any means...They are _different_ operating systems...  There are not a lot of different versions of windows because Microsoft has a monopoly of the market..and I think Bill would kill people if someone made a free version of windows (although piracy is the same thing as free windows isnt it?:P)  It hurts me to say this, but you cant install mac programs on windows machines even though they are "similar"  same thing holds true with linux..  Although We are Ubuntu linux and there is Redhad Linux and Debian Linux, and Gentoo linux.. we are all different, and have different goals..  With a little reading and a bit of willpower, almost any program can be installed on any flavor of nix, it may require compling, but because we are different architectures(sp.) we dont have the ability for a global 1 click installer.

---

### Post by earobinson on 2006-01-20
[QUOTE=Jolva]Correct me if I'm wrong (and I'm only guessing) but aren't there a lack of "installers" because there's so many different flavors of Linux Distributions?[/QUOTE]

Yes and no, there are many projects that are trying to solve this problem, [autopackage]("http://autopackage.org/") is the biggest one I know of. also there is a command (alian) that will convert rpm installers to deb installers that ubunut can use.

A lot of things cause this problem, but linux is about choice and saying we should scrap all the distros (I know your not saying this) is not the answer, making it easyer for us to use eachothers work is a very noble quest and one that a lot of people spend a lot of time on.

But even if we where all working on the same version of linux we would still have the problem that we have a very small share of the market so people just wont make linux installers.

---

### Post by fuscia on 2006-01-20
as a 'normal user', i found i had to learn about windows as well as having to learn about linux. the difference was that linux users were more than willing to help me. 

> I wanted to install Firefox 1.5, and found out i have to do a lot of steps (detailed on the wiki), that i could understand, and do, but where very unnatural.

you're confusing 'natural' and 'habitual'. just because something's a habit doesn't make it natural. take toilet training, for example: it's far more natural to fill your pants.

---

### Post by jon_z on 2006-01-20
the Automatix installation, which I have added to my signature, provides a extremly easy installation of pretty much everything you need to surf the web and download things with..

---

### Post by kwanbis on 2006-01-20
thanks for all the replies. I would read them all and post a reply. Thanks.

---

### Post by kwanbis on 2006-01-20
*NOTE 01: you can install firefox 1.5 buy using the backports.*

what are the backports? a diferent repositorie? by the way, why is that all the usefull repositoires are not enabled by default?

[I]The answer to this question is because an installer has not been made yet. In windows when you dl the firefox installer that has been compiled, and made. But no one made a installer for firefox so it is hard. If some one had made an installer then you could just dl the program and do a sudo dpkg -i firefox_installer_name.deb and just that one line would install everything.

Correct me if I'm wrong (and I'm only guessing) but aren't there a lack of "installers" because there's so many different flavors of Linux Distributions? Creating an executable program for Windows XP is one thing, but creating a one click installer that works on hundreds of slightly different operating systems must be much more tricky right?[/I]

thats what i thought myself. i understand that linux is about "choice", but why can't we at least concur on a distribution method?

*the different version of linux's are not identical by any means...They are different operating systems... There are not a lot of different versions of windows because Microsoft has a monopoly of the market..and I think Bill would kill people if someone made a free version of windows.*

how much different thatn Windows NT is to Windows 95, or XP to 2000? I mean, at least on the same hardware.

*Yes and no, there are many projects that are trying to solve this problem, autopackage is the biggest one I know of. also there is a command (alian) that will convert rpm installers to deb installers that ubunut can use.*

does alien works ok? should i donwload RPMs and convert them if no deb exists?

[I]A lot of things cause this problem, but linux is about choice and saying we should scrap all the distros (I know your not saying this) is not the answer, making it easyer for us to use eachothers work is a very noble quest and one that a lot of people spend a lot of time on.

But even if we where all working on the same version of linux we would still have the problem that we have a very small share of the market so people just wont make linux installers.[/I]

i think is a chicken+egg problem. we have little sahre, cause its dificult, so we don't get more share. i also think that many distributions already hurt it. there are 365 on distrowatch listed. by the way, i thought apple had less share than linux.

*you're confusing 'natural' and 'habitual'. just because something's a habit doesn't make it natural. take toilet training, for example: it's far more natural to fill your pants.*

double clicking an EXE (or a DEB), and just pressing next and making choices sounds much more natural than the install i had to follow to install ff 1.5. (i have seen the trick of assosiating a deb so it would launch on double click, but, why isn't defaulted?)

*the Automatix installation, which I have added to my signature, provides a extremly easy installation of pretty much everything you need to surf the web and download things with..*

cool, i would look for it. i had tried easyubuntu.

*If you have an ATI video card, mlomker has made an excelent guide here*

again, i did it, and installed it. but is much more dificult than a windows driver install. we can probably blame ati for it.

another thing, i tried to install vmware on ubuntu, again, pages of instructions. in windows, next, next, netxt, reboot.

again, I DON'T LIKE WINDOWS, in fact, i hatte it. but i would love to see linux take over it (or have at leas 20% of the market).

*as a 'normal user', i found i had to learn about windows as well as having to learn about linux. the difference was that linux users were more than willing to help me.*

thats the coolest part :)

---

### Post by Burning Bronx on 2006-01-20
[quote=kwanbis]what are the backports? a diferent repositorie? by the way, why is that all the usefull repositoires are not enabled by default?[/quote]
Backports is a repository for new upstream versions of different applications. You can request apps at the Backports section of the forum.

[quote=kwanbis]
how much different thatn Windows NT is to Windows 95, or XP to 2000? I mean, at least on the same hardware.[/quote]
The difference between different flavours of linux kernels could vary from "almost missing" to "huge abbyss". 

[quote=kwanbis]does alien works ok? should i donwload RPMs and convert them if no deb exists?[/quote]
You can use RPMs through alien or DEBs from debian's repos but since they are different distros compatibility can't be guaranteed. For software not in the repositories it's best to build from source. It's not that hard to learn (if you come from Windows then you'll find you have to "learn").

[quote=kwanbis]the Automatix installation, which I have added to my signature, provides a extremly easy installation of pretty much everything you need to surf the web and download things with..

cool, i would look for it. i had tried easyubuntu.[/quote]
Such scripts are the easiest way to screw your Ubuntu installation. They could work and they could trash your PC. Throw the dice.

[quote=kwanbis]again, i did it, and installed it. but is much more dificult than a windows driver install. we can probably blame ati for it.[/quote]
Blame ATI and the rest of the manufacturers that don't release their drivers open source.

[quote=kwanbis]
another thing, i tried to install vmware on ubuntu, again, pages of instructions. in windows, next, next, netxt, reboot.[/quote]
That's the reason a windows system is so easy to break. Cause it's all "next, next, next". And that's the reason Linux is so educational. Cause you have to read and learn some things.

Really. Spend some more time reading and learning. Each thing you learn how to do and reproduce later will come in handy sooner or later. 
Also don't think Linux is all about getting a bigger market share and killing windows. Linux is about freedom therefore leaving you many options on how to do things. Big market share is good but functionality and freedom is better.

---

### Post by aysiu on 2006-01-20
[QUOTE=kwanbis]
Why can't i just download a firefox installer and run it? why can't i just download a java installer and run it? why can't i just download an ati driver and do a simple installation? why is so dificult to do normal things?[/QUOTE] These aren't *normal* things. These are Windows power users things. No "normal" computer users I know install ATI drivers (or even know what ATI drivers are) or install Firefox 1.5.

All the "normal" users I installed Firefox for (because they couldn't install it themselves) are still using the same version I installed for them, be it 0.9 or 1.0.3.

There are basically three types of Linux users:
1. Low skills, low needs.
2. High skills, high needs.
3. Medium skills, high needs.

Unfortunately, most ex-Windows users who migrate to Linux *think* they're "normal" users (category #1), but they're really not (they're category #3).

Linux in general (and Ubuntu specifically) are really ideal for categories #1 and #2, not #3. If you're #3, you've either got to suck it up and spruce up your skills or just dumb down your needs.

---

### Post by matthewstory on 2006-01-20
I hate to recommend another distro on the ubuntu site, but if you like the OS X installation so much you might want to try gobo linux: [www.gobolinux.org](www.gobolinux.org).  It's a linux distribution whose entire purpose is to replicate the ease of the OS X type installation.  All of the program's files are stored in an application folder, and the installation is as easy as downloading the program image, mounting it and dragging the icon to the application folder . . . in theory.  In practice they're not quite there yet, but it's something to look foreward to.  

regards,
matt

---

### Post by kwanbis on 2006-01-20
[QUOTE=Burning Bronx]The difference between different flavours of linux kernels could vary from "almost missing" to "huge abbyss".[/QUOTE]
i can't think why more different than XP SP1 and SP2.

[QUOTE=Burning Bronx]You can use RPMs through alien or DEBs from debian's repos but since they are different distros compatibility can't be guaranteed. For software not in the repositories it's best to build from source. It's not that hard to learn (if you come from Windows then you'll find you have to "learn").[/QUOTE]
i know i will.

[QUOTE=Burning Bronx]Blame ATI and the rest of the manufacturers that don't release their drivers open source.[/QUOTE]
i don't agree on this. Windows drivers arent open source.

[QUOTE=Burning Bronx]That's the reason a windows system is so easy to break. Cause it's all "next, next, next". And that's the reason Linux is so educational. Cause you have to read and learn some things.[/QUOTE]
i agree the educational part. don't agree with the "easy to break" part. we have OSX again to prove the contrary.

[QUOTE=Burning Bronx]Also don't think Linux is all about getting a bigger market share and killing windows. Linux is about freedom therefore leaving you many options on how to do things. Big market share is good but functionality and freedom is better.[/QUOTE]
market share is good, cause it gives more freedom, more support from manufacturers, a better experienco for all of us.

by the way, i would do a LFS installation try. To try learn more and faster. I would then probably return to ubuntu ;)

---

### Post by Burning Bronx on 2006-01-20
Good luck then. I haven't tried LFS but from what I have read it's a good experience. Thought if you get used to it you may want to go for Gentoo later.

---

### Post by el3ktro on 2006-01-29
[QUOTE=kwanbis]i don't agree on this. Windows drivers arent open source.[/QUOTE]

Yes but Linux is an open source world, and closed source apps/drivers just don't "fit in". The same goes for Skype on my system, which I have to use because some of my friends refuse to use something more open, something that doesnt force you to use this one particular application.

Well all this a matter of taste. If you don't like the "Linux way" then go back, but if you're willing to change some of your habits you'll soon see all the advantages of it. There are so many threads here where people who have installed Linux for the first time ask why nothing happens when they click on the program file they've just downloaded from some site. This is not how Linux works! In Linux (and on Ubuntu in particular) software is managed in packages, thrown together into repositories. It's a breeze to install software from this repository, it's much easier than to do in Windows actually. But this repository thing also means that you have to wait for the Ubuntu people to add new software to this repository - and the newest Firefox just hasn't been added yet, there's only 1.0.7. I switched from Gentoo to Ubuntu, and I first had to get used to that you sometimes have to wait longer until a new version pops in, but now I got use to it and am happy that others do this for me and that I can rely on a stable system and apt-get.

Tom

---

