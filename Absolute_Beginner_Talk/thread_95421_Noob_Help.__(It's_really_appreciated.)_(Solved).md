---
title: "Noob Help.  (It's really appreciated.) (Solved)"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Tendril on 2005-11-26
Hello, I'm very new to linux.  Especially ubuntu, which I just reciently switched over to from XP.  So far, I have not regretted it, for even a second.

1)  How do you run a program after you download the tarball, extaract, make, make install, and make clean?  What do I do now?  How do I access the program to run it?  The program I tried is rxvt.

2)  What is a good terminal on desktop program?  Rxvt is what I have installed, but people say it's old, and outdated.

3)  I run Ubuntu, with the gnome UI.  Is there any nice way to switch to KDE, without downloading the iso of Kubuntu?

Thank you for your time, it's really appreciated.  Cheers!

 //Tendril

---

### Post by Xian on 2005-11-26
[QUOTE=Tendril]1)  How do you run a program after you download the tarball, extaract, make, make install, and make clean?  What do I do now?  How do I access the program to run it?  The program I tried is rxvt.[/quote]

If you will install the application with [Synaptic](https://wiki.ubuntu.com//SynapticHowto) it will probably install a launcher in the panel menu for you. That package is in the universe repos.

```
$ apt-cache policy rxvt
rxvt:
  Installed: (none)
  Candidate: 1:2.6.4-9
  Version table:
     1:2.6.4-9 0
        500 http://archive.ubuntu.com breezy/universe Packages
```

[QUOTE=Tendril]2)  What is a good terminal on desktop program?  Rxvt is what I have installed, but people say it's old, and outdated.[/quote]

I like rxvt and it is a good terminal. Who cares what others say?
If you like it then run it. 

[QUOTE=Tendril]3)  I run Ubuntu, with the gnome UI.  Is there any nice way to switch to KDE, without downloading the iso of Kubuntu?[/quote]

Open a terminal and tell apt to install the KDE library.

```
$ sudo apt-get install kde
```

---

### Post by aysiu on 2005-11-26
[QUOTE=Tendril]
1)  How do you run a program after you download the tarball, extaract, make, make install, and make clean?  What do I do now?  How do I access the program to run it?  The program I tried is rxvt.[/quote] Xian is right. It's in the repositories. You don't need to use tarballs unless you know exactly why you're doing it.

To enable extra repositories see the first link in my sig.
To install it, you'd ```
sudo apt-get install rxvt
```

> 
3)  I run Ubuntu, with the gnome UI.  Is there any nice way to switch to KDE, without downloading the iso of Kubuntu? ```
sudo apt-get install kubuntu-desktop
```

---

### Post by Tendril on 2005-11-26
Thank you for your help.  

1) Let's say that I didn't install with the package manager.  I installed through the terminal.  With make / make install / make clean.  Is there any way for me to get a launcher to put on my desktop?  I can't actually get into the program I have installed, or at least I don't know how.

2)  I'll stick with rvxt, then.  As long as it works.

3)  I can hold out for KDE.  Gnome is working for me.  So, I'm content, for now.

 //Tendril

---

### Post by Xian on 2005-11-26
[QUOTE=Tendril] Let's say that I didn't install with the package manager.  I installed through the terminal.  With make / make install / make clean.  Is there any way for me to get a launcher to put on my desktop?  I can't actually get into the program I have installed, or at least I don't know how.[/QUOTE]
You can create a launcher via the right-click menu.
For the command I would try /usr/bin/rxvt.

Or go back to the source folder and issue:
$ sudo make uninstall

Then use Synaptic to install the binary .deb package.

---

### Post by aysiu on 2005-11-26
Have you tried typing ```
man rxvt
```?

---

### Post by Tendril on 2005-11-26
```
       rxvt (ouR XVT) - a VT102 emulator for the X window system

SYNOPSIS
       rxvt [options] [-e command [ args ]]

DESCRIPTION
       rxvt,  version  2.7.10, is a colour vt102 terminal emulator intended as
       an xterm(1) replacement for users who do not require features  such  as
       Tektronix  4014  emulation  and  toolkit-style  configurability.   As a
       result, rxvt uses much less swap space -- a significant advantage on  a
       machine serving many X sessions.

OPTIONS
       The  rxvt  options  (mostly  a subset of xterm´s) are listed below.  In
       keeping with the smaller-is-better philosophy, options  may  be  elimi&#8208;
       nated or default values chosen at compile-time, so options and defaults
       listed may not accurately reflect the version installed on your system.
       ‘rxvt  -h´  gives  a  list of major compile-time options on the Options
       line.  Option descriptions may be prefixed with  which  compile  option
       each  is  dependent  upon.   e.g.  ‘Compile  XIM:´  requires XIM on the
 Manual page rxvt(1) line 1/usr/bin/tbl:/usr/local/man/man1/rxvt.1:775: `.' not last character on line
/usr/bin/tbl:/usr/local/man/man1/rxvt.1:775: giving up on this table

```

This is what I get.  Sorry, I don't know what it means, or what to do.

Currently, I'm trying several things, very few are actually working.  Does anyone have any real down to earth guides on the respositories, and the package manager.  I'll get it sooner or later.

Thank you all for all of your help.

 //Tendril

---

### Post by Xian on 2005-11-26
> **Tendril]SYNOPSIS
       rxvt [options] [-e command [ args ]][/quote]

This is telling you the command string format to use.

[QUOTE=Tendril]DESCRIPTION
       rxvt,  version  2.7.10, is a colour vt102 terminal emulator intended as
       an xterm(1) replacement for users who do not require features  such  as
       Tektronix  4014  emulation  and  toolkit-style  configurability.   As a
       result, rxvt uses much less swap space -- a significant advantage on  a
       machine serving many X sessions.[/quote]

This is the package description.

[QUOTE=Tendril]OPTIONS
       The  rxvt  options  (mostly  a subset of xterm&#180 said:**
>  

This is telling you how to use the command options.

[QUOTE=Tendril]Does anyone have any real down to earth guides on the respositories, and the package manager.  I'll get it sooner or later.

The [User Documentation Page ](https://wiki.ubuntu.com/UserDocumentation) is a good place to start.

---

### Post by aysiu on 2005-11-26
[QUOTE=Tendril]
This is what I get.  Sorry, I don't know what it means, or what to do.[/quote] Unfortunately, having never used rxvt myself, I have no idea, either. Those man pages are a hit or miss. Sometimes, they're clear. Other times, they're not.

> 
Does anyone have any real down to earth guides on the respositories, and the package manager.  I'll get it sooner or later. Yes, see the second link in my sig.

You can also read [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

That won't help you launch rxvt, unfortunately, but it'll let you know easier ways to install other software packages.

---

### Post by Xian on 2005-11-26
If -- and this is a big IF -- you installed it correctly from the source package, then you can open a terminal (it's easier to just create a launcher for repeated use), type in 'rxvt' and the application will appear in a new window.

That's all there is to it. Ignore all these other complications.

It pretty much acts like most terminals so you don't need to read the man files or any of that other mess to do the basics. If it won't start then remove the blasted compile using the command I gave you earlier and do it right the second time by using Synaptic.

---

### Post by Tendril on 2005-11-26
Yes!  I got it to work.  And, it was easier than I thought.  I downloaded it through Synaptic.  Thank you for being kind, and listening to a noob, talk about his linux problems.  

Lessons Leaned:
- Synaptic is your friend.  Make friends with it.
- If you ever have troubles, turn off your computer, and go lie down and think.  It helps a lot.

Have a nice day.

 //Tendril

---

