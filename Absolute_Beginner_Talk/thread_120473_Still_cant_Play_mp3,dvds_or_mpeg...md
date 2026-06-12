---
title: "Still cant Play mp3,dvds or mpeg.."
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-01-21
i followed the steps in this link [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)
[restricted formats]
when i type sudo apt-get install  gstreamer0.8-mad 
this is the error i get:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gstreamer0.8-mad

when i type:
 sudo apt-get install  gstreamer0.8-plugins  gstreamer0.8-plugins-multiverse  gstreamer0.8-ffmpeg

this is what i get:

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package gstreamer0.8-plugins has no installation candidate

what do i do....??

---

### Post by Dr Von Bon Bon on 2006-01-21
Hmmm,


You should try opening all of your repositries, that may help.


You can do this by going into synaptic, going into settings, clicking on repositories, go to settings and allow the showing of the disabled software sources.

Click on all of these so they are selected and they may work.



Of course though, the best way to get all the plugins you need is through the wonderful Automatix.

Click here for that:

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


Rock On

---

