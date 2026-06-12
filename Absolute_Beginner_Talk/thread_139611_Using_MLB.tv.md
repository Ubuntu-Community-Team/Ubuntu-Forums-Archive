---
title: "Using MLB.tv"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by Duloc on 2006-03-04
I'm trying to watch baseball on ubuntu linux.  I installed realplayer etc.  When I load it up, Mplayer says loading, playing, then stopped and nothing ever happens.  Anyone know what is going wrong?

---

### Post by Duloc on 2006-03-04
I messed around further, uninstalling and reinstalling mplayer and realplayer, and now all I get is a (No Picture) seems I've made things worse.  Any help?

---

### Post by russbuss on 2006-07-01
There have been a few posts about this at the following url:

[http://www.ubuntuforums.org/showthread.php?t=154781&highlight=mlb.tv]("http://www.ubuntuforums.org/showthread.php?t=154781&highlight=mlb.tv")

The basic nuts and bolts are here from prof_booty:

> First, make a back up of your mplayerplug-in.conf that you can use if this breaks anything.

$ sudo cp /etc/mplayerplug-in.conf /etc/mplayerplug-in.conf.bak

then, edit the file to force mplayer to open the video in a new window

$ sudo gedit /etc/mplayerplug-in.conf

find this line:

#noembed=0

change it to

noembed=1

Then go to mlb.tv and log in before clicking on the streams, this seems to be a key step. 

Make sure you notice that you have to remove the "#" before "noembed".  I failed to notice this and it didn't work for me at first.

Hope this helps.

---

