---
title: "OpenBSD for a laptopp?"
date: 2007-09-17
forum: BSD
---

### Post by Beau D. on 2007-09-17
So I have been longingly looking at my OpenBSD 4.1 install cd for the past couple of days. Wondering if I could get it up and running on my current main machine. (Dell D610, 1.8 ghz Pentium M, 1 gig of RAM, Intel Pro 2200 series wireless) My biggest question is what do you guys who are running BSD on the desktop have for hits, helps, pointers etc. I have been over the MAN pages, the handbooks..and purportedly my machine should work. Just wondering if others are using OpenBSD for a desktop OS..and if so how has your experience been?

Beau D.

---

### Post by Bachstelze on 2007-09-17
[http://cvs.openbsd.org/faq/faq1.html#Desktop](http://cvs.openbsd.org/faq/faq1.html#Desktop)

I'm currently writing a guide about OpenBSD on the desktop : [http://fkraiem.no-ip.org/wiki/OpenBSD_Desktop_HowTo](http://fkraiem.no-ip.org/wiki/OpenBSD_Desktop_HowTo) - though it's still far from finished. For pointers, the [FAQ](http://cvs.openbsd.org/faq/) is a nice source of information, or you can use the allmighty Google ;)

Also, if you have more precise questions, feel free to ask.

---

### Post by Beau D. on 2007-09-18
I have read your wiki..I even have it bookmarked. My biggest concern is getting my wireless up and running. I have an Intel IPW2200 chipset. I know the driver is in there. But no firmware from what I understand. Meaning I would have to load it in after. Plenty of FAQ's and such for doing that in linux. Though I have never had to as Ubuntu see's it..and just loads all I need. So did Fedora, and all the other distros I used. So I guess I have no clue to where to look for help with that. I realize it will be done via CLI..that doesn't bother me one bit. After that I would like a nice app for roaming with the wireless. I move around alot during the day, and never know what network I might hook up to. 

 I am also leaning towards Fluxbox for a DE..not for the lack of hardware, Just something light, but efficent. Any ideas? No need for Compiz or any of that stuff...I don't even use it now..nor do I forsee me using it down the road. And just so you know..I am not a fan of KDE. So we can cross that one out..lol.

Beau D.

---

### Post by mips on 2007-09-19
> **Beau D. said:**
> I have read your wiki..I even have it bookmarked. My biggest concern is getting my wireless up and running. I have an Intel IPW2200 chipset. I know the driver is in there. But no firmware from what I understand. Meaning I would have to load it in after. 

 I am also leaning towards Fluxbox for a DE..not for the lack of hardware, Just something light, but efficent. Any ideas? No need for Compiz or any of that stuff...I don't even use it now..nor do I forsee me using it down the road. And just so you know..I am not a fan of KDE. So we can cross that one out..lol.

Beau D.

The BSD documentation is good, see:

[http://www.openbsd.org/cgi-bin/man.cgi?query=iwi&arch=i386&sektion=4](http://www.openbsd.org/cgi-bin/man.cgi?query=iwi&arch=i386&sektion=4)
[http://damien.bergamini.free.fr/](http://damien.bergamini.free.fr/)
[http://damien.bergamini.free.fr/packages/openbsd/http://damien.bergamini.free.fr/packages/openbsd/iwi-firmware-3.0.tgz](http://damien.bergamini.free.fr/packages/openbsd/http://damien.bergamini.free.fr/packages/openbsd/iwi-firmware-3.0.tgz)  can be added with pkg_add

Fluxbox is cool, I always install that with OBSD and it flies, even on old hardware. You also have option like e16, gnome, kde, xfce, fvwm etc

I just found this, [http://www.swax.de/content/system/login-manager.shtml](http://www.swax.de/content/system/login-manager.shtml)

It's early here and I think you gave me a bug, gonna install OBSD on my laptop again today ;)

---

### Post by ChillMonkey on 2007-09-19
while i'm not sure about your specific laptop, i ran openbsd on one of my past laptops for several years. everything about it was great. i actually preffer the kernel config process on bsd to linux, but that's just me. just keep userland and the kernel in sync and everything will be great.

---

### Post by mips on 2007-09-19
I just posted a howto on creating a bootable OBSD install cd, [http://ubuntuforums.org/showthread.php?t=554486](http://ubuntuforums.org/showthread.php?t=554486)

Net install is not always an option and it is handy to have the cd.

---

### Post by Beau D. on 2007-09-22
Okay so I am going to go for it. Problems and all. I tried to install the package I found but no joy. So it looks like I need to find a different one to download for my firmware. That said..how should I partition my hard drive? I see all the tutorials/FAQ's were written some time ago. I'd just as soon Use my entire 60gig HDD..andy ideas how big I should make each part? A general guide? And where should I look to find out how to install and setup a GUI? I plan to add gnome as my DE. I know pkg add will get all I need..my question is what do I have to do after I add the package to get it up and running with GDM and such? Google hasn't been my friend with this so far. 

Beau D.

---

### Post by Bachstelze on 2007-09-23
> **Beau D. said:**
> I tried to install the package I found but no joy. So it looks like I need to find a different one to download for my firmware.

Which firmware ? Some weireless stuff ? The man page of your drive should have the URL to download the firmware.

> **Beau D. said:**
> That said..how should I partition my hard drive? I see all the tutorials/FAQ's were written some time ago. I'd just as soon Use my entire 60gig HDD..andy ideas how big I should make each part? A general guide?

[http://fkraiem.no-ip.org/wiki/OpenBSD_Desktop_HowTo#The_disklabel_2](http://fkraiem.no-ip.org/wiki/OpenBSD_Desktop_HowTo#The_disklabel_2)

Of course, since you seem to have a 60 G drive, you can give yourself a couple gigs more for /usr and a bigger /home. Also, remember to leave a couple gigs free, just in case.

> **Beau D. said:**
> And where should I look to find out how to install and setup a GUI? I plan to add gnome as my DE. I know pkg add will get all I need..my question is what do I have to do after I add the package to get it up and running with GDM and such? Google hasn't been my friend with this so far. 

Can't help you with Gnome, sorry...

---

### Post by Beau D. on 2007-09-23
Well the package I wa referring to was the ipw-2200 firmware for my wireless. I seem to have found the openBSD one now, and downloaded it to a USB thumbdrive. Once I get it installed and running..I'l be able to install the ports tree..and then start adding packages. Seems to be the reccomendation of OpenBSD to add packages when available rather than add from ports. As a side note, I installed PCBSD 1.4 RC for a short bit. While it installs great, found my wireless et al. It seemed to be very cobbled together. The PBI system seems to be the over riding design feature. Seems like a rather novel package system..but has VERY limited software. And some of it didn't seem to even install. Not sure if this is a PBI problem, or the OS itself being beta. 

Beau D.

---

### Post by Bachstelze on 2007-09-23
> **Beau D. said:**
> Well the package I wa referring to was the ipw-2200 firmware for my wireless. I seem to have found the openBSD one now, and downloaded it to a USB thumbdrive. Once I get it installed and running..I'l be able to install the ports tree..and then start adding packages.

You don't need to have the ports tree to install packages. Just configure the PKG_PATH environment variable :

```
export PKG_PATH=ftp://ftp.openbsd.org/pub/OpenBSD/4.1/packages/`machine -a`/
```

And then do

```
sudo pkg_add -vi package
```

it will automagically fetch and install it from the FTP mirror you provided, as well as all the dependencies.

---

### Post by Beau D. on 2007-09-23
Thanks for the heads up.  I thought I read in the FAQ that people usually install the ports tree, then use that to find packages..and if a package isn't available you already have the ports tree up and running so you can then just build it from ports. I'll likely try both ways..and see what I prefer. 

 Well..off to wipe out my HDD.

 Wish me luck..lol


Beau D.

---

### Post by iggdawg on 2007-09-29
One nice thing on openbsd that the other BSDs don't have is the "afterboot" manpage.  It's just what it sounds like.  Install the OS and get to your first command prompt, then type "man afterboot" before you do anything else at all. OpenBSD does things a little differently than the other BSDs so it's good to look over this file.

---

### Post by Wiebelhaus on 2007-09-29
**Random comment of the day**

BSD is cool as hell , looks very polished , I run PCLOS & Ubuntu on my linux box , for fun I tried BSD , Used it for 30 minutes had Multimedia , Browser , IM normal stuff running , Hard_freaking_freeze out of no where , Hasn't happened in PCLOS or Ubuntu , so I removed it.

---

### Post by Beau D. on 2007-09-30
Well I will be honest. OpenBSD has been beating me down on this machine. Install is no problem..heck I can get that down to about 5min even adding a new user. Sadly the reason I am so adept at it is my utter lack of skill and knowledge gettig my wireless up and running, therefore negating me getting anything else on the system. The man pages are all fine and good..but so outdated it's basicly useless for most stuff that I am looking to do(just look at all the man pages about partition sizes..most of them are for a 10-20GB hard drive when was the last time a computer shipped with a drive that samll?). I do find that the BSD stereotypical behavior kind of a putoff. Don't bother asking for help really..most running openBSD are wrapped up in server end things and have no tolerance for "simple" questions. Which is fine..I get it..but why so rude? What defines a simple question isn't really put out there. Your on your own to figure that out and incur their wrath. Seem google is the only fairly regular answer you will get other than look at the outdated manpages that discuss apps and procedures you won't need. I wouldnt mind so much if they had a community like this..where almost any question you have can be found in a search, and likely with a step by step fix.

 My problems are to numerous to list here..but I sure wish I could do it. It is pretty quick, and we all know the security issue. Maybe someone will put a howto for dummies up so a complete noob like me can get things up and running smoothly. 

My main problems.

 Mounting my USB stick with the intel firmware on it to enable my wireless.
 Mounting my CD drive.
 A decent FAQ or guide for the package system
 A decent rundown of packages needed for different WM's

 I am still plugging away though. Not giving up just yet.

Beau D.

---

### Post by Bachstelze on 2007-09-30
> **Beau D. said:**
> 
 Mounting my USB stick with the intel firmware on it to enable my wireless.

> **Beau D. said:**
> Mounting my CD drive

The mounting of anyhing is just the same as in Linux : 

```
sudo mount -t /dev/something /somewhere
```

For USB sticks, see [here](http://cvs.openbsd.org/faq/faq14.html#flashmem). For CD-ROM drives, it's usually /dev/cd0c.

> **Beau D. said:**
> A decent FAQ or gide for the package system

[http://cvs.openbsd.org/faq/faq15.html](http://cvs.openbsd.org/faq/faq15.html)

> **Beau D. said:**
> A decent rundown of packages needed for different WM's

For KDE, *kdebase*, for Fluxbox, *fluxbox*. Don't know about the others.

---

### Post by Harpalus on 2007-10-02
I'm not sure what you mean about outdated man pages. I've found OpenBSD man pages and documentation to consistently rank much higher then anything else I've seen, overall. My fanatic Gentoo friend now uses their man pages often, because he finds the quality higher.

The wireless configuration takes a bit of getting used to. It is one of the complaints I have with OpenBSD. However, the current method isn't incredibly difficult. man ifconfig. It's just a tad annoying. Nothing show-stopping.

The supposed "hostility" of the OpenBSD community doesn't really exist. Just keep in mind that you're NOT in Linux land anymore. I don't particularly care whether you use OpenBSD or not. I really don't, and I don't understand the need of many Linux people to advocate Linux wherever possible. (Or worse yet, their favourite distro!) That's why, for the most part, they'll help you out -- but only if you ask decent questions. They're not interested in convincing you to stay.

Myself, I've been happily using it as a desktop for quite some time now.

[http://ports.openbsd.nu/x11](http://ports.openbsd.nu/x11)

Try that link for window managers. The previously mentioned FAQ is excellent and is exactly what you wanted.

Many new BSD users get tripped up by /dev, in my experience. IE,  my connection is /dev/dc0, rather then /dev/eth0. Same for the CDROM, it's labelled differently. I prefer it now, but I tripped up on that too when I was first trying to mount things.

---

### Post by Beau D. on 2007-10-02
To be honest..I don't mind the community so much. They are just rude, and overbearing on people. I can deal with that easy enough..I just ask my BSD questions here..and am given far more help..in a non rude constructive way. I do find it a bit funny that I have gotten better help here on the Ubuntu forums than on say BSDforums. Its even more ironic that the only comprehensible desktop howto I could find is being written by a member here at the ubuntu forums. Aimed at helping the newby get his machine running, and then get into BSD.  As for the man pages. I'll be honest. My biggest sticking point is my wireless driver. I can likely live without 3d accelration, or a decent powermanagement system. But without my sole connection to the net..i'm dead in the water. The only explanation about my wireless card (intel iw2200) is that the firmware isn't "free". Great. A link to the firmware..yet no explanation of how to use it or install it other than package add. No word on how to configure it or if I even need to do any of that. And as for the man pages being outdated..well like I said It starts basically at page 1. Look at the suggested sizes for partitions, personally I just tripled the sizes based on the 20GB size in the page. Is that the right way though? I certainley don't know..and when you ask you get pointed to the same page you already read..with the same size hard drive from 2001.

 As a side note. Your right openBSD isn't linux. I get that. Your comments worded like this "I don't particularly care whether you use OpenBSD or not. I really don't, and I don't understand the need of many Linux people to advocate Linux wherever possible. (Or worse yet, their favourite distro!) That's why, for the most part, they'll help you out -- but only if you ask decent questions. They're not interested in convincing you to stay." though seem a bit..prickly. Now..I am personally not offended by them. I get what your saying..and don't take it personally.  I'm not going to get into what I said or didn't say. I haven't now or will attempt to advocate Linux to anyone who doesn't ask my opinion. Let alone on a BSD board. I have more or less sworn off BSD boards though..the air of elitism, and simple fear of being flamed is enough to keep me off. And while I understand you..nor anyone else cares if someone uses BSD in any form, you can be assured less and less people will use it when the introduction is so harsh. And while that may be fine and well..you never know who you are turning off. Maybe a great dev could of been had down the road, or someone willing to beta test the craziest things, or maybe just someone who would spread the word and bring someone like those two into the community.. Seems to me it shouldn't be to much for a advanced user to tackle this..make a safe place for a newbie to come learn, find some wiki stuff on how to do the basics. Like when I try to mount my USB stick it tells me I need to edit Fstab..all fine and good. I vim into it and attempt to add..but I can't. Oh well...back to the books I guess.

 And maybe I'm just not advanced enough to do this right now. But I am trying to learn. It just isn't very easy..and I'd rather learn with a running machine than trying to put all this down on paper, and hope I can get something working after I have no connection to the net. But that is what I have been doing. working on it as best I can, and then redoing it again..then popping in a LiveCD to get back to finding info.



Beau D.

---

### Post by Harpalus on 2007-10-02
I know how you feel. Back in high school I switched cold turkey from Windows to Slackware command line. (Luckily I used to be a DOS guy...) Was hell, I know what you mean about the learning curve. :) In the end it's worth it, at least for me -- and once you get used to it, OpenBSD is much easier to administer then, say, Fedora Core or Ubuntu.

I didn't mean to sound elitist or condescending - I was just trying to explain why many BSD users don't feel the need to go out of their way to help newbies. Sorry it seemed that way.

And I've never been to BSD forums, actually, I use the openbsd-misc mailing list. Provided you provide a dmesg, relevant information, and have read the man page/faq, they'll be willing to help you out. And if they're not, they'll just ignore you, but honestly, that's rare. Can't speak for the BSD forums, but my experiences on the OpenBSD-misc mailing list have been positive.

The partition sizes shouldn't be taken as indicators of the quality of the man pages, trust me. :) It's just that many use old computers for OpenBSD servers, and it's more convenient to aim lower. The sizes recommended there are more then fine for the average desktop user. Use their example partitions, and dump all your remaining free space into /home. If you like, add more to each partition. Example: An extra 50mb or 100mb for /, /var, etc. An extra 2g for /usr, and then the rest of the free space into /home. It's up to you, but the 20gb example is fine for desktop use, the rest of your space may as well go where you'll use it most, /home.

As for your wireless card: man the driver for it. I'm not sure offhand which driver iw2200 goes to, and Google isn't turning up anything. The man page will link to the firmware if it's supported. Install the firmware, then it's just a matter of setting up wireless. The following link might help, it's example files:

[http://www.weirdnet.nl/openbsd/wireless/](http://www.weirdnet.nl/openbsd/wireless/)

Again, man ifconfig will give you more information on configuration. I'll see if I can dig up my Zaurus, and post my own config files.

Oh, and try the OpenBSD mailing lists. Personally, I've had good experiences there.

EDIT: Relevant files. DHCP, on a WEP network. OpenBSD doesn't support WPA: horrendous protocol, lack of interest among developers.

/etc/hostname.wi0 (replace wi0 as applicable. For non WEP networks, ignore nwkey)

dhcp NONE NONE NONE nwkey 0x<hex key>         (WEP key, remember to prefix 0x)
nwid <name>                                           (eg, Linksys)

/etc/mygate

192.168.1.1     (Gateway, self explanatory)

/etc/myname

borzoi      (computer name, self explanatory)

/etc/dhcp.interfaces

# Commented stuff included by default
.
.
.

wi0

I don't remember touching anything else. You may need to edit /etc/dhcp.conf, I didn't need to. Hope this helped. When you want to switch networks, you'll need to either edit /etc/hostname.wi0 and bring wi0 down and up again, or type in the relevant ifconfig command. There's no convenient iwconfig, hopefully that changes soon.

---

### Post by mips on 2007-10-03
> **Beau D. said:**
> To be honest..I don't mind the community so much. They are just rude, and overbearing on people. I can deal with that easy enough..I just ask my BSD questions here..and am given far more help..in a non rude constructive way.


Beau D.

I have not really had issues with the community. You are expected to read the documentation and try things for yourself first, RTFM ;) Once you have read the docs & tried things ask your question in IRC or wherever, you will be helped. Only once did I get a snotty reply on irc but the rest of the people told me to ignore the person as he is known to be like that.

---

### Post by Th3Professor on 2008-04-17
A native of Slackware, I was a fan of the "K.I.S.S." simplicity motto early on, and when I added OpenBSD to my mix I fell in love.

Perhaps it's just a BSD thing in general, though I know from my experience specifically with OpenBSD that it is one of the most logical operating systems available. I never thought I'd find myself saying, "Unix is easier to learn than Linux"... (that is BSD vs Linux). Though I am still saying it, I believe it's easier than Linux.

The infrastructure, everything. Very logical. Easy. Simple.

I've got Solaris on a desktop, just so I can experience SysV, and it is certainly different, though it's still pretty solid.

I'm enjoying Ubuntu Studio now for the pre-configured aspects and the pre-packaged, uhm, packages (mostly audio apps). Though, I still have OpenBSD and it's great.

I ignore the rude remarks that some of the users throw out there, like in their email lists, especially from the creator.

OpenBSD works great as a laptop system. If I need to go all-out with apps that are best-suited for Linux, then I use Linux.

Although BSD can do the whole Linux emulation thing, it's not an optimal approach, so in those cases I just boot into Linux. Otherwise, putting obvious security advantages aside, there's no going wrong with the *stability* of OpenBSD. (I have never had any problems with it. Very impressive.)

---

### Post by PmDematagoda on 2008-04-17
This thread is more than three months old and I really don't see the point in continuing this thread any longer. If you want to give out your views on OpenBSD then you can do so in a new thread.

This thread is closed.

---

