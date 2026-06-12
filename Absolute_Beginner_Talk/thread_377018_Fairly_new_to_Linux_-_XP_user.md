---
title: "Fairly new to Linux - XP user"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by djdez92 on 2007-03-05
[B]Hey this is Des and I am failry new to Linux.

A few years ago I downloaded Mandrake and tried to install it to an old HP machine running Windows 98. I finished the installation when I started to have problems. I have used Live CD's since on and off.

I am a Windows user and always have been. I want to install Ubuntu to my computer without uninstalling my Windows. BUT I want to know how to do it safely with low risk of total screw up.

I personally am not a fan of Gnome and more comfortable with KDE, is there an Ubuntu with KDE? If not it's all good, Ubuntu seems to be the most user friendly Linux distribution out there that I have seen.

So if anyone can help me out a little and give me some tips, I will appreciate it greatly![/B]

---

### Post by oilchangeguy on 2007-03-05
kubuntu, has kde. however given the age of your computer it'll probably run better with xubuntu.

---

### Post by benfindlay on 2007-03-05
Yes its safe to install with windows. You choose during the installation procedure to manually partition hard drives and provided you have a spare partition you can leave your windows one untouched!

As for ubuntu with kde, its called kubuntu and there are cds to download or order online at [http://www.kubuntu.org/]("http://www.kubuntu.org/")!

Hope this helps and welcome to the club!

---

### Post by djdez92 on 2007-03-05
I am actually running a new HP right now.

Thanks for telling me about Kubuntu!

---

### Post by benfindlay on 2007-03-05
No problem, and just a word of warning, depending on what you want to do, you may want to download and install Dapper, not Edgy (version 6.06, not 6.10) It is slightly older but it is on long term support.

Don't know what real difference it makes to the typical user, but I do know that Edgy (the newer one) is more buggy and some of the things I need it for don't work properly!

---

### Post by ziggykg on 2007-03-05
If you're a KDE fan, there's Kubuntu, the KDE version of Ubuntu.

Ubuntu lets you install Linux without disturbing the exising Windows install.  

As usual back up any data that you'd rather not lose.  I've never last any data so far during a Linux install but best to err on the side of caution.

Then create some free space on your harddisk for your Ubuntu install.  The last time I did this, I used the partition manager app in the latest Ubuntu live CD.

If you're patient I suggest you wait for the next Ubuntu release in April.  It's just fab!  If you're not, download the lastest [Desktop CD]("http://cdimage.ubuntu.com/daily-live/current/") of the upcoming release.  I've installed it myself on a standard Dell PC which has XP and I can now boot one or the other at startup.

---

### Post by djdez92 on 2007-03-05
I have a AMD 64 chip in my computer, should I download the version made for that processor or can I download the regular PC desktop CD?

---

### Post by benfindlay on 2007-03-05
It's up to you, both work as far as I am aware, although you need the 64 version to take full advantage of your processor! Think there are a few things that are a bit glitchy on 64bit version, but don't quote me on that!

---

### Post by Phantom784 on 2007-03-05
There is an area of this forum dedicated to the 64bit version, which describes the different problems you might encounter when using this version and how to work around them.  I've never used the 64 bit version before, but I will be soon once my new system arrives.

---

### Post by igknighted on 2007-03-05
Debian (and by extension K/X/Ubuntu) tends to not integrate 32bit and 64bit apps well.  You will run into issues trying to get things like flash (which don't have 64bit versions) and other various programs working.  If you want to deal with these issues, you will get a slight performance gain at highly processor-intensive tasks (on my gentoo system for example compile times are much shorter), but in day to day tasks you only get the satisfaction of knowing you are ahead of the wave (if you are like me that means a lot).  32bit Ubuntu (i386) will work perfectly fine on your system, in fact will be less of a hastle, so for learning it is usually recommended.

---

### Post by djdez92 on 2007-03-05
I thank you all for helping me out.
I will try it out then Install.

If you are wondering why I have less experience on things is because I'm a youngsta at 15 years old.

But I have worked with computers for many years. So I'm pretty sure of what I'm doing.

---

### Post by djdez92 on 2007-03-05
I also am a little bit lost on installing things on Linux too. If it doesn't contain a self installing RPM I am pretty much shot.

I have had some success but never fully installed a tar.gz / .tgz file.

---

### Post by Nda on 2007-03-05
If your main concern is safety then I would recommend using the Alternate CD rather than the Live CD, and following [COLOR=SandyBrown]_[this comprehensive guide]("http://users.bigpond.net.au/hermanzone/")_[/COLOR].

Choose 6.06 rather than 6.10, substitute Kubuntu for Ubuntu if KDE is your preference and, as stated above, use the 32-bit version to ensure compatability.

This should reduce your risk factor from very small to very, very small indeed.:)

Nda

---

### Post by igknighted on 2007-03-05
Ubuntu uses .deb packages.  You should never scour the internet for programs except as a last resort either.  Just open up synaptic (or a terminal, then use apt-cache search) and search through what is available.  It will do the downloading, installing, and adding to the menus for you.  .tar.gz files generally need to be compiled, you need to install the build-essential package from synaptic for this.  Also, it is best to install the checkinstall and autoapt package too, as this will create .deb packages which ubuntu can easily install out of the source code (this allows for easy uninstalls/upgrades later on).

---

### Post by djdez92 on 2007-03-05
I have Kubuntu installed! Problem is, I can't seem to install a RPM file.... Can anybody help me with this?

By the way I wrote over windows, it's all good I can get a disc tomorrow and fix that..

As long as I can install a RPM I'm fine!

Loving Ubuntu so far! It's running great!

---

### Post by hscottyh on 2007-03-05
You shouldn't need to install an RPM. That is a package for fedora and other distros. Ubuntu uses .deb packages. Go to System -> Administration -> Synaptic to install software. Most stuff will be there if you enable all the repositories. If you can't find it there and you must download a package from a website look for DEB's not RPM's.

---

### Post by tht00 on 2007-03-06
> **djdez92 said:**
> I have Kubuntu installed! Problem is, I can't seem to install a RPM file.... Can anybody help me with this?

It is possible to install RPM files from the command line with a program called alien.  This is not recommended when the same packages exist in the repository.  Check to see if the package is in Synaptic first.

> **djdez92 said:**
> By the way I wrote over windows, it's all good I can get a disc tomorrow and fix that..

When you reinstall Windows, it will overwrite GRUB, the Linux boot loader.  You don't be able to launch Ubuntu without it, and your choices are to either: 1) reinstall Linux or 2) reinstall GRUB from the command line of the liveCD (can be a messy task, depending on the setup).

---

### Post by djdez92 on 2007-03-06
I will format my HD and install XP again then Install Ubuntu on my OS'less Laptop.

I figured out alien by the way, all good!

---

