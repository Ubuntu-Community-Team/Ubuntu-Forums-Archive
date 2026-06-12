---
title: "Should I try Arch?"
date: 2008-11-12
forum: Arch and derivatives
---

### Post by extruct on 2008-11-12
Hi, I heard about Arch and understood that its more or like Gentoo (I tried Gentoo successfully few years ago) but instead of compiling everything it have binary packages.
First of all I do happy with Ubuntu and used it for about 2 month without switching back to windows, so I'm planning to stay with Linux as much as I can. Also I'm planning to upgrade 8.04 to 8.10 soon (around the end of month) but i heard that its better to do a clean install. I want to have more control over my system: to have base system and than add packages as I need, but on the other hand I don't want to mess to much with configuration. Should I try Arch Linux? I heard is pretty good, and since I don't want to install Gentoo (too much time), but I'll do a clean install anyway so just wanted to hear your recommendations.
Thanks!

---

### Post by Rumor on 2008-11-12
If you are happy with Ubuntu and it is working well for you, then you probably do not have a reason to switch to Arch. I switched to Arch because of a few problems with Ubuntu and the fact that i did not enjoy the upgrade process between releases.

> **extruct said:**
> I want to have more control over my system: to have base system and than add packages as I need, but on the other hand I don't want to mess to much with configuration. Should I try Arch Linux?

You make a couple statements that are sort of in opposition to each other. You want control, but you don't want to configure. Unfortunately, to get the control, you have to do the configuration. Arch is wonderful for giving you the control. The base install gives you the tools you need to install only the programs you want and run only the services you want on start up. However, you have to do the basic system configuration. You'll have to edit your /etc/rc.conf file to tell Arch about your network, about the daemons you want started on boot up and a few other things. 

The documentation for Arch is wonderful. It will help you through the configuration steps, if you take the time to read it and understand why you are making those changes.

But, like I said at the beginning . . . If Ubuntu works and you're happy with it, stick with it. When you have a reason to switch to Arch, it will still be here for you.

---

### Post by chucky chuckaluck on 2008-11-12
arch is for you. there are options to autoconfigure various steps of the process, so the amount of configuring you do is dependent, in large part, on how much of it you want to do (though, you'll have to do some). the documentation is very clear and mercifully brief (and no idiotic manifestoes to sift through). go for it, i say.

---

### Post by SomeGuyDude on 2008-11-12
I think the "configuration" caricature of Arch is overblown. It's not like you're going to be sitting at your computer for three hours editing text files to get Arch to recognize your mouse or optical drive. Really, if you use auto-prepare on your HD, the installation itself requires almost no editing.

Setting up the system (alsa/X/etc) will take a little time, but it's not much more than copying a few easy to understand commands. Most of the time spent in an Arch setup is sitting around while packages install and later upgrade. Once you're set, you're pretty much good. Don't enable the testing repos and nothing should break terribly for you.

---

### Post by chucky chuckaluck on 2008-11-12
i was drunk the first time i installed arch, if that gives you any perspective.

---

### Post by extruct on 2008-11-12
Cool Thanks for the answers!
Ill try Arch in virtual machine, and if everything will go good I think Ill make it as my main system! I really want to have control as I said, and its pretty disappointing that Ubuntu don't let you to this control, at least an option to select what packages to install like Fedora, cause after Ubuntu installation I got a lot of things I never use: Bluetooth, PalmOs device and etc.
More comments for and against Arch Linux still accepted.
Thanks a lot!

Edit:
I have CPU that supports 64bit, and 1GB of ram (never will be updated to more than 4GB), should I use 64bit? I understood its not that stable as i686, am I right?

---

### Post by handy on 2008-11-12
> **extruct said:**
> 
Edit:
I have CPU that supports 64bit, and 1GB of ram (never will be updated to more than 4GB), should I use 64bit? I understood its not that stable as i686, am I right?

I always use 64bit on whatever distro, & I play games with Crossover & Cedega too.

Arch 32/64bit is stable, any problems I have had I have caused for myself, except for a couple of problems that have come from upstream, & they were no real problems in the end.

Flash & Java work in 64bit beautifully the following link gives all you will need:

***_[http://ubuntuforums.org/showpost.php?p=5945109&postcount=7](http://ubuntuforums.org/showpost.php?p=5945109&postcount=7)_***

---

### Post by elmer_42 on 2008-11-12
I figure that as long as you can follow instructions (specifically [these]("http://wiki.archlinux.org/index.php/Beginners_Guide") instructions) you can install Arch. The configuration is covered very well there, and if you want any more control you can always look up more specific tutorials.

---

### Post by SomeGuyDude on 2008-11-12
> **extruct said:**
> .Edit:
I have CPU that supports 64bit, and 1GB of ram (never will be updated to more than 4GB), should I use 64bit? I understood its not that stable as i686, am I right?

Stick with 32-bit. Any performance boosts will be incredibly negligible, and the drawbacks outweigh it, in my eyes.

If you had a production machine with 8GB of RAM and planned on doing a lot of CPU-heavy computing, then yeah I'd suggest going for it, but I'm in a similar position (with 2GB of RAM, though), and I found 32-bit Arch to be a better experience, in no small part because you never have to worry about compatibility.

---

### Post by RiceMonster on 2008-11-12
Yes, you should try it. To get more info on it, read these:
[http://wiki.archlinux.org/index.php/Arch_Linux](http://wiki.archlinux.org/index.php/Arch_Linux)
[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

Also, when you install, follow the beginners guide and you'll be fine:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by Dr Small on 2008-11-12
I would say that Arch is for you.
I moved to ArchLinux myself, because I wanted to control my system, remain minimalistic, and have a fast system (compared to GNOME on Ubuntu).

Installation is a breeze. I've found it to be very basic and simple. Once you finish, you are left with the core system to install and build what you want from there. Follow the Beginners Guide, and you will have no problems.

Of course, there is necessary configuration editing, but that's the fun part. It's not like you have to edit files every day (unless you really like to tweak your system all the time). I generally take a few hours when setting up Arch to install, tweak and setup sound/video and begin installing packages and configuring them. After that, I am just about done!

> **SomeGuyDude said:**
> Don't enable the testing repos and nothing should break terribly for you.

I've always enabled the testing repository and never had any problems (that were not caused by myself :D).

---

### Post by extruct on 2008-11-13
Well I tried Arch in VM, everything went fine except few kernel panics (probably due to old version of VritualBox, on a newer one all were ok). I really like the Arch way, its simple, fast enough, and also pacman is awesome (however I miss the auto-complete of packages on TAB hit), seems like I'm going to backup data now and install Arch! The night is going to be long :) Need beer :)

---

### Post by medic2000 on 2008-11-13
And extra good news for you can that you do auto-complete. Just look at the "sudo" section in the ArchWiki.

---

### Post by mips on 2008-11-14
> **medic2000 said:**
> And extra good news for you can that you do auto-complete. Just look at the "sudo" section in the ArchWiki.

[http://wiki.archlinux.org/index.php/Sudo](http://wiki.archlinux.org/index.php/Sudo)

---

### Post by extruct on 2008-11-14
Arch is awesome!
I like it very much!

---

