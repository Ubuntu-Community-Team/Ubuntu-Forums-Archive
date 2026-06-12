---
title: "How secure is Linux"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Chuck_Schuldiner on 2007-09-05
I have been playing with Ubuntu for a day or so. It looks like a pretty stable and secure probram since Im not logged in as root I wasnt able to do a few things I was trying so thats good.  But as far as a hacking attemp to my PC how good is Linux Ubuntu without a firewall compared to for example my additional PC running Windows XP and I have a load of firewalls i.e. Panda Professional, Zone Alarm Professional and Windows Firewall running? 

 I mean I heard is pretty secure without the use of a firewall is that true?  

Sorry for the dumb question....  Just learning Linux and to be honest Im looking at the possibilities of staying with it as my regular OS and never using windows again but Linux seems too complicated thats why Im trying to learn as much as I can to see what I can decide from here.

Any comments are appreciated!  I have been reading other posts and all of you guys seem like nice people who want to help!!!!!

---

### Post by lisati on 2007-09-05
Basically, it's as secure as you want it to be....with the added advantage that it REQUIRES a userid/password to log on to it, which other systems don't insist on.

Security from viruses (and other such "nasties") seems to be a matter of opinion, but because there are fewer for Linux by a significant factor, these are not likely to be a hassle.

---

### Post by freesitebuilder on 2007-09-05
This has good info on viruses (or lack of them!) in Linux:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by tribaal on 2007-09-05
Ubuntu comes with a very restrictive firewall enabled by default.
If you want to "see" it, you can install the "firestarter" package that will let you see and edit your firewall's config to your heart's content.
(to do this type the following in a terminal: sudo apt-get install firestarter)

You might want to read the [following very good article]("http://psychocats.net/ubuntu/security"). There is lots of info there.

Hope this helps

- trib'

---

### Post by southernman on 2007-09-05
IMO, you don't need a firewall, especially if your behind one of the many mass produced routers (Love my Linksys... and it's older than dirt itself). You can add a firewall if your super paranoid, but it isn't required. By design and default, Ubuntu has no open ports on a new installation. 

Can Linux/Ubuntu be hacked, well yeah, but it is entirely dependent on a lazy/ignorant/over confident system admin (technically, if you use Linux you are a system administrator to some degree). 

Ubuntu without a firewall or AV installed, is far more secure than a Windows box with layers of firewalls and AV software/scanners. 

By the way... Welcome to Ubuntu, and Ubuntu Forums!

---

### Post by nowshining on 2007-09-05
ubuntu comes with a kernel iptables which need to be configured - by default all ports are CLOSED not stealthed, i suggest arno-iptables-firewall great by default - easy to configure - change a 1 to 0 do disable or a 0 - 1 to enable and a ip block list just copy + paste and restart - and you can even input custom rules - type or copy and paste them in custom rules and restart the firewall.. :)



edit: if you need more help on that firewall just ask.. it uses iptables...and sets it up on every boot..

---

### Post by Malibu Illusion on 2007-09-05
> **tribaal said:**
> Ubuntu comes with a very restrictive firewall enabled by default.'

It does?  Actually, it comes with an unconfigured firewall by default in form of iptables.

Ubuntu's advantage is that a fresh installation has nothing listening on any of its ports.

---

### Post by Kobalt on 2007-09-05
To be precise Ubuntu comes with IPtables firewall installed but no restrictions are activated. On the other hand, all ports are closed by default, as said before.
About [Ubuntu security]("http://ubuntuforums.org/showthread.php?t=510812")...

---

### Post by az on 2007-09-05
> **lisati said:**
> Basically, it's as secure as you want it to be....with the added advantage that it REQUIRES a userid/password to log on to it, which other systems don't insist on.

It's the same with windows.  You can make Ubuntu autologin very easily.

> **lisati said:**
> 
Security from viruses (and other such "nasties") seems to be a matter of opinion, but because there are fewer for Linux by a significant factor, these are not likely to be a hassle.

Not true.  There are a significant number of linux computers running web and email servers on the internet.  As for the desktop, malware can not affect a GNU/linux computer in the same was a windows because it is source-based.  The binary interface (as well as many parts of the underlying OS) change all the time.

If windows actually did something to *prevent* viruses from working, they would break a lot of functionality.  That's why you have to scan for viruses instead of just plugging the holes they exploit.

In GNU/linux, this sort of thing wouldn't happen, the hole would be closed ASAP.

You don't need an antivirus not a firewall on an Ubuntu desktop.  Just keep up-to-date with updates.

---

### Post by Rev_neil on 2007-09-05
i may be new and this may be dumb, but why would hackers bother to get into a linux users PC anyway, as linux and most things u use are freely available 

On the other hand you have to buy windows, buy virus / firewalls and buy nearly any program you need(if u want the fully working vers), if u buy an item from a garge sale, ya might have to even buy the drivers to get it to work, Pretty soon You will probably have to Pay to turn a windows computer on

Username:
Password:
Visa/MC No:

:)

all the best
Take care

---

### Post by silent1643 on 2007-09-05
compared to xp linux is iron clad - keep in mind most virus' out there are made for windows so you are less likely to be infected, but your not 100% clear of trojans or virus' . 
useful [post]("http://www.littleubuntu.com/blog/?p=12") i have made in the past 

if you must have a firewall try firestarter

---

### Post by oilchangeguy on 2007-09-05
also see this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by eljoeb on 2007-09-05
> i may be new and this may be dumb, but why would hackers bother to get into a linux users PC anyway, as linux and most things u use are freely available

Personal information?

---

### Post by evildarknight on 2007-09-05
7 years with linux no problem at all concerning security 
check this page on wikipedia about viruses
[http://en.wikipedia.org/wiki/Windows_vs_linux](http://en.wikipedia.org/wiki/Windows_vs_linux)

---

### Post by lisati on 2007-09-05
> **az said:**
> It's the same with windows.  You can make Ubuntu autologin very easily.



The Windows machines I've used at home (2x XP home edition, 1xWin98SE) were set to autologin to an administrator account by default after a fresh install. With Ubuntu you have to set it to autologon on purpose. I'd say that the default setup for Ubunutu makes better sense from a security perspective. After the install, it largely boils down to personal choice when tinkering with the settings.

The only times I've had problems caused viruses were on a Windows machine, and that was largely due to carelessness on my part.

EDIT: I just remembered, **once** back in the 80s, a cover disk from a magazine I was checking out on someone else's MS-DOS machine had the "stoned" boot sector virus on it.......possibly someone in the shop had checked it out with an infected machine. Easily fixed with the right tools.

---

### Post by asmoore82 on 2007-09-05
> The firewall (iptables) is built into the kernel, and if you need to run services that require a firewall you can install a program like Firestarter to simplify the firewall configuration. By default, however, an Ubuntu install does not listen for incoming network connections unless a user specifically configures it to. **Out of the box, it is already more locked-down than a Windows box with a commercial Firewall**.
[https://wiki.ubuntu.com/CriticismFAQ#head-3d2b5b99a3764c54c33f95448f7157899d133481](https://wiki.ubuntu.com/CriticismFAQ#head-3d2b5b99a3764c54c33f95448f7157899d133481)

---

### Post by Xoanan on 2007-09-05
> **evildarknight said:**
> 7 years with linux no problem at all concerning security 
check this page on wikipedia about viruses
[http://en.wikipedia.org/wiki/Windows_vs_linux](http://en.wikipedia.org/wiki/Windows_vs_linux)

> **eljoeb said:**
> Personal information?

Or to knock down, Microsoft

---

### Post by evildarknight on 2007-09-05
na
with windows i had to restart my pc at least 4 times a day or had to kill processes to get it to behave
with debian i can keep my pentium mmx (for downloading things) running for a full week without ever taking a look at it!!!!!

---

### Post by bone2006 on 2007-09-05
az I think you misunderstood him.  Even though windows you can put in a username and password and require it to start up and ask you, you aren't forced to do this.  You can install windows completely without a password, which is the way a lot of people install windows, which could make it less secure.

---

### Post by hyper_ch on 2007-09-05
Furthermore a virus or malware on windows will do much mor damage... most programs require some admin access to actually run and everything is tightly knotted together... so if you can hijack just one program you get full admin access to the windoze machine...
On linux it's ver different... you have a modular structure here and most things can't do much on their own... so hijacking e.g. your browser doesn't let an attacker do too much...

---

### Post by bodhi.zazen on 2007-09-05
Well, that is a broad question.

In general , IMO, Linux is moderately secure, but it also depends on the version of Linux you are talking about.

There are versions of Linux specifically targeted at security and Ubuntu can be hardened.

See this link for more information [[color=black]Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812)[/color]

---

### Post by Chuck_Schuldiner on 2007-09-05
Thanks guys.. You guys are really good!  I have been here to be honest almost 2 days reading post after post after post just to see if I can get a better understanding about Linux and little by little is sinking in!!!  Im an IT student and the reason why I decided to go Linux is because well to be honest I never thought I would need it since I have 3 other computers with XP/XP pro and Vista but I have a teacher who introduced me to Linux and all the other Open Source software out there and is really nice.  I love the whole concept behind Linux and after I learned about it I just kinda fell in love with it.  Plus my school's IT is running everything in UNIX and Linux...

Thanks for all your tips guys it really helps....

now I will go and keep reading Linux for Dummies ;-) :guitar:

---

### Post by SpiritIsReality on 2007-09-05
howdy

very good thread, thanks all.

trails

---

### Post by az on 2007-09-05
> **bone2006 said:**
> az I think you misunderstood him.  Even though windows you can put in a username and password and require it to start up and ask you, you aren't forced to do this.  You can install windows completely without a password, which is the way a lot of people install windows, which could make it less secure.

I think we are mincing words.  It is not a there by default on a non-production windows system.  But every single corporate workstation that I have seen that runs a current (not windows 98) version of windows uses a login.  The model is the same as in Ubuntu.

If you want to nitpick and say that you can install a home edition of windows without a password, well, I can boot the Ubuntu live cd and become root without a password.

It's the same.

In that respect, it's not a valid pro-Ubuntu argument.

---

