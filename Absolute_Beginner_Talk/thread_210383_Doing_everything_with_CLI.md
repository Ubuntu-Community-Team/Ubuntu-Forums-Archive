---
title: "Doing everything with CLI"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by lucia_engel on 2006-07-06
I've been using Ubuntu for awhile now, and I really want to learn to do everything without relying on GUI.

I know a few basics like navigating through my files and installing programs, but how do I change my wallpaper, themes, burn CDs, configure my network, many other things, with only the command line?

I bought the Linux pocket guide to learn new commands, and I'd like more resources on useful CLI programs.

---

### Post by aysiu on 2006-07-06
Almost everything is a configuration file.

*locate* will help you find files. ```
locate kmenu.png
```
*grep* will help you find words within files. ```
grep -inr panel ~/.gconf
```
*nano* will help you edit files. ```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Lord Illidan on 2006-07-06
What's the purpose of changing themes and wallpapers with CLI, when they are essentially GUI stuff? Don't use CLI just for the sake of using CLI, or you'll find it dull, use it when you need it. If your purpose is to learn, though, then go ahead!

Research DCOP, you can do wonders with it in KDE and CLI.

---

### Post by Dr. Nick on 2006-07-06
Some stuff like changing themes/wallaper will be different depending on the desktop enviroment.  It would most likely require you to edit a config file.

Stuff like networking though can be done via the command line no matter what desktop enviro you use. If you look at the link in my signature, or click [here]("http://www.geocities.com/aebcoat/commoncommands.html") I have started a basic guide discussing a few common command line tools.

If you look in apt-get thier is a package called "burn"  to use the command line to burn cds, quote of the description

> Command line Data-CD, Audio-CD, ISO-CD, Copy-CD writing tool
Quick command-line tool to create Audio-CDs from .mp3, .ogg and .wav
files, to backup data, to create CDs from ISOs, to copy CDs on-the-fly.

Burn is a program/script written in Python that aims to quickly and
simply make audio CDs and backup of your data. It performs any of its
feature invoking it only once and with one and only one command line.
No previous ISO creation command is needed.

---

### Post by lucia_engel on 2006-07-06
[QUOTE=Lord Illidan]What's the purpose of changing themes and wallpapers with CLI, when they are essentially GUI stuff? Don't use CLI just for the sake of using CLI, or you'll find it dull, use it when you need it. If your purpose is to learn, though, then go ahead![/QUOTE]

Thanks for the replies so far.
I want to use CLI to understand how the program does it under its graphical frontend. I guess I just find it fun :p

[QUOTE=Dr. Nick]If you look in apt-get thier is a package called "burn" to use the command line to burn cds, quote of the description[/QUOTE]

Actually, I've tried using burn, but it always return this error
> Error. Please insert a blank CD/DVD. regardless of whether or not I have a blank disc inserted. I should file a bug report...

---

### Post by Lord Illidan on 2006-07-06
[quote=lucia_engel]Thanks for the replies so far.
I want to use CLI to understand how the program does it under its graphical frontend. I guess I just find it fun :p



Actually, I've tried using burn, but it always return this error
 regardless of whether or not I have a blank disc inserted. I should file a bug report...[/quote]


Hehe... understandable..

How about delving into vi, too.

---

### Post by uzi09 on 2006-07-06
oo, latest one ;P
well, number one: if you search the threads, you'll find at least a TON of these threads :d

here a few i found:
[http://www.ubuntuforums.org/showthread.php?t=73885&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=73885&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=170931&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=170931&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=163907&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=163907&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=121348&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=121348&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=113437&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=113437&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=98548&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=98548&highlight=learn+tutorials)
[http://www.ubuntuforums.org/showthread.php?t=55883&highlight=learn+tutorials](http://www.ubuntuforums.org/showthread.php?t=55883&highlight=learn+tutorials)
[http://ubuntuforums.org/showthread.php?t=189370&highlight=bash+shell+learn](http://ubuntuforums.org/showthread.php?t=189370&highlight=bash+shell+learn)

and some of my recommendations:
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by lucia_engel on 2006-07-07
Thanks for the links uzi09.
I know the basics of terminal like changing permissions, etc. (though I still have to look up the commands) I guess what I'm looking for is like a listing of **recommended** CLI programs.

Say under Web browser you'd have:
Lynx
Elinks
w3m
and under CD burning you'd have:
burn :)


Something like [Table of equivalent Linux/Windows softwares]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") but specifically for CLI programs, maybe with ratings and reviews too. Does anyone know more sites like that?

I can of course just search under Synaptic or try all the options listed in the Table of equivalent...but I wouldn't mind someone else doing the work for me :p


I've been trying to learn vim with the vimtutor, but I don't know how long it'd take for me to get use to its commands.

---

### Post by richbarna on 2006-07-07
> **lucia_engel said:**
> Thanks for the links uzi09.
I know the basics of terminal like changing permissions, etc. (though I still have to look up the commands) I guess what I'm looking for is like a listing of **recommended** CLI programs.

Say under Web browser you'd have:
Lynx
Elinks
w3m
and under CD burning you'd have:
burn :)


Something like [Table of equivalent Linux/Windows softwares]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") but specifically for CLI programs, maybe with ratings and reviews too. Does anyone know more sites like that?

I can of course just search under Synaptic or try all the options listed in the Table of equivalent...but I wouldn't mind someone else doing the work for me :p


I've been trying to learn vim with the vimtutor, but I don't know how long it'd take for me to get use to its commands.

CLI programs for Unix/Linux :-
[http://www.allworldsoft.com/keywords/unix/relevance/CLI/](http://www.allworldsoft.com/keywords/unix/relevance/CLI/)

For commands look at my "sig" for BASH (For using the Terminal/Console)
|
|
v

---

### Post by uzi09 on 2006-07-08
ahh ic.

actually, while reading up on linux tutorials and such, i've come across different sites that provide the exact table you're looking for for common programs. unfortunately, i've been to so many different sites, i'd have to google em to find some. i'll come back and post any results i find.

the best thing though, is to just google the program you're looking for and add "for linux" at the end. you'll find something eventually.

and as far as learning linux overall (programs and all) -- best thing i find is to just read books and keep using it. i've learned SOOOOOOOOOOOOOOo much more after just using it.

---

### Post by GNUbieNZ on 2006-07-16
Hi,

I found a really good book that will help you here.  Its 'UNIX Power Tools' published by O'Reilly.  U got it out from the library and read it basically cover to cover.

Its not a dry text text book, and i found it very easy to read and understand with awesome examples.

After reading it i appreciated the unix ethos of lots fo small apps that do only one thing but very very well.  I now regulary use sed/awk/cut etc that from the man pages seem impossibly hard but are now a piece of cake.

I cant recommend it highly enough!!

Dave

---

### Post by srf21c on 2006-11-17
I've been looking for a way to change the wallpaper from the command line in Xubuntu 6.10 so that I can get webilder working.  If anyone has figured this out, please post or PM me.

---

