---
title: "Mplayer problems"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-04
I am having troubles installing mplayer.  When I sudo apt-get install mplayer, I get this:

wesley@wesley-laptop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
wesley@wesley-laptop:~$

---

### Post by taurus on 2006-11-04
I am not sure but I don't think mplayer is available from regular repos.  Therefore, you should install automatix2 and use it to install mplayer and codecs.  Don't forget to install the codecs or you won't be able to play anything in Ubuntu...

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

### Post by CatKiller on 2006-11-04
Alternatively, you could just [enable the Universe and Multiverse repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") in Synaptic.

---

### Post by ferd on 2006-11-06
I have this mplayer problem. I used synaptic to uninstall and tried to use automatix2 to install but the install fails. There is an unresolvable dependency at this time, I believe this started on 5Nov. I will wait for a resolution.
I found a solution that worked for me. I opened synaptic and checked the repos that were listed as in the fault box that opened when I tried to install packages. I eliminated those repos. I was then able to download and install a working mplayer and plugins. I am using Dapper.

---

