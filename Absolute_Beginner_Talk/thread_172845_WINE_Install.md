---
title: "WINE Install"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-09
I'm using the book "Beginning Linux Ubuntu" to install Wine, but I've run into a dead end.  After downloading Sidenet, the next step is supposed to be to download three programs;  DCOM98, Windows Installer add-in (releaseid=32831), and MFC4.0 Runtime.  No problem with DCOM98; however, the Windows installer add-in does not exist at M$, as directed, nor does the MFC 4.0 Runtime url.  I haved Googled them both and had no luck.  I have found a download of MFC 8.0, but I have no idea if that will work or not.  I need help, please. Thanks.

---

### Post by mjm115 on 2006-05-09
You can get the 4.2 version from [here]("http://www.winsite.com/bin/Info?500000023982").

---

### Post by Guns90 on 2006-05-09
Thanks mjm115, I have it.  Now if I can just find someone who understands what that Windows installer add-in is all about.

---

### Post by Guns90 on 2006-05-09
My knowlege of Linux is appalling.  I initially tried to install wine using the wiki.  I was doing fine until I got to the point of where it said...
Running Windows programs/installers

To run most programs or installers, type wine name_of_program.exe

Configuring specific Windows programs
Adding applications to the menu

To add a Desktop launcher to the menu, you need to find out where in the pseudo-C drive the program exists.

I don't understand a few things here:  Is this referring to programs actually loaded onto the hard drive already?  
    a.  If it is, then the only windows program I know of on the hard drive is IE6 and what comes along with that.  The problem there is I can't figure out the path to it.  The wiki instruction above said, "you need to find out where in the pseudo-c drive the program exists.  How do I do that?
    b.  If it isn't, I've tried to install a couple of windows programs from the cd-rom, but that doesn't work either.  My way of thinking is that I have to use the command line and do something like first creating a directory, accessing that directory, then 'wine  install ###.###'.  

I really feel stupid right now.  If someone can't answer my previous post, but answer this one, I'd go back to the original installation process, remove wine, and try it the Wiki way again.

---

### Post by mjm115 on 2006-05-17
You can also try:

[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

---

### Post by helphope on 2006-05-17
I know what I'm asking is a bit off-topic, but by the way I don't understand in what sense  wine gives  me the chance to run a windows program, whether without installing it or installing it, but where in a total linux pc?:confused:

---

