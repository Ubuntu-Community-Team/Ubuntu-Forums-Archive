---
title: "Firefox Broken, can't fix"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by CraftyCathy on 2007-03-09
I am having a probem with Firefox. In the Synaptic Package manager it says I have a broken package.

I am running Ubuntu Dapper Drake 6.06. 

I went to the terminal, this is what happened.

craftycathy@craftycathy:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  helix-player
The following NEW packages will be installed:
  helix-player
0 upgraded, 1 newly installed, 0 to remove and 72 not upgraded.
1 not fully installed or removed.
Need to get 0B/4062kB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 180289 files and directories currently installed.)
Unpacking helix-player (from .../helix-player_1.0.6-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
craftycathy@craftycathy:~$

Won't fix its self. What do I do?

---

### Post by r4ik on 2007-03-09
Try,

synaptic edit fix broken package

good luck !

---

### Post by CraftyCathy on 2007-03-09
This is what I get when I run Synaptic Edit Fix Broken Package.

The following problems were found on your system:

E: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb: trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay

---

### Post by croxi on 2007-05-03
I tried this approach, getting synaptic to fix the broken package but its not done anything, I'm sick of this damned broken pipe, and talking to my ISP to give me a compatible modem won't make my life easier, it'll complicate it exponentially, so I will have to use one of my other PCs to send mail, but its so frustrating to know that I have such a great little OS sitting here at my fingertips, including a host of willing helpers who actually want to fix things. 

Well, no worries, UBUNTU, you're a little difficult to handle at times, but I'm falling in love with you already...big hug!!!

---

### Post by srt4play on 2007-05-03
Try removing the realplay package in synaptic and then telling it to fix broken packages.

---

