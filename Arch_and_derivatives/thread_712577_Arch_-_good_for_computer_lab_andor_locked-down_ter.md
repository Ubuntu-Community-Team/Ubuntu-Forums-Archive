---
title: "Arch - good for computer lab and/or locked-down terminals?"
date: 2008-03-01
forum: Arch and derivatives
---

### Post by sajro on 2008-03-01
I am wanting to switch my school's computer lab over to Linux, but I have been given the task of making a system with similar functionality to the current Windows XP system. (The reason I am able to do this is because the IT infrastructure of this part of the school isn't bound by the county's Windoze because it's PTA funded. Also, the filternazi software is server based (I can tell because my Live CDs still get filtered net.))

What it needs to be doing is: web browsing, office work (OpenOffice already in use, so that's easy enough), and be hard to mess with. I think Arch would be good because these machines are almost bleeding-edge and the newer processor optimizations would be good. Not to mention it's not bloated and is more confusing to script kiddies than Ubuntu, Fedora, etc.) I do, however, need a little more help as to how to do these.

I'm thinking KDE. Fluxbox + iDesk would be my second choice but KDE for simplicity and familiarity (for some people) would be better, plus its automatic handling of things many people get confused by. What I need to know there is: what is the difference between KDE and KDEmod?

As for web, it's Firefox (*ahm* I mean "Gran Parasido", Arch users). I need to know how to lockdown Firefox to prevent students from bookmarking, accessing proxy settings (transparent proxies), installing extensions, etc. I know quite a few people who would really abuse those.

For office, it's obvious to use OpenOffice. It's heavier than I'd like, but the hardware can handle it. It's also familiar for some of the people there.

As for hard to mess with, I mean tinkernazi lockdown on the system. Keeping people from changing the KWin theme, installing via Pacman, changing desktop background, etc.

I need to make an ISO for quickly installing this system wherever needed, fully configured (the whole lab's hardware is identical). Also, I need to be able to SSH in from home to work out problems. I'm kind of new to a lot of this, so I could use help with that.

 I'm also trying to learn some Python and PyGTK to make my "Stupidity Safeguard" program, which is a simple lockdown program requiring the root password for shutting down X, killing system processes, etc. I initially thought of it to keep myself from stupidly hitting unknown key combos, but thought it would work well for this. So, if you could direct me to some resources to aid in that, and especially how to require root privileges to configure it, I'd appreciate it.

Thanks in advance,
Sajro

---

### Post by Rumor on 2008-03-01
I've used Arch for a small network of computers in our church. We were NOT using state of the art hardware, so Arch was ideal for its lightness.

I used Dan's Guardian [http://dansguardian.org/](http://dansguardian.org/) for managing web use (blocking inappropriate sites).

Since pacman requires root privileges to run, it was not an issue. The user account was not really locked hard. They were free to change the desktop background and mess with themes and whatnot since the only settings they could effect were in that user's /home.

I used ssh for remote admin so I could pacman -Syu from home and restart systems as needed.

I'd create three user accounts: root, your user account and the general user account. Use your account for ssh. Your general account does not need to be a member of all possible groups. You can limit access to cdroms or usb drives or whatever if you don't want users using them.

---

### Post by mips on 2008-03-03
> **sajro said:**
> What I need to know there is: what is the difference between KDE and KDEmod?


KDEmod is a modular KDE and you have more choice over what is being installed. A rough example would be you install package kdemultimedia from kde, this is a meta package wich actually installs several packages. In kdemod they break the kdemultimedia package down into smaller bits and allow you to choose what components of it to install ie. kdemod-kdemultimedia-kaudiocreator.

This has basically been done with the whole kde and it makes for a nice lean & clean kde install. kde should actually be like this by default if you ask me as it is so much better.

---

### Post by pieisgood4589 on 2008-03-21
> **sajro said:**
> I am wanting to switch my school's computer lab over to Linux, but I have been given the task of making a system with similar functionality to the current Windows XP system. (The reason I am able to do this is because the IT infrastructure of this part of the school isn't bound by the county's Windoze because it's PTA funded. Also, the filternazi software is server based (I can tell because my Live CDs still get filtered net.))

What it needs to be doing is: web browsing, office work (OpenOffice already in use, so that's easy enough), and be hard to mess with. I think Arch would be good because these machines are almost bleeding-edge and the newer processor optimizations would be good. Not to mention it's not bloated and is more confusing to script kiddies than Ubuntu, Fedora, etc.) I do, however, need a little more help as to how to do these.

I'm thinking KDE. Fluxbox + iDesk would be my second choice but KDE for simplicity and familiarity (for some people) would be better, plus its automatic handling of things many people get confused by. What I need to know there is: what is the difference between KDE and KDEmod?

As for web, it's Firefox (*ahm* I mean "Gran Parasido", Arch users). I need to know how to lockdown Firefox to prevent students from bookmarking, accessing proxy settings (transparent proxies), installing extensions, etc. I know quite a few people who would really abuse those.

For office, it's obvious to use OpenOffice. It's heavier than I'd like, but the hardware can handle it. It's also familiar for some of the people there.

As for hard to mess with, I mean tinkernazi lockdown on the system. Keeping people from changing the KWin theme, installing via Pacman, changing desktop background, etc.

I need to make an ISO for quickly installing this system wherever needed, fully configured (the whole lab's hardware is identical). Also, I need to be able to SSH in from home to work out problems. I'm kind of new to a lot of this, so I could use help with that.

 I'm also trying to learn some Python and PyGTK to make my "Stupidity Safeguard" program, which is a simple lockdown program requiring the root password for shutting down X, killing system processes, etc. I initially thought of it to keep myself from stupidly hitting unknown key combos, but thought it would work well for this. So, if you could direct me to some resources to aid in that, and especially how to require root privileges to configure it, I'd appreciate it.

Thanks in advance,
Sajro

If the computers have more thank 256MB of RAM, why not Linux Mint community KDE edition or Kubuntu? They get updates frequently, and a completely new system every 6 months... If the 6 month upgrades are just too much of a hassle for the schools, MEPIS is the best Linux distro ever for hardware detection, and it's very easy to use. :lolflag:

PS- Hi :)

---

### Post by jseiser on 2008-03-24
im an arch fanboy - but i dont think you would want arch on a computer lab - you will have to update all teh time for security updates, and that could in turn cause a problem.  I havent actually had a problem with the packages being so new, but a little while back, large amounts of people had xorg issues etc.  That would seriously stop your pc lab from working untill the arch packagers fix the issues, or you will spend all week configuring your pc's.  Might be better to get a basic slackware install, sometihng that wont crash.

---

