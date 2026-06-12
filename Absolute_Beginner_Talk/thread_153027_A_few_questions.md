---
title: "A few questions"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by crakkajakka15 on 2006-03-31
hey whts up i finally got ubuntu up and working on my system (p3 1.0gzh, 512ram, 80 gig hd) thank to all of those who helped me. OK now to my question. I am coming from the world of MAC's and PC's. I think i have those 2 down pretty well to be dangerous. Now my question is i cant for the life of me figure out how to download and install a program with this OS. (5.10) example xmms, which is the mp3 player correct? Also is there a program that will play wma files and quicktime files on this OS. ALso do i need anti virus for ubuntu also? if so any good one out there? PLease help. Once again Thanks alot
Todd

---

### Post by hw-tph on 2006-03-31
Start by reading the [Ubuntu Desktop Guide](http://doc.ubuntu.com/ubuntu/desktopguide/C/index.html). It should answer most of your questions.

You want to install XMMS? No problem: **sudo apt-get install xmms**
...or use the aptitude or synaptic programs (the latter found in System menu --> Administration --> Synaptic Package Manager). Have a look at beep-media-player too, it is a GTK2 fork of XMMS so it fits better in with the Gnome2 desktop Ubuntu uses.

As for antivirus, well the jury is still out on this one. There aren't many virii out there that attack Linux, but if you exchange files with Windows users a lot (if you're on a network with Windows systems for example) you should consider installing antivirus. Not because Ubuntu is vulnerable but because it is *your* responsibility not to further distribute any virus that ends up on your computer. If you don't use Windows at all or don't have much interaction with Windows users I'd say skip the antivirus program.


Håkan

---

### Post by firehead on 2006-03-31
welcome crakkajakka15 to the fascinating world of (k)ubuntu linux
well installing progs isn't as difficult as most people think. the easiest way is to use the stuff, that's in the repositories (which is a lot!). now to do so you type ```
sudo apt-get update 
```
to fetch the newest 'file lists' from the repositories and then type
```
sudo apt-get install name-of-programm-to-install
```
where xmms as name of program should work perfectly. however if you're a little more into gui installing, i recommend using adept or kynaptic. these are quite intuitive to use...
a third alternative would be to use a automated gui installer like automatix, which can install the most common applications (including media-players for almost any format imaginable). you'll find infos about automatix here: [automatix-thread]("http://ubuntuforums.org/showthread.php?t=80295")
concerning antivirus-programs, there are a lot of discussions about wether it's necessary or not...me personally i don't use one and i don't even know one,so i can't help you on that...

have fun

---

### Post by Praetorian on 2006-03-31
Take a look at the [wiki ]("https://wiki.ubuntu.com/RestrictedFormats")it covers a lot's of info on the codes you need to install to play al your movie's, mp3's etc. 

You don't need anti-virus on your ubuntu system :). There is ClamAV but it is for windows virus.

---

### Post by 3rdalbum on 2006-03-31
I recommend you install MPlayer. When you do, it'll automatically install XMMS too. Visit the MPlayer homepage (whose URL eludes me right now) and you'll find a file there called "w32codecs". Download that, follow the instructions, and you'll have the ability to play most formats (including Quicktime and WMV (?))

---

