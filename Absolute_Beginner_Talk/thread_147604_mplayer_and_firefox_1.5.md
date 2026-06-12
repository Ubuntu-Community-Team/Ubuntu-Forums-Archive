---
title: "mplayer and firefox 1.5"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Tawler on 2006-03-20
Hey, sorry if I sound dumb... be patient I want to really like this linux stuff, and so far I do!

Anyway, I've come a ways in this past week.  I got a partition, I got ubuntu, I got 855resolution, I got xfce, and I just got firefox 1.5.  This command line stuff is, strangely, lots of fun.  Reminds me of when I was young and dos still reigned.  But not I'm stuck.  I can't seem to get mplayer installed.  Whenever I try an apt-get on it I get this...

 >  mplayer: Depends: libartsc0 (>= 1.4.3-1) but 1.4.3-0ubuntu1 is to be installed
           Depends: libasound2 (> 1.0.10) but 1.0.9-2 is to be installed
           Depends: libcairo2 (>= 1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
           Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libfribidi0 (>= 0.10.7-1) but 0.10.5-2 is to be installed
           Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
           Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed
           Depends: libglib2.0-0 (>= 2.9.3) but 2.8.3-0ubuntu1 is to be installed
           Depends: liblame0 (>= 3.96.1-1) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libogg0 (>= 1.1.3) but 1.1.2-1 is to be installed
           Depends: libpango1.0-0 (>= 1.11.6) but 1.10.1-0ubuntu1 is to be installed
           Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
           Depends: libvorbis0a (>= 1.1.2) but 1.1.0-1ubuntu1 is to be installed
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: libxvmc1 but it is not going to be installed
           Depends: mplayer-skins but it is not installable
W: Couldn't stat source package list [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/si.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Yeah... I'm dumb.  Can someone help?

---

### Post by LordBug on 2006-03-20
> W: You may want to run apt-get update to correct these problems


Have you tried that yet?

---

### Post by KansasJoe on 2006-03-20
I have a lot better luck with mplayer when i compile and install it because you know you have the correct codecs and everything and you learn a lot and you can change the skin and fonts (you can probably do this if you apt-get it also) but you'll learn more by compiling.

---

### Post by Tawler on 2006-03-20
Thanks for the comments, I did try apt-get update and I still had the same issues.

I'll have to figure this compile business out it seems.

---

### Post by KansasJoe on 2006-03-20
Download sources, codecs, fonts and skins from here [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html) 

the instructions are here [http://www.mplayerhq.hu/DOCS/README](http://www.mplayerhq.hu/DOCS/README)

make sure when you configure you type in
./configure --enable-gui 

and not just ./configure or you won't be able to use it on gui

if you haven't already you will need to 

sudo apt-get install build-essential

if it says you're missing something then just dl it from apt-get or synaptic

---

### Post by Tawler on 2006-03-20
Well I got it up and working, but when it's streaming a video off a web site it's really choppy.  Is this par for the course or am I goofin up somewhere?  Probably the latter...

---

### Post by reubadoob on 2006-04-27
I've noticed the choppiness also. Anyone have any suggestions?

---

