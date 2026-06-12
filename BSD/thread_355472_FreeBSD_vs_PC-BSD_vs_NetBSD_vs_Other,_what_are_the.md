---
title: "FreeBSD vs PC-BSD vs NetBSD vs Other, what are the advantages of each?"
date: 2007-02-07
forum: BSD
---

### Post by Jamesbowden on 2007-02-07
I was thinking about install FreeBSD on my laptop. However before i do i would like to know if there are any advantages to PC-BSD, NetBSD or any other BSD varients. Or if there are any disadvantages to FreeBSD.

What are the major differences between the different forms and falvors of BSD.

thanks

---

### Post by mips on 2007-02-07
[http://ubuntuforums.org/showthread.php?t=330889](http://ubuntuforums.org/showthread.php?t=330889)
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php)

FreeBSD - Fast, stable & keeping up with time.
OpenBSD - Security is main focus
NetBSD- Aims to work on many different CPU architectures
DesktopBSD - FreeBSD + all the stuff that makes up easy installable desktop environment.
PCBSD- Same as above but has PBI package management.

Check what the latest version of DesktopBSD is  based on, should be 6.x I think and install that. It is FreeBSD in essensense with the extra stuff on top. Works just like freebsd so you can learn that just fine.

I don't care much for PCBSDs PBI package manager, use BSD via portage I would say.

Depending on your skill level you can install any of the above, some are just harder than orthers, meaning the non desktop ones.

---

### Post by runningwithscissors on 2007-02-07
There are only about four distinct BSDs at the moment. Free, Net, Open and DragonFly.
Other BSDs mostly have the Debian->Ubuntu relationship to the four above.

NetBSD ships with older versions of software compared to the others, however, you have newer versions with pkgsrc.
They are all pretty similar despite them trumpeting their security records or SMP technology or number of architectures they run on.
I'd say you'd be best off with FreeBSD. Ports is huge, you can get binary packages for some software as well, and ships with a good deal of stuff on the installation media, and a friendly installer.

---

### Post by mips on 2007-02-07
I would agree with the above sentiments. DesktopBSD is FreeBSD at the end of the day though.

---

### Post by Jamesbowden on 2007-02-07
So freeBSD or DesktopBSD? advantages or disadvantages to either? what are the differences (if any)?

thanks.

---

### Post by mips on 2007-02-07
> **Jamesbowden said:**
> So freeBSD or DesktopBSD? advantages or disadvantages to either? what are the differences (if any)?

thanks.

None, except the version of FreeBSD being used by DesktopBSD. The nice thing is you get a full FreeBSD install plus the desktop environment which is cool.

You could do either. But like I said said before check the version being used. If it is older then just install FreeBSD and add the DesktopBSD stuff via portage.

---

### Post by Jamesbowden on 2007-02-07
Thanks alot, this has been very helpful.

---

### Post by mephisto786 on 2007-03-30
Or give pc bsd a  spin and use ports and pkg_add instead of pbi packages.....the latest is bsed on freebsd 6.1 , with a .2 base expected on their summer pc bsd 1.4 release.....both the spinofffs provide a simple one disk desktop install with freebsd under the hood....

enjoy

---

### Post by zeusx64 on 2007-06-04
Stop! There were originally two BSDs. FreeBSD & I am unsure which of the other two (OpenBSD & NetBSD)came first but some members had disagreements and therefore we now have three. As for the dominant of the three, that is & always will be FreeBSD. I have used most everything worth using. I only hang on to a very slim few Linux distros and really am only very fond of FreeBSD itself.
I am a member of the forum over at PCBSD but do not actually use still. There are two easy to install variants of FreeBSD; PCBSD & DesktopBSD. The only two things that seperate PCBSD from it's mother, FreeBSD, is that it has been made to install a desktop automatically & the PBI (PCBSD installer).
Kris Moore is very good at what he does but after figuring out the FreeBSD installation, fetching the ports directory over the web, and configuring the environment installation, Xorg, TTYs, and a few other things, I fell in love with the method. Once you have your desktop installed and configured, you will really feel accomplished, as this usually takes a couple to a few days to complete and most all of it is with nothing but a black screen and white text, so get used to the CLI way of doing things.
Anyway, PCBSD & DesktopBSD are just FreeBSD preconfigured for you. They may as well call it lazy BSD. LOL

Do your self a big favor & get FreeBSD on disk, run the install yourself, and take it from there. Be aware, you need to read about it before hand, unless you already have. FreeBSD is great with Dlink DWL 510/520/ & 650 wireless cards & also with nVidia cards. Luckily, as of 6.2 FreeBSD automatically detects your Atheros based wifi cards. This is a fun install if you love this kind of stuff.
Here are a couple of links for various stuff that is simple to do. There may or may not be some outdated stuff by now, which means yes there is but just to maybe to see some of the stuff that I have done.

[http://forums.pcbsd.org/viewtopic.php?p=41159#41159](http://forums.pcbsd.org/viewtopic.php?p=41159#41159)
[http://forums.pcbsd.org/viewtopic.php?t=5750&highlight=](http://forums.pcbsd.org/viewtopic.php?t=5750&highlight=)
[http://forums.pcbsd.org/viewtopic.php?t=5218&highlight=](http://forums.pcbsd.org/viewtopic.php?t=5218&highlight=)
[http://forums.pcbsd.org/viewtopic.php?t=4296&highlight=](http://forums.pcbsd.org/viewtopic.php?t=4296&highlight=)

This one below is for the FreeBSD handbook. Just go to the server and find the pdf download/ book.pdf
[ftp://ftp.FreeBSD.org/pub/FreeBSD/doc/](ftp://ftp.FreeBSD.org/pub/FreeBSD/doc/)
You wanted to know what was good about FreeBSD ? It is closer to the real deal. FreeBSD is a varient of the original AT&T Unix, as it was licensed to **B**erkley **S**oftware **D**esign. Whats bad about it ? You have to do it by hand (CLI) but that is only bad if you are lazy. Good luck & Have fun. ;)

---

### Post by Jamesbowden on 2007-06-07
> **zeusx64 said:**
> Stop! There were originally two BSDs. FreeBSD & I am unsure which of the other two (OpenBSD & NetBSD)came first but some members had disagreements and therefore we now have three. As for the dominant of the three, that is & always will be FreeBSD. I have used most everything worth using. I only hang on to a very slim few Linux distros and really am only very fond of FreeBSD itself.
I am a member of the forum over at PCBSD but do not actually use still. There are two easy to install variants of FreeBSD; PCBSD & DesktopBSD. The only two things that seperate PCBSD from it's mother, FreeBSD, is that it has been made to install a desktop automatically & the PBI (PCBSD installer).
Kris Moore is very good at what he does but after figuring out the FreeBSD installation, fetching the ports directory over the web, and configuring the environment installation, Xorg, TTYs, and a few other things, I fell in love with the method. Once you have your desktop installed and configured, you will really feel accomplished, as this usually takes a couple to a few days to complete and most all of it is with nothing but a black screen and white text, so get used to the CLI way of doing things.
Anyway, PCBSD & DesktopBSD are just FreeBSD preconfigured for you. They may as well call it lazy BSD. LOL

Do your self a big favor & get FreeBSD on disk, run the install yourself, and take it from there. Be aware, you need to read about it before hand, unless you already have. FreeBSD is great with Dlink DWL 510/520/ & 650 wireless cards & also with nVidia cards. Luckily, as of 6.2 FreeBSD automatically detects your Atheros based wifi cards. This is a fun install if you love this kind of stuff.
Here are a couple of links for various stuff that is simple to do. There may or may not be some outdated stuff by now, which means yes there is but just to maybe to see some of the stuff that I have done.

[http://forums.pcbsd.org/viewtopic.php?p=41159#41159](http://forums.pcbsd.org/viewtopic.php?p=41159#41159)
[http://forums.pcbsd.org/viewtopic.php?t=5750&highlight=](http://forums.pcbsd.org/viewtopic.php?t=5750&highlight=)
[http://forums.pcbsd.org/viewtopic.php?t=5218&highlight=](http://forums.pcbsd.org/viewtopic.php?t=5218&highlight=)
[http://forums.pcbsd.org/viewtopic.php?t=4296&highlight=](http://forums.pcbsd.org/viewtopic.php?t=4296&highlight=)

This one below is for the FreeBSD handbook. Just go to the server and find the pdf download/ book.pdf
[ftp://ftp.FreeBSD.org/pub/FreeBSD/doc/](ftp://ftp.FreeBSD.org/pub/FreeBSD/doc/)
You wanted to know what was good about FreeBSD ? It is closer to the real deal. FreeBSD is a varient of the original AT&T Unix, as it was licensed to **B**erkley **S**oftware **D**esign. Whats bad about it ? You have to do it by hand (CLI) but that is only bad if you are lazy. Good luck & Have fun. ;)

TYVM!

---

### Post by Bachstelze on 2007-06-07
*sneaks in*

Just wanted to point out that the D of BSD stands for *Distribution*.

*leaves*

---

### Post by zeusx64 on 2007-06-07
LOL, my bad. Thanks for pointing that out. I am at least glad that I realize I am human. :D
For me, the accomplishment of installing and configuring FreeBSD is great, as I am ADHD all the way, so attention span is weak some times. Anyways, thanks for the correction. 
If you have not tried it already, DesktopBSD is at 1.6_RC2 and runs pretty damn good, plus they use a GUI for the ports system. The GUI may be a plus for some & may not for others of us whom like the CLI way. Anyhow, it is seemingly well put together & you can always reinstall something else if you do not like it. :shock:

---

### Post by A.I. BOT on 2007-06-07
I always wanted to try out BSD namely DesktopBSD. I have a few question, if you dont mind :) and sorry if they sound dumb :P.

If I'm correct, FreeBSD compiles it's ports?, Are their any binary packages (not talking about PCBSD's PBI's) or is it strictly compiling?

How up-to-date are the packages? Bleeding-Edge, Few Months old, or so on?

Thats basicly all I need to know before I try it out :P

Thanks.

---

### Post by zeusx64 on 2007-06-07
> **A.I. BOT said:**
> I always wanted to try out BSD namely DesktopBSD. I have a few question, if you dont mind :) and sorry if they sound dumb :P.
There are no dumb questions. DesktopBSD, if that is what you want to try, is now using the choice between a graphical click and run installation or you can boot to the live cd, check it out & then install from there. There is an icon on the desktop for the install. Remember that DesktopBSD & PCBSD are made to install with there own premade settings and such. They are nice & cool but for me, a straight FreeBSD is the way to go. Please check those two out but also try FreeBSD itself & read the handbook before hand. If you choose just to use DesktopBSD, that is your own choice. :grin:
> **A.I. BOT said:**
> If I'm correct, FreeBSD compiles it's ports?, Are their any binary packages (not talking about PCBSD's PBI's) or is it strictly compiling?
Yes all ports install by compiling for your system. That is the good thing about ports, they compile for "your system". Some times, ports may use a binary, which is usually downloaded prior to installation and copied to the /usr/ports/distfiles folder, via the cp command. Remember ports are a CLI type install, /usr/ports is a system location, & that any action in these directories require you to use su (super user) with the root password. Without it, you get an error message and can do nothing.
Also, there is another method to install, which is precompiled packages. This is the pkg_add method. The diff here is that you get older packages. The newest packages have not been precompiled yet. If you look back at my first post for this thread, you will find a link to the FreeBSD ftp site directory, where you can find the FreeBSD handbook and in it, all of the neccessary info for using pkg_add & ports & also doing cvsup, which grabs your system source for you. You will need to get sources for your kernel & such for the nVidia driver and things of that nature, as you do with Linux. 
> **A.I. BOT said:**
> How up-to-date are the packages? Bleeding-Edge, Few Months old, or so on?I think that you will find no real bleeding edge stuff unless using FreeBSD current. The FreeBSD released version or RELENG, is not bleeding edge like that. I think that FreeBSD likes its released versions to be very stable. You can however,  get into that current stuff if you want but "be aware", if you break something, you broke it at your own risk and in current, thing definately can & will break.
FreeBSD now sports xorg 7.2, which is why I push a straight up FreeBSD minimal install, with no xorg installed at first. This gives you the opportunity to install xorg 7.2 (After a portsnap, of course) from ports, without all of the upgrade bull s--t. This leaves no room for upgrade breaking and we know that with xorg 7.2, we get options for compiz & beryl.

I hope I have helped in any way at all. Have fun... :biggrin:

---

### Post by A.I. BOT on 2007-06-07
Yeah youve helped me a lot. I ended up trying it out and installing the RC of it on a seperate partition. It looks beautiful, very beautiful, runs fast and the installer and GUI package manager is super easy.

Unfortunately, when trying to update the system and install somethings, most of the ports couldent be found on any mirror for some reason. :(. Oh well. Its a very nice system though.

---

### Post by zeusx64 on 2007-06-08
FreeBSD straight is the way to go. You will learn lots in the process. Be adventurous...

---

