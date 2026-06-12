---
title: "A command line based distro"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-22
Hello, I was wondering if they make just a "command line based" version of Ubuntu, or some other distro, that when it finishes installing, all you have is a the command line.

I don't want any applications, or any desktop.
I want to install X11 after I get the command line, and then install VirtualBox. I would like the system to be as bare minimum as possible, and use the VirtualBox on another hard drive, to install different virtual machines.

Someone recommended the mini cd, the alternate cd, and debian to me, but I tried the mini cd, and once in the end, you have to select some form of server (i am guessing). But it has to download Mbs of system packages. I selected LAMP, but it never got anywhere, so I CTRL + ALT + DEL 'ed it, and it ruined my install. :| Clumsy ain't I :p

But back to the main question. Is there a distro that just install the command line and nothing else ? Well... No applications, just the system settings/requirements.

Dr Small

---

### Post by RomeReactor on 2007-09-22
Hi. You might want to try [Slax: Frodo Edition]("http://www.slax.org/download.php"); it just provides you with the command line and drivers, but let's you add modules before burning the image so you can customize which programs you want in it.

I used for just a few hours, though, so I can't assure you it will work as you intend.

---

### Post by Dr Small on 2007-09-22
I thank you for your response. I will try it out.

Dr Small

---

### Post by louieb on 2007-09-22
> **Dr Small said:**
> ... No applications, just the system settings/requirements.
Any of the alternate x-k-u-buntu have the option to install a command line only system. But may get a few extra programs such as  those need  to  connect to the internet. and maybe a samba client or you might get a program to let you add a user. Gentoo and Slackware also come to mind as distributions that pretty much let you roll your own. Even Puppy has a command line only install called barebone pup.

---

### Post by ayenack on 2007-09-22
You could download [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition") and config that.

---

### Post by AndyCooll on 2007-09-22
As ayeneck indicates you'll be wanting the Ubuntu Server edition. The default install for that is command line only version of Ubuntu (no X etc).

:cool:

---

### Post by testube_babies on 2007-09-22
Arch ([http://www.archlinux.org/](http://www.archlinux.org/)).

The default installation really does install ONLY what is necessary to get a command line (~100mb + a kernel).  After that, you can easily install X separate from any desktop environment / window managers.

It's quite a bit more difficult to learn than Ubuntu, especially since you have to manually configure a lot of options specific to your hardware, but it seems to be another viable alternative for what you're looking for.

Check out the beginner's guide:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by Dr Small on 2007-09-22
Ok, I will try out some of those other options.
But, I have a different question, somewhat...

When installing from the minimal cd, and after it downloads everything it is supposed to, it asks me what type of server I want to install. Example, DNS, LAMP, Edubuntu, Ubuntu Desktop, Ubuntu Server, ect.

It allows me to select multiple ones.
Can I just continue without selecting any, which would just leave me with a command line, or will it not work that way ?

Dr Small

---

### Post by MetalMusicAddict on 2007-09-22
Really. I think all of you have made this more complicated than it needs to be.

Dr Small. louieb mentioned it. Grab the Ubuntu "[Alternative]("http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso")" CD and when it boot choose the "Install command-line system" option. Done. :)

If you then want X do: **sudo apt-get install xorg**.

---

### Post by Dr Small on 2007-09-22
Yes, lol. I do seem to make things more complicated than they really are at times.
Thank-you. I will now look for a torrent, because of my bandwidth restrictions :p

Dr Small

---

### Post by asmoore82 on 2007-09-22
> **testube_babies said:**
> Arch ([http://www.archlinux.org/](http://www.archlinux.org/)).

The default installation really does install ONLY what is necessary to get a command line (~100mb + a kernel).  After that, you can easily install X separate from any desktop environment / window managers.

It's quite a bit more difficult to learn than Ubuntu, especially since you have to manually configure a lot of options specific to your hardware, but it seems to be another viable alternative for what you're looking for.

Check out the beginner's guide:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

+1 for [SIZE="3"]archlinux[/SIZE]
arch was the first system that I ever used that had binary packages/repos/dependency solving :D
which, of course, many other distros have in the form of apt ...

If you install arch, I highly recommend never installing anything but the bare "base" system
from the CD. Then boot into your new system and update ``pacman -Syu'' before adding
any other packages ``pacman -S *someprogram*''

---

### Post by bodhi.zazen on 2007-09-22
Ummmm ...

+1 Arch

---

### Post by Dr Small on 2007-09-22
I'll be downloading Arch and the alternate cd over the next couple of days to try them out :D

---

### Post by louieb on 2007-09-23
After looking at the beginners guide I get the feeling that Arch Linux  might be a good  distribution for learning the inside of Linux. 
But then I read the last for this page [http://wiki.archlinux.org/index.php/ArchLinux_Newbie_Guide](http://wiki.archlinux.org/index.php/ArchLinux_Newbie_Guide)
and it reads 
> **FAQs**

 **Q)** When I run "pacman --sync" it comes up with "could not open sync database:reponame have you used --refresh yet?" but when I run pacman --refresh it does nothing?! 
**A)** This error is due to your inability to read man pages.  We recommend you try the pacman man page - it really is very useful.
Wow that is real new user friendly:lolflag:

---

### Post by jordanmthomas on 2007-09-23
The arch community is very friendly and very helpful (the developers themselves will answer a lot of questions in the forums)  provided you have in fact looked at man pages, googled, etc.

I didn't read the wiki the first time I installed it and it took me a while to figure out 1. to use pacman and 2. how to use pacman (though I ended up finding the wiki), so if you do install arch make sure you read up on the installation wiki first.

Just read this or have this handy before you install it and you really shouldn't have any troubles with it (ftp install is broken atm though).

**edit** oh, and +1 arch.  :)

---

