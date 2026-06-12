---
title: "Ubuntu on an old computer"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Holmgreen on 2006-06-30
I have Ubuntu running on two machines at home. One is running smooth and without problems (Dapper Drake). I love my Ubuntu, and that's why i choosed to install it on my server as well, but i found that to be a whole different story.

Unfortunately it's a rather old computer. PII 450mHz with 128MB RAM.
For you to understand my needs better, i'll like to explain the purpose of this computer:

It's running 24/7 in our kitchen, where it mainly serves as fileserver and jukebox. My family uses it for netradio and as a client to play our MP3 collection. It contains 3 hard drives: One 10GB drive for OS. One 60GB drive for music and pictures, and one 150GB drive i use as a central storage for all files in the house.

Well... first i tried to install Ubuntu out of the box on this computer. Very quickly i recognized that this was way too heavy for this poor old buddy of mine. Then i tried Xubuntu - and that helped a little, but not at all enough. The computer is still extremely slow and simple tasks as open a web browser   or a media player is a pain.

I've been reading a bit about DamnSmallLinux, Slackware and such to find an alternative, but firstly (and mostly) i find Ubuntu to be the single best Distro to suit me, and secondly i'm not at all skilled in the use of Linux. I like Ubuntu for being so user friendly and i fear Slackware for not being so.

Ok - here's my question:
Can i get any tips on how to tweak Xubuntu to fit my old computer? Any applications i should avoid (i guess OpenOffice is a good place to start), and what are the alternatives then? 

I was i bit surprised that the xfce windowsmanager didn't help more than it did. Is there there an even more lightweight one to get running on Ubuntu?

Thanks in advance ;-)

---

### Post by cowley on 2006-06-30
there is a ubuntu server dist i think though i know nothing about it or how to use it.  maybe this would be worth looking into

simon

---

### Post by cowley on 2006-06-30
[QUOTE=cowley]there is a ubuntu server dist i think though i know nothing about it or how to use it.  maybe this would be worth looking into

simon[/QUOTE]

just seen this thread - maybe useful to you

[http://ubuntuforums.org/showthread.php?t=206093](http://ubuntuforums.org/showthread.php?t=206093)

---

### Post by Jagot on 2006-06-30
Not sure if it's possible to tweak XFCE any more but you could possibly use a more lightweight window manager.  You may want to have an experiment with these:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Holmgreen on 2006-06-30
Thanks a lot for the quick answers.
Since this computer also is used by my family members, i have to have a windows manager. My wife makes funny noises when she see a command line:roll: 

I've checked out the documentation on installation on low memory systems, and it surely looks like the answer to me. Also IceWM looks like something i could use.

But... do anyone know the big differences between putting IceWM on a regular Ubuntu compared to adding it to a server version?
If i could avoid reinstalling everything and just adding the new windows manager it would be a great relief.

---

### Post by cowley on 2006-06-30
i cant see that being a problem, you could then at login select which session you would like to use, and make which ever the default

simon

---

### Post by Jagot on 2006-06-30
As cowley says, there shouldn't really be any problem with that, but you may get better performance if you through the server install route first as with the current installation you'll have a lot of files which will be redundant and thus may cause a slight performance hit.  I can't honestly say whether that performance hit would justify doing a whole reinstall.  You may want to look at the bottom of this page:

[http://psychocats.net/ubuntu/puregnome.php](http://psychocats.net/ubuntu/puregnome.php)

It details the command you'd need to completely get rid of Xubuntu, so if you go over to another window manager you can get rid of some of the component programs which will be redundant.

---

### Post by Holmgreen on 2006-06-30
Thanks a lot for all your help.
I'll try to install IceWM on my current ubuntu. If it's not good enough i'll give the server version a try.

I might be able to keep my Ubuntu and the sun is shining - what an excellent day :D

---

