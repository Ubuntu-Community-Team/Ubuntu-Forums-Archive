---
title: "Insufficient computer background education?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Nakajoe on 2006-08-04
A very general question, and one that might sound a bit odd, but here goes. I`m a fairly new Linux user (2~3 months) and have run across several problems along the way, as seems normal. 

No problem, except that these issues take me a long time to work out. A really long time. This is the case because I can very rarely understand instructions I find after a google as-is and have to look up many of the subprocedures one by one. For instance: it says here to edit fstab. Wonder what that is. :: off to google again :: (note: that problem is solved already, no need to answer ;) )

While not really a bad thing per se, I would personally prefer to get my hands on something or other that would help me understand the system on a more basic level--that is, not just finding a tutorial that tells me the keystrokes required to fix the problem, but rather prior to any specific problem something that would let me take an educated guess as to why a given problem might be happening in the first place. Personally I`ve been using computers for as long as I can remember (23 now), but have never really studied how they work and recently have been getting extremely curious about the insides of the machine (software/hardware both).

In short, as per the subject line, I`d like to re-educate myself on background, basics, etc. Rather than blindly wander off by myself, I was hoping somebody could give me some sort of direction. Good website, good book, good area to study first, very important area of study, whatever. I`m poor so cheap stuff is better, but I appreciate any leads.

Thanks for your time,
Joe

---

### Post by WADemosthenes on 2006-08-04
Me too!  If theres a good book that will help, I'd like to know about it.  Generally though, I I use the Ubuntu forums, wiki, and google, and it usually works out.

---

### Post by XAsmodeanX on 2006-08-04
I'll point you in the same direction that I was pointed when I started my Linux adventure a few years ago - the Man pages.  The man (or formally, the Linux Programmer's Manual) pages are a collection of informative and descriptive articles about the programs on Linux that will aid you in understand what they are, how they work, and sometimes most importantly, how to use them.  Quite simply they are  the Linux help files.  They are free, come with every Linux distribution and are readily accessible.  To access the manual you need to open up a terminal and type in:

man <item> 

For instance, it may be a good idea to start with the command:

man man

That will tell you in more detail (probably then you care to know) what the man pages are.

For something else it's as easy as something akin to:

man fstab

They are very technical and you'd have to be a masochist to read through most articles in their entirety but nonetheless, a great starting place for people.  Also good is the "info" pages.  Just type in info in the terminal and have at it.  If command line things aren't quite what your looking for, I've found that the Linux introduction tutorials on [http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html) to be extremely informative and the explanation of most things to be superb.

Remember, don't get frustrated (as easy as that sounds) and keep working at it.  If you get an error, put it in quotes and do a search at google.com/linux and see where you go.

---

### Post by stormblue on 2006-08-04
This may seem a bit odd, but one of the best things you can do to learn is get a spare box say 200mhz with 65megs of ram or more, it doesn't really matter, but learn to set up your own server.  If you have no reason to set up a web server, set up Ubuntu Center: Hive.  This will teach you a lot and you won't be fixing a problem on your main machine.

---

### Post by 5-HT on 2006-08-04
The man and info commands XAsmodeanX described are some of the best resources as they pertain to the package versions installed on your system.

Some good sources of Linux information on the web:[LIST]
[*]The Linux Documentation Project: [http://tldp.org/](http://tldp.org/)
[*]Debian's documentation: [http://www.debian.org/doc/](http://www.debian.org/doc/)
[*]Gentoo Wiki: [http://gentoo-wiki.com/Main_Page](http://gentoo-wiki.com/Main_Page)
[*]Ubuntu Wiki: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)[/LIST]While most of the above are not Ubuntu specific, a lot of the information they provide still applies (e.g., file names/locations may be different but the files themselves still serve the same role).  However, some  information may not apply so it would be best to double check these forums or the Ubuntu wiki to find out the 'Ubuntu way of doing things' until you get your bearings. 
Overall though, any information pertaining to Debian should be very similar to Ubuntu.

---

