---
title: "Region setings/unlock, internet region?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by lumberjack52 on 2008-04-06
I want to watch movies that i have bought in japan on my computer and im told that there is a region lock on my computer, im wondering how i can unlock it or change it somehow to allow the Japanese's region. Im unsure as well how far this goes because i watch movie and music vidoes on crunchyroll.com its a web page that uploads anime and in general media from china korea japan and a few other places as well but since coming to linux gutsy gibon i cant play the videos at crunchyroll and the message says that "Sorry, this video is not available in your region" so im not sure if my computer is causing this problem or my internet connection or what please help thanks

---

### Post by coggins on 2008-04-08
Your DVD drive is probably region locked.  To change the region code you can install regionset (from the universe repo) and run it from the command line.  Be warned that you can only change the region of a drive a few times in many cases.  Check the DVD packaging to determine which region to change it to.
Internet region is a different thing entirely.  They will look at your IP address to determine where you are.  Essentially you have no control over this, other than to migrate ;-)  You could possibly use some sort of proxy service, but that would probably be prohibitively slow for streaming video.
Ya gotta love DRM!

---

### Post by lumberjack52 on 2008-04-08
jake@jakes-laptop:~$ sudo apt-get install regionset
[sudo] password for jake:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  regionset
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 11.5kB of archives.
After unpacking, 73.7kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe regionset 0.1-3 [11.5kB]
Fetched 11.5kB in 1s (8831B/s) 
Selecting previously deselected package regionset.
(Reading database ... 121696 files and directories currently installed.)
Unpacking regionset (from .../regionset_0.1-3_i386.deb) ...
Setting up dansguardian (2.8.0.6-antivirus-6.4.4.1-4) ...
 * Starting DansGuardian dansguardian                                    [fail] 
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error processing dansguardian (--configure):
 subprocess post-installation script returned error exit status 1
Setting up regionset (0.1-3) ...
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

Hmmmmm I dont have a gui for dansguardian and every time i play with dansguardian to try and refine it i break it lol so i have a back up copy but still any ideas how to get around this one?

---

### Post by Dave Otter on 2008-04-08
Japan is the same region as UK so should play

---

