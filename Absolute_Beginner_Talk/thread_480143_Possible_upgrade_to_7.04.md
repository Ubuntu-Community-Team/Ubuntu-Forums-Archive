---
title: "Possible upgrade to 7.04?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Fenryr on 2007-06-21
g'day, folks...I've recently gotten the disk for Ubuntu 6.06(LTS) to install, partition, and set me up with a working dual boot machine, but I have a few questions:

Is it now possible to upgrade to 7.04 without losing any of my current settings or programs? Is it WORTH doing so?
If I wish to use mostly KDE programs, such as the editors, debuggers, and compilers for C++ in order to learn programming in that language, should I just install Kubuntu instead, or simply install KDE packages into the existing system?

I've been using Firefox, but I can't seem to get the NEWEST version (2.0) to install, and I can't get firefox to update ITSELF, as it does under WinXP. How do I resolve this issue?

I"m sure I'll have a few million more questions as time goes on, but so far I'm cautiously pleased with this OS...If FFXI ever gets ported to run in it, I'll happily toss Windows and all other MS products off my machine for good and all...*g*

---

### Post by bobfarrell on 2007-06-21
Updating Ubuntu is easy, there's an update manager that automatically gets software updates (similar to Windows Update), and it also has a system upgrade to get the latest distribution release.

If you think you'll mostly be using KDE I'd say it wouldn't hurt to install standard Ubuntu and then get KDE as well (or get Kubuntu and get Gnome as well). You can still run KDE programs in Gnome and other desktop environments. I switched around between a few but currently using XFCE4.

What problems are you having installing Firefox 2.0?

Opera's worth a look too - they have up-to-date distribution-specific .deb packages so it's easier to install, so if you can't get your Firefox issues resolved you might want to give that a go.

---

### Post by sankarv on 2007-06-21
you can upgrade using the update manager which comes with ubuntu. U can see that somewhere in the System menu.

the kde packages r enough no need to have kubuntu for this. 

definitely u will  hav a new look n feel in ubuntu 7.04..

for firefox check its website / search the web. there are binaries available for latest versions.

---

### Post by bobfarrell on 2007-06-21
You might want to try automatix as well, that'll probably have the latest Firefox release and it'll do everything for you.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

There are straight forward install instructions there, just type in a few terminal commands and it should appear on your systems setting menu, if not call ```
gksudo automatix2 
``` from a terminal.

Installing KDE is easy:
```
sudo apt-get install kde
```

So it doesn't really matter whether you get KDE or not. Install it, then log out and select KDE from the sessions manager.

---

### Post by Kobalt on 2007-06-21
You actually cannot update straight from Ubuntu 6.06 to Ubuntu 7.04 (you would need to upgrade to 6.10 in between, but you would run into a long a possibly buggy process).
If I were you I'd [make a separate Home partition]("http://www.psychocats.net/ubuntu/separatehome"). This way you store all your personnal files and settings whatever version of Ubuntu you'll install, whatever Linux distro. And so, you would make a clean install of Ubuntu 7.04.

Just a couple of advices : if you want to install KDE I would either run ```
sudo aptitude install kde-core
```
or```
sudo aptitude install kubuntu-desktop
```
Installing just the 'kde' package will bring you almost all the KDE packages, and there's a great chance you don't want that. 

If I want to install some new softwares or anything else, I wouldn't use Automatix in any way...

---

### Post by Fenryr on 2007-06-21
> 
Just a couple of advices : if you want to install KDE I would either run
Code:

sudo aptitude install kde-core



Ok, after running the above command, I now get the following error message on boot:

Cannot open theme file/usr/share/apps/kdm/themes/kubuntu

The machine hangs there until I click the button under it, then gives me a Kubuntu login screen, which functions normally. once logged in, the system seems to work just fine, but the same message appears again on shutdown, again hanging until I acknowledge the message, after which it shuts down normally. Seems kinda sloppy to me, even though it hasn't affected the functions of the OS otherwise. Any thoughts on how to get rid of it? Did I miss a file somewhere?
Thanks...

---

