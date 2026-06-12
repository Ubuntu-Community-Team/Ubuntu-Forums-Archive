---
title: "w32codecs install walkthrough plzy"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by cramlow on 2005-12-18
Hello & greetings,


I have searched for days on how to play winodws media files.  Totem wont play em, nor kaffieen, nor any other program I have tried to install.  I have tried to follow the unofficial guide to doing the w32codecs install and screwed up my source.list file. 

Please, please....and pleasey help me by way of holding a newbies hand install the w32codes for totem or better yet, kaffeen.  By the way I have a ibook ppc install and not sure that this even matters.  At least I got my frapichino dvd player to finally play! Sheesh!

Thxy!

---

### Post by kaamos on 2005-12-18
[http://ubuntuforums.org/showthread.php?t=79449](http://ubuntuforums.org/showthread.php?t=79449)

And for restoring your sources: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

If you still have problems, post them here. :)

---

### Post by cramlow on 2005-12-18
I got this -

cramlow@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package w32codecs
cramlow@ubuntu:~$

Any advices?

---

### Post by kaamos on 2005-12-18
Aah, the w32codecs package does not exist for powerpc (doh). However I found this package that seems to have the codecs. [http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20051120.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-ppc-20051120.tar.bz2)

Extract it and have a look at the README file. Try copying to codecs to the directories mentioned there. They are outside of your home directory so you need to use this command in terminal```
sudo nautilus
```

They are for mplayer so you might need to use that (not sure). Search synaptic for mplayer.

---

### Post by cramlow on 2005-12-18
I followed but at the end of this I got a couldn't find w32codecs

cramlow@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [25.8kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [582kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [1625B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [8422B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [20.1kB]
Get:15 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages [547B]
Get:16 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages [983B]
Get:17 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources [316B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [2831B]
Get:19 [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources [473B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages [1832B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources [232kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2258kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources [914kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [80.1kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [17.6kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [5088B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [8467B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [23.0kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [14B]
Fetched 4324kB in 39s (109kB/s)
Reading package lists... Done
cramlow@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs

---

### Post by cramlow on 2005-12-18
i am new to this stuff - please tell me how to do this.


Thank you!

---

### Post by prizrak on 2005-12-18
You might want to look for Automatix or Easy Ubuntu (on the easy ubuntu site there is an easy kubuntu link too) I'm not an Apple user so I can't help you too much just the general stuff.

---

