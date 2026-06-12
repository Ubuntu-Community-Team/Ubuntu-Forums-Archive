---
title: "Linux for number crunchers"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Skip Da Shu on 2007-11-09
For a variety of reasons I am looking at converting some headless number cruncher PCs from Windows.  These "PCs" sole mission in life is to run BOINC, a distributed computing number crunching platform.  

My youngest son (a Gentoo Geek) once help me get 1 running under 64b Gentoo.  But once he was gone I had about 5 commands I could do and most of the time I couldn't find the BOINC config files or TCP/IP settings I might need to fix or tweak something w/o him around.  It became frustrating for me and when somebody wanted an old PIII for a web browser/email machine I reinstalled windows on it and sold it. 

So anyway I am once again motivated to try installing, setting up and getting BOINC to run under a Linux distro.  Hopefully learning enough in the process to actually be able to update and maintain them when needed.  If that leads later to using it as a desktop OS so be it...but it's not part of my current mission.

What I want it to do -  Run 24/7/365 reliably on mildly OC'd machines.  They are 64bit, fairly minimalist, headless machines.  Mostly micro-atx boards with on-board video and lan, 512KB to 1GB memory, Intel and AMD 64 bit CPUs, smallish old IDE drives, RealVNC to access.  No monitor,  CD, floppy keyboard or mouse (unless installing or debugging).  No wireless.  No games.  Worried about missing a couple tools but I'm sure there's something available that'll do the job (CPUZ & coretemp come to mind).

One of the mods on the OverClocking wiki forums has recently been impressed with Ubuntu 7.10.  So I've spent a few hours lurking about here and think this may be the one to try.  

I downloaded and burnt these two to a CD:  gutsy-desktop-amd64.iso  and xubuntu-7.10-alternate-amd64.iso

The "test" machine I'd like to start with is an AMD X2.  I'm gonna yank off the 10GB drive that's on it and plug a blank 10GB drive back in it's place as my "backup" plan.

Yes, I am a Windows person but I do date back to DOS and so command line in and of it self doesn't particularly bother me if there are some command references around.

So, I am here now to ask my first questions:

1) Did I pick the right distro to learn with and run 64bit on fairly minimalist, headless machines? (Didn't feel that Gentoo was really the right animal for me)

2) Anybody got a link that'll walk me thru  how to set my static IPs?

3) Where's a good read on the directory structure Ubuntu uses?


From what little I've gathered here so for it seems ya'll have a good group and mix of folks here.  Hope to be able to join in the fray once I learn to spell Linux right at least 4 out of 5 times ;-)

Thanx in advance, Skip

---

### Post by mikewhatever on 2007-11-09
> So, I am here now to ask my first questions:

1) Did I pick the right distro to learn with and run 64bit on fairly minimalist, headless machines? (Didn't feel that Gentoo was really the right animal for me)

2) Anybody got a link that'll walk me thru how to set my static IPs?

3) Where's a good read on the directory structure Ubuntu uses?


1) Since you seem to have no need for Office and other application included by default, I'd recommend a [Minimal Installation]("http://psychocats.net/ubuntu/minimal").

2) [http://www.sematopia.com/?p=50](http://www.sematopia.com/?p=50)

3) [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
    [http://www.google.co.il/search?q=linux+directory+structure&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.il/search?q=linux+directory+structure&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by Skip Da Shu on 2007-11-10
> **mikewhatever said:**
> 1) Since you seem to have no need for Office and other application included by default, I'd recommend a [Minimal Installation]("http://psychocats.net/ubuntu/minimal").

From the above I downloaded "Ubuntu 7.10 "Gutsy Gibbon" Minimal CD" and burn the .iso to a CD.  Following the directions on that page the first thing it says is to type in "server" at the first prompt.  That returns "Could not find kernel image: server".  

I noticed the screen instructions are also a bit different than in the example.  I'm going to hit ENTER and see what happens.

---

### Post by HermanAB on 2007-11-10
If you are not familiar with Linux yet, then I suggest that you install a standard, but lightweight desktop version, for example Xubuntu, instead of the Server version.

---

### Post by Skip Da Shu on 2007-11-10
> **HermanAB said:**
> If you are not familiar with Linux yet, then I suggest that you install a standard, but lightweight desktop version, for example Xubuntu, instead of the Server version.

Well since "server" didn't work I suspect that's what I'm doing with this "minimal" CD... working on the partitions now... trying to find out if I want to use EXT3 or ReiserFS...  If this bellies up I'll go back to the other live desktop CD or look for Xubuntu.

Right now on my 10GB drive I have:

1) EXT3, 5GB, Primary, root
2)         , 1GB, Logical, swap
3) EXT3, 4GB, Logical, home

This sound about right?

UPDATE... it has installed the base system and ask me what else I wanted... I selected "Xubuntu desktop" and it's off working again.

---

### Post by Skip Da Shu on 2007-11-10
Well this was too easy so far...of course I've broken it already.  I set my IP to static and I've lost connectivity to my lan.

Skip

Restarted and it came back.

---

