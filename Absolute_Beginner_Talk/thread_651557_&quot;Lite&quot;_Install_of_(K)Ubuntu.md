---
title: "&quot;Lite&quot; Install of (K)Ubuntu?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Sir Chasm on 2007-12-27
Hi, I'm just about to do a reinstall of Kubuntu, and I was wondering if there's a way to install only the barebone OS. I don't want to build the OS myself. That's too much research and work (unless it was really easy and then I'd appreciate someone linking me to a guide), I just don't want all the extra programs that come with it to be installed. If I want to have a torrent program, for example, I'll add it myself. If I want bluetooth connectivity, I'll add it myself too. And other programs I know I'll end up switching anyway (like Konqueror for Firefox), so what's the point of me installing Konq if I'm going to remove it after anyway?

I know I can go back and remove all the stuff I don't want myself, but the problems with that is:

a) Some programs invariably leave traces of themselves behind, like Ark, which leaves right-click context menus after I got rid of it. I know I can get rid of those too if I search around, but as you can see, removing OS bloat then becomes a major pain in the ***. Although I guess since I've switched to Linux, I should be used to pain in the ***.

b) Some packages are dowright cryptic (and I'm not really a n00b when it comes to computers), and sometimes even google searches don't bring to light what it does, and how it's used and by what. Thus it becomes difficult to distinguish if I'll ever need that package or not.

So yeah, what are my options here if I wanna scale back the initial install?

---

### Post by LaRoza on 2007-12-27
Yes, you can do a bare bones of *buntu

Get the alternate disk, and "install a command line system" or something like that.

---

### Post by SOULRiDER on 2007-12-27
You will have to start building everything from there.

IMHO, if you want to build something from the very bottom I suggest you try other distros more "oriented" for doing such things.

---

### Post by LaRoza on 2007-12-27
> **SOULRiDER said:**
> You will have to start building everything from there.

IMHO, if you want to build something from the very bottom I suggest you try other distros more "oriented" for doing such things.

Arch

---

### Post by SOULRiDER on 2007-12-27
> **LaRoza said:**
> Arch

For example, but if you have the patience and are brave enough you could experiment with distros like Gentoo (with emphasis on time and brave)

---

### Post by Sir Chasm on 2007-12-27
Hmm, well I wasn't ready to move to a whole new distro yet. I just installed Kubuntu now for the very first time, and I like it so far, but I quickly came across the same problem that I hate about the pre-loaded Windows install I originally had with my laptop - it came with a whole bunch of bundled software that I really didn't want.

How "easy" is the command-line installation or Arch installation? Does it kinda walk you through it asking questions and giving you options and stuff, or does it pressupose you know in advance what stuff you want and the exact commands to install it?

---

### Post by SOULRiDER on 2007-12-27
Its kind of between the middle. The best thing you can do is print the wiki and have it there when you install to help you. You should also learn to use CLI programs like irssi and links. Links is for web browsing, and irssi is for IRC. If you get on IRC while youre installing i can help you out.

---

### Post by flamelab on 2007-12-27
You should have a guide .

&#919;ere in Greece I followed a great guide ,you could translate greek to english here -->[www.google.com/translate]("www.google.com/translate")

The url of the greek arch guide -->[http://adslgr.com/forum/showthread.php?t=88599#content_start]("http://adslgr.com/forum/showthread.php?t=88599#content_start")

For a weird reason the url translation doesn't work , you could copy paste the text from the site to google translate

edit : the same greek author helped in the greek translation of this -->[http://www.my-guides.net/en/index2.php?option=com_content&do_pdf=1&id=49]("http://www.my-guides.net/en/index2.php?option=com_content&do_pdf=1&id=49")

---

### Post by SOULRiDER on 2007-12-27
> **Sir Chasm said:**
> 
a) Some programs invariably leave traces of themselves behind, like Ark, which leaves right-click context menus after I got rid of it.

Should a bug report be filed for that?

---

### Post by benerivo on 2007-12-27
> **Sir Chasm said:**
> How "easy" is the command-line installation

It's quite easy. You will first be presented with a few graphical screens that ask you for language, partitioning and user account options and it will then install. On boot, it will take you to a command line, where a few commands will install the base kde system. I have done it several times.

---

### Post by flamelab on 2007-12-27
> **benerivo said:**
> It's quite easy. You will first be presented with a few graphical screens that ask you for language, partitioning and user account options and it will then install. On boot, it will take you to a command line, where a few commands will install the base kde system. I have done it several times.

I wish it were so easy . You have to change rc.conf , to create xorg.conf , to do a lot of things , you must have a guide . Someone who has just left Ubuntu doesn't know what to install in an empty distro !

---

### Post by benerivo on 2007-12-27
> **flamelab said:**
> I wish it were so easy . You have to change rc.conf , to create xorg.conf , to do a lot of things , you must have a guide . Someone who has just left Ubuntu doesn't know what to install in an empty distro !

Yes, you must have a guide to do it, although it really is only three commands...

sudo apt-get install xorg kdm kdebase
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start

At least it is on my machine. The second command will take you to a graphical setup of xorg which i just select the defaults for and it works.

---

### Post by flamelab on 2007-12-27
I am talking about Arch linux , that he asked before .

Kubuntu alternate cd **does **have a GUI after installation . He doesn't need anything over that .

---

### Post by Sir Chasm on 2007-12-27
Well then, that just makes it that much easier to stick with KUbuntu. :p

I'll find a guide for the Alternate CD thing, thanks.

---

### Post by benerivo on 2007-12-27
> **flamelab said:**
> I am talking about Arch linux , that he asked before. Kubuntu alternate cd **does **have a GUI after installation . He doesn't need anything over that .

Sorry flamelab. I'm talking about the alternate ubuntu install that he asked about, so that he can have a lighter version of kubuntu.

---

### Post by Sir Chasm on 2007-12-27
> **SOULRiDER said:**
> Should a bug report be filed for that?

Dunno really, I removed it through Adept Add/Remove programs, and I noticed that in Dolphin, when I select a compressed file, there's a right click-menu for extract with Ark, or something similar. I'm not really experienced with Linux yet to be filing bug reports. I've worked as a software tester, so I know how agrravating poorly-written bug reports are. :p

---

### Post by Sir Chasm on 2007-12-27
One more thing, I gotta say, the friendliness and helpfullness of these forums is really astounding. I've been reading some of the threads here, and these forums are by far the most newbie-friendly place I've seen out of all the forums I've been on over the years. :)

---

### Post by SOULRiDER on 2007-12-27
Remember to **SAVE YOUR WORKING XORG.CONF, YOU'LL NEED IT!** The KDE distribution in Arch sucks butt, you'll have to add the kde-mod repo to have a nice modularized KDE.

---

### Post by Sir Chasm on 2008-01-02
> **benerivo said:**
> Yes, you must have a guide to do it, although it really is only three commands...

sudo apt-get install xorg kdm kdebase
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start

At least it is on my machine. The second command will take you to a graphical setup of xorg which i just select the defaults for and it works.

After digging through the forums, I've found out about the command

```
apt-get install kubuntu-desktop
```

from this thread: [http://ubuntuforums.org/showthread.php?t=644327](http://ubuntuforums.org/showthread.php?t=644327)

My question is how benerivo's commands that I quote relate to the command above? Do they accomplish the same thing? Just wondering which one (or maybe both?) to use.

---

### Post by benerivo on 2008-01-06
Sir Chasm, "apt-get install kubuntu-desktop", will give you the full kubuntu distro, as you would have if you installed kubuntu from the live cd. The kubuntu distro is the kde base, with extra programs, some desktop and environment settings, and artwork on top, as chosen and setup by the kubuntu team.

The command line installation is just the core of ubuntu with no programs or graphical desktop at all. The lines i quoted above are what i would add to such an installation. They provide a graphical server and the kde base, which includes only basic applications like a text editor, console, settings manager, web browser and file manager.

---

