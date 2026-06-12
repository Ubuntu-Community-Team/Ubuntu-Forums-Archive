---
title: "*Noob* How does installing apps work?"
date: 2005-08-12
forum: Absolute Beginner Talk
---

### Post by noobquestions on 2005-08-12
Hello everybody,

Sorry if this is a very very basic question but I don't have much experience with Linux distros. I'm looking at switching from WinXP to a Linux distro or MacOS X maybe sometime in the future.

I'm working with some applications that do have Linux versions, but from the way I get it there is no common installer for Linux, right? What I mean is I can't install a .rpm on Ubuntu for example? If so then the only distribution that I could use from that point of view would be RedHat. If I can't even run those apps that have Linux versions on any distro then that's a bit disappointing.

Or is this all nonsense? Looking for constructive input!

---

### Post by poofyhairguy on 2005-08-12
[QUOTE=noobquestions]
I'm working with some applications that do have Linux versions, but from the way I get it there is no common installer for Linux, right?[/QUOTE]

Well...Linux has a universal software package- the tar ball (source file). But we don't have cross distro binary installers with "next, next, next, finish" type installers yet.

> 
 What I mean is I can't install a .rpm on Ubuntu for example? 

Actually, we have this neat program called Alien that allows you to do that. It converts RPM to DEB (package format Ubuntu uses). Yet it does not work 100% of the time (sometimes the distro the RPM was made for is too different from Ubuntu.

If you have a particular RPM, I could show you how to deb it.

> 
If so then the only distribution that I could use from that point of view would be RedHat. If I can't even run those apps that have Linux versions on any distro then that's a bit disappointing.


If you need a certain 3rd party closed source app that requires you to have Red Hat, you might have to have Red Hat. For most free (open source) software, it is already packaged for Ubuntu. You then use synaptic to install programs:

[http://www.nongnu.org/synaptic/action.html](http://www.nongnu.org/synaptic/action.html)

After a little bit of fiddling, you can access over 16000 programs in synaptic.

Hope I helped. PM me if you need more info.

---

### Post by drummer on 2005-08-12
[QUOTE=noobquestions]Hello everybody,

Sorry if this is a very very basic question but I don't have much experience with Linux distros. I'm looking at switching from WinXP to a Linux distro or MacOS X maybe sometime in the future.

I'm working with some applications that do have Linux versions, but from the way I get it there is no common installer for Linux, right? What I mean is I can't install a .rpm on Ubuntu for example? If so then the only distribution that I could use from that point of view would be RedHat. If I can't even run those apps that have Linux versions on any distro then that's a bit disappointing.

Or is this all nonsense? Looking for constructive input![/QUOTE]
 Ubuntu is based on Debian, which uses the fantastic apt package management system. Most applications you will need are in the repositories (giant online stores of software on remote servers). First of all you will want to activate the extra repositories for Ubuntu (that can't be included by default due to legalities) by following the instructions at [http://www.ubuntuguide.org#extrarepositories](http://www.ubuntuguide.org#extrarepositories)

Then to install packages, open Synaptic (System > Administration > Synaptic Package Manager) and you will have access to about 16,000 packages to search for and install. Synaptic is a graphical front-end to apt, which keeps track of all the installed .deb packages (Debian's 'equivalent' to rpm) on your system.

---

### Post by Lord Illidan on 2005-08-12
And you might want to take a look at the Ubuntu Guide..

[www.ubuntuguide.org](http://www.ubuntuguide.org)

EDIT : You lot r too fast for someone who has just woken up!!

---

### Post by aysiu on 2005-08-12
I wrote a little tutorial just for you:

[http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

---

