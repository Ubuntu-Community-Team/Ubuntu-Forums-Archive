---
title: "Beryl is much EASIER to set up than getting a proper screen resolution &amp; refreshrate"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by tanelt on 2007-05-22
From what I've seen here, most people always say that Beryl, Compiz, etc are alpha/beta software, very unstable and very difficult to install/configure. Well, I followed ubuntuguide.org's instructions and I must say it works **perfectly**. It's perfectly stable, super-simple to set up and provides stunnig eye-candy effects.

Time it took to set it up: about 10 minutes
The number of times I have had problems with it: 0

I have to admit the people who are working on it have REALLY made a great and a stable software, in spite what most people say.


Now, moving on to another subject: changing the screen resolution and refresh rate.

Time it took to set it up: I have never ever managed to get a good screen resolution and refresh rate on ANY linux distro that I've tried in the past 5 years on ANY graphics card  on ANY monitor (all CRT monitors)
The number of times I have had problems with it: 5364795634795675746
The number of times I have asked myself "WHY doesn't it work?!!": 75320572573582735332


If I was a open source developer (which I hope to become one day, because I like the philosophy behind it) and if I had the knowledge about how to code, I would make it my [SIZE="3"]**absolute first priority**[/SIZE] to make sure people new to Linux could at least get their screen resolutions and/or refreshrates working properly, so they would not have to go through all the hell where I've been.

Just my 0.02$

/Edit: please excuse all the typos and grammar mistakes, it's just that I can't look at the screen for a long time, because my eyes start bleeding.

---

### Post by overdrank on 2007-05-22
> **tanelt said:**
>  ANY linux distro that I've tried in the past 5 years on ANY graphics card  on ANY monitor (all CRT monitors)

Just my 0.02$

Hi and this is just my 2 cent. You have been working with linux 5yrs and me 6 months. It took me several times to install beryl and now I have it done pat. I think that is why it is hard to install is peeps like me coming from windose. Dont take this the wrong way I love ubuntu and beryl and I am glad things work for you. :D As for the resolution problem I have no help there sorry!;)

---

### Post by tanelt on 2007-05-22
No, I have not been using Linux for the past 5 years. I've been using WinXP for the past 5 years. And during that time I have tried dozens and dozens of Linux distros and NEVER EVER have got a proper screen resolution and a refresh rate working correctly.

Although I have tried Beryl only once and it works perfectly.

---

### Post by crimesaucer on 2007-05-22
When I first installed Beryl 1.1, things were a lot more difficult then, and I think that is where all of the "unstable Beryl" talk started. 

I use xubuntu with xfce4, and I had to search for a week straight, just to find any directions for xfce4, and when I did, they were wrong, and it was a giant troubleshooting thread with everyone trying different things from different threads and guides for Beryl to work with xubuntu.

I also couldn't find any info on which Beryl to use, and tried to use Beryl xgl since that was the most commonly used one that you would read about, and it broke my beginner install, so I had to start over with a fresh xubuntu reinstall. 

I had followed all of the different threads correctly the first time, it was just xgl would crash my system and I was such a beginner that I would rather just wipe the hard drive, and start over.

If you would of even have seen the first Beryl forum before they had there database hacked and all of the posts lost, you would laugh. So many people with problems and difficult times trying to make it work.

So after the new fresh install of xubuntu, somebody finally made a wiki installation guide for the new Beryl AiGLX that would work with my Intel embedded graphics card and the new xubuntu edgy. 

That guide was a lot easier for a beginner. 

I followed the steps accurately, and had a perfectly working Beryl 1.1 in about 5 minutes, with start_up shell scripts and everything.

So then I had no problems until I felt comfortable enough to try the Beryl 1.5-SVN build. Upgrading was simple, but things were very buggy like a SVN can be.

Anyway, that was also where a lot of the "Unstable" talk came from because of all of the plug-ins that they kept trying. I spent a lot of time on the Beryl forums just trying to fix new things that would break every 3 or 4 days when they tried something new.

It was actually fun, and I learned a lot about Linux from just messing with Beryl.

So around Beryl 2.0-SVN, things began to work smoothly, and I never really had much of a problem since then. 

In fact this Beryl Feisty, is more buggy for me then all of the SVN builds since 1.5 changed to 2.0.

I just can't wait until they release the new merged project.

---

### Post by tanelt on 2007-05-22
When speaking about the resolution and refreshrate, this is me using wind0ze:
[http://xs215.xs.to/xs215/07213/Hammock42343.jpg](http://xs215.xs.to/xs215/07213/Hammock42343.jpg)

And this is me using Linux:
[http://xs215.xs.to/xs215/07213/BleedingEyes4234243.jpg](http://xs215.xs.to/xs215/07213/BleedingEyes4234243.jpg)


That's the ONLY thing that has made me go back to wind0ze every time I have foolishly hoped that I would manage to get it working. :(

---

### Post by powder on 2007-05-22
Perhaps we can help if you copy / paste the contents of /etc/X11/xorg.conf here....?

---

### Post by tanelt on 2007-05-22
[http://ubuntuforums.org/showthread.php?t=444222](http://ubuntuforums.org/showthread.php?t=444222)

---

### Post by jerrylamos on 2007-05-22
Well, I'm a Ubuntu user and what I like to do is try to run pre-Alpha (this is a cobbled together Gutsy 7.10) Alpha, Beta, and on release try to help some of the people who seem to have the same problems (still) I had.

Another Linux version I run is Puppy Linux, CD Live has the best yet persistent mode, and is small enough to run in memory hence fast because of no disk accesses.

During boot, Puppy tries to figure out a bunch of plausible screen resolutions and color depths and presents you with a list.  If you know what you want for resolution, pick that one and that's what you get.  Your fault if you pick one your hardware won't support.  If you want to save the selection, when you shut down you can save files, downloaded packages, setup on a USB pen drive for portability, or on a file on a hard disk (including XP NTFS), or even the rest of the CD/DVD-RW that Puppy came on.  It's open source.

Yes, it doesn't "just work", but sure beats sudo dpkg-reconfigure -phigh xserver-xorg.

Cheers, Jerry

---

### Post by tanelt on 2007-05-22
I don't expect it to "just work".

In wind0ze I encode x264 streams and use vmware to run several OS's simultaneously and a whole lot of other stuff that all require some HEAVY configuration and dedication just to make it work, so I'm well prepared for it.

But right now in Linux I have the entire place full of xorg.conf backup files, tried dozens of modelines and god knows what, JUST to get the darn screen resolution and the refresh rate working.

Don't you think it's a bit ridiculous having to do all of that for such a simple task?

If even I can't do this, do you really expect a person who is new to computers to handle it?
Ready for desktop... yeah right. Having to manually edit xorg.conf in the year 2007 is just retarded.

---

### Post by macogw on 2007-05-22
Well tell us what the graphics card is and what resolution you want already!  We can't help if you don't tell us what's going on.

---

### Post by tanelt on 2007-05-22
> **macogw said:**
> Well tell us what the graphics card is and what resolution you want already!  We can't help if you don't tell us what's going on.

Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=444222](http://ubuntuforums.org/showthread.php?t=444222)

---

### Post by powder on 2007-05-22
Hi tanelt,

I posted this in the other thread by mistake! :)

Sorry for my late reply.  I already know why you can't get 1280x960 working.  It's true, you need a custom modeline to achieve this resolution, but there is currently a regression in the fglrx driver that causes custom modelines to not work.  If you revert fglrx to ver 8.29.6 or use the open source ATI driver you should be able to achieve 1280x960.

P.S. Try this modeline:
```

# V-freq: 120.00 Hz  // h-freq: 124.14 KHz
Modeline "1280x960" 315.80  1280 1440 1824 2544   960  960  965 1034 -hsync +vsync

```

---

### Post by siralphred on 2007-05-22
in my opinion the stability of Beryl depends mainly on the graphic card, but dats just my opinion :)

---

