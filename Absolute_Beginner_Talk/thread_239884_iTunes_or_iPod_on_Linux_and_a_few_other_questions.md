---
title: "iTunes or iPod on Linux and a few other questions"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by BigManJoe on 2006-08-19
My iPod is almost my second heart (if I had a second one) and I use many tools on Windows to mod it and do the usual sending of music and data to it. I have Linux on my iPod and I figured I'd like to try it on my PC.

I've been a Windows user since I started working with computers 12 years ago and I'm ready to switch, but only if iTunes works or if another application exists that does the same. I don't mean just sending over music, I mean like the same stuff iTunes does. I want to be able to import album art, and all that good stuff. I heard there's a way to get iTunes on Linux using some program, but I haven't even put Linux on my PC yet, much less used it before so would it be difficult to get that working? I've tried D.S.L. on my Xbox but it wasn't the same as a PC, and you couldn't do anything.

Next, I just want to know how difficult it is to install software on Linux. For my iPod, it all has to be done in the command prompt and I'm not a fan of that. Are there normal installers like Windows? 

Thanks for helping out a pathetic newbie. :)

---

### Post by hopstah on 2006-08-20
ok, there is a fantastic program named amarok which has almost all of itunes' functionality, including album art, smart playlists, dynamic playlists, radio streams... and it also has some great functionality that itunes doesn't, such as fetching similar artists and displaying them, integration with wikipedia, last.fm support.....  the one thing that i really miss is being able to define that a song should start playing at, say, one minute into it to get rid of some annoying intros that some songs have.  also, m4b (official audiobook format) isn't supported as of yet, but i don't think that's too far off.

i have an ipod, and haven't found anything that i can't do with it in linux, you just need to get used to a *different* (not better, and not worse, just different) way of doing things.

remember, linux is NOT windows

and as far as the installer goes, yes - you can boot right into a livecd version of ubuntu, and from there there is an icon on the desktop which initiates the install process.  easy, peasy, japanesie.

---

### Post by kombipom on 2006-08-20
As far as I know there isn't an all-in-one replacement for iTunes in Linux.  However there are apps which can do the things that iTunes can do.  At the top of this forum is a sticky called Read this First which contains a handy list of software equivalents in Ubuntu and Windows including software that will perform the various functions of iTunes.

More generally, before you go ahead and install Ubuntu you should be prepared for that fact that using Linux is substantially different to using Windows and it will take some getting used to.  Almost everyone here will tell you that it is well worth the (usually small amount of) effort required.

I see hopstah beat me to making much the same point ;)

---

### Post by 3rdalbum on 2006-08-20
Installing software on Linux is much, MUCH different to installing software on Windows.

On Windows, you have to double-click a program, click "Next" a whole heap of times, wait while the program hogs your whole system, etc. And the installer usually has all sorts of components that you already have on your system, so you're basically downloading a file that's twice as big as it needs to be.

You occasionally get that sort of installer on Linux too, but generally you just use the repositories which you access through the Synaptic Package Manager. With these, you just select what you want to install. The package manager then figures out what else it needs to install that you don't already have, and then downloads and installs the stuff in the correct order. You can go on with other work while it's happening, and it almost never asks you any further questions.

I've never used iPod Linux, so I can't comment on how to install programs on that. If it's just a single command that you have to type in, my suggestion is to try not to get annoyed by that; many people prefer to type one command than click a whole bunch of buttons in a GUI.

---

### Post by BigManJoe on 2006-08-20
Thanks guys. I'm burning the .ISO right now. *Corsses fingers*

---

### Post by catlett on 2006-08-20
> gtkpod is a linux app for ipod

> About:
gtkpod is a platform-independent GUI for Apple's iPod using GTK 2. It allows you to import your existing iTunes database, add/delete songs/playlists, edit ID3 tags, modify the iTunes database without having the iPod connected, and synchronize at a later time. It also features international charset support for ID3 tags, detects when adding already existing songs, and more
When you install, go to the top panel and enter into System<Administration<Synaptic Package Manager this is the gui for all the free software that is available for the Ubuntu distro. The software is kept in online repositories. All you do is search for your application, mark it for instalation and hit apply. Synaptic will fetch it from the repository and install it.
There are different repositories. You can enable more after installation. I say this because gtkpod is in my synaptic but I have extra repositories enabled.

Here are a few links to help you out.
First is how to install anything in Ubuntu [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Next is the Dapper Guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
This is the Dapper guide's page on repositories [http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories](http://doc.gwos.org/index.php/DapperGuide#How_to_add_extra_repositories)

---

### Post by sinaen on 2006-08-30
> **hopstah said:**
> ok, there is a fantastic program named amarok which has almost all of itunes' functionality, including album art, smart playlists, dynamic playlists, radio streams... and it also has some great functionality that itunes doesn't, such as fetching similar artists and displaying them, integration with wikipedia, last.fm support.....  the one thing that i really miss is being able to define that a song should start playing at, say, one minute into it to get rid of some annoying intros that some songs have.  also, m4b (official audiobook format) isn't supported as of yet, but i don't think that's too far off.

i have an ipod, and haven't found anything that i can't do with it in linux, you just need to get used to a *different* (not better, and not worse, just different) way of doing things.

remember, linux is NOT windows


heres to make audiobooks in m4a format. and to get amarok to work with them.

[http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support](http://www.ubuntuforums.org/showthread.php?t=180073&highlight=audiobook+support)

---

### Post by justin whitaker on 2006-08-30
> **BigManJoe said:**
> My iPod is almost my second heart (if I had a second one) and I use many tools on Windows to mod it and do the usual sending of music and data to it. I have Linux on my iPod and I figured I'd like to try it on my PC.

I've been a Windows user since I started working with computers 12 years ago and I'm ready to switch, but only if iTunes works or if another application exists that does the same. I don't mean just sending over music, I mean like the same stuff iTunes does. I want to be able to import album art, and all that good stuff. I heard there's a way to get iTunes on Linux using some program, but I haven't even put Linux on my PC yet, much less used it before so would it be difficult to get that working? I've tried D.S.L. on my Xbox but it wasn't the same as a PC, and you couldn't do anything.

Next, I just want to know how difficult it is to install software on Linux. For my iPod, it all has to be done in the command prompt and I'm not a fan of that. Are there normal installers like Windows? 

Thanks for helping out a pathetic newbie. :)

There is an article over on Linux Journal on using an ipod on linux today:

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

They did not mention that both Banshee and Amarok are alternatives to using Rhythmbox to transfer files.

---

