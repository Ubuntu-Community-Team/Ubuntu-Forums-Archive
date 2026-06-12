---
title: "State of Ubuntu by a common peer part 2"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Redlance on 2006-11-03
well as i stated after my last failed attempt at linux
[http://www.ubuntuforums.org/showthread.php?t=267240]("http://www.ubuntuforums.org/showthread.php?t=267240")

i tried edgy this go around.. got direct rendering and 3d working first try :)
played around a bit. loaded a few games. got the needed codecs going . watched a movie. all smooth sailing only hitch was manually setting monitor resolution to 1280x1024 by editing the xorg.conf (yay! not so noobish 8)  )
unfortunately refresh rate is 47mhz???
:-k 

gonna have to do a forum search and dig up that answer

just thought id drop in and say thanks to the team for a really spiffy job!! Now lets see how long this learning curve is :D

---

### Post by SunnyRabbiera on 2006-11-03
I wish you good luck, as Linux is a learning curve but once you know it you will see how easy it can really be, even easier then windows!
As for the refresh problem I know my refresh rate is stuck, but I think there are things for fixing monitor resolutions and stuff in synaptic.

---

### Post by caravel on 2006-11-03
Download the documentation for your monitor and set the exact refresh rate ranges within xorg.conf.  If you don't you'll get funny refresh rates such as 47Hz or 87Hz

---

### Post by Redlance on 2006-11-03
holy smokes guys 2 min old and 2 posts :D
ok will do ill dig up the specs on the monitor and read howto on the refresh thingy looks like another xorg.conf edit.. appearently just sticking in a resolution is not a 'clean' way to do it :P

---

### Post by bodhi.zazen on 2006-11-03
> **Redlance said:**
> holy smokes guys 2 min old and 2 posts :D
ok will do ill dig up the specs on the monitor and read howto on the refresh thingy looks like another xorg.conf edit.. appearently just sticking in a resolution is not a 'clean' way to do it :P

Here is a brief guide:
[Monitor resolution](http://ubuntuforums.org/showthread.php?t=269052)
There are referances there for further reading.

Here is a sample xorg.conf (with coments). IT DOES NOT APPLY TO YOU it is a sample only:
[xorg.conf](http://darkshed.net/files/rcs/misc/xorg.conf)

---

