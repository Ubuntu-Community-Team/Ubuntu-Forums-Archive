---
title: "A hello, and some problems.."
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by Daemon on 2005-08-09
Hello all! I was wondering if you could help me out! 

Tried using the command

$ sudo apt-get update

But when I run it and get to the 'Reading packages list..." I get this error

$W: Conflicting distribution: cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 $Binary-l (20050129) unstable release (expected unstable but got hoary)
$W: You may want to run apt-get update to correct these problems

Also I want to be able to play mp3s while im working... I know enough now to know that mp3 support isnt built in, and its apparently difficult to get it to work(?!) Any help guys?


Thanks!

---

### Post by az on 2005-08-09
You instlled Ubuntu from an unstable experimental cd.  Several cds like this are released throughout the development for debugging.  Just remove that cd from your repository list and do a dist-upgrade (smart upgrade) from the internet.

You need to install gstreamer-ffmpeg to get mp3 support.  It is in universe.

---

### Post by Daemon on 2005-08-09
thank you for the fast response!  :grin:  I've started the distribution upgrade now.. do i just use ...

$sudo apt-get install gstreamer-ffmpeg

...to get gstreamer?


Also, (this is showing how new to linux i am) how do i find out how much disk space is being used/available?

---

### Post by heimo on 2005-08-09
You need to enable universe
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

Package you want to install is[font=Arial][size=1] [size=2]gstreamer0.8-ffmpeg[/size][/size][/font]
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg)

azz will correct me if I'm mistaken

---

### Post by Daemon on 2005-08-10
[QUOTE=heimo]You need to enable universe
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

Package you want to install is[font=Arial][size=1] [size=2]gstreamer0.8-ffmpeg[/size][/size][/font]
[http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg](http://packages.ubuntu.com/hoary/libs/gstreamer0.8-ffmpeg)

azz will correct me if I'm mistaken[/QUOTE]


Nice one  :-)

---

### Post by roland on 2005-08-10
[QUOTE=Daemon]

[...]

Also, (this is showing how new to linux i am) how do i find out how much disk space is being used/available?[/QUOTE]

You can see your disk usage by executing the command [font=courier]df[/font]. This will give a list of disk usage per partition. If you want to know how large a specific directory is, use the command [font=courier]du -s <directory>[/font].

---

