---
title: "dvd not working (not for lack of trying)"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Evan Burchard on 2007-07-11
I've followed instructions from various sources, including the ubuntu forums and the ubuntu guide, but to no avail.  I have got this working on other pc's too, so I'm not sure what's different, or what I'm doing wrong.

Computer: Thinkpad Z61m  
OS: Dapper


What I've tried:

sudo apt-get install libdvdread3
sudo apt-get install dpkg-dev fakeroot debhelper # If you have AMD64.  You need dpkg-source.  Otherwise skip.
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install totem-xine
sudo apt-get install libdvdcss2

Also:
Using automatix and EasyUbuntu

Using Xine (error reading nav packet), Gxine (something asking if I was trying to play it without ibdvdcss2), Kaffeine, mplayer, etc.


I was considering the possibility that something might be blocking it... I don't know what, and why, but any ideas along that line of reasoning might be good.
 

Any help would be greatly appreciated,

-Evan

---

### Post by Canis familiaris on 2007-07-11
Have you set the region zone in your DVD?

---

### Post by Canis familiaris on 2007-07-11
If that's the case install the regionset package from Synaptic/apt-get

---

### Post by gn2 on 2007-07-11
Do you know for a fact that the drive is definitely working correctly?

Sometimes a DVD drive will stop reading DVD's but still be OK with CD's.

Tried VLC media player?

---

### Post by Evan Burchard on 2007-07-11
Yeah.  I tried vlc.  It didn't work.  As far as the region, no I never set it, and I never read anything that said I should have to unless I want to play other regions (I know that I only get a few switches before I'm stuck with one region).  

I tried to uninstall players/codecs and reinstall them, and that didn't work.  At this point, I really don't know what to do.  Which installation procedures should I follow?  I know that none of the few that I tried lead to success, but for the sake of going the extra step afterwards.  

Is there any output or error messages that would be useful to anyone?

---

### Post by Evan Burchard on 2007-07-11
BTW, it reads the disk, and shows the title of the movie.

---

### Post by Old Jimma on 2007-07-17
Mine doesn't work, either. Sure would be nice to have it work!

Phil Smith
Duluth, GA

---

### Post by NightFalcon on 2007-07-17
I am having the same problem, while I was following the Help I saw a problem:
Ubuntu Help & Support
5.1.&#8195;Playing DVDs
 2. "sudo /usr/share/doc/libdvdread3/install-css.sh"

checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

I got this error.

Another point is that the libdvdcss doesn't have a 64-bit version in the official website, maybe this is the major problem: 64 incompatibility.

Any ideas? Thank you all.

---

