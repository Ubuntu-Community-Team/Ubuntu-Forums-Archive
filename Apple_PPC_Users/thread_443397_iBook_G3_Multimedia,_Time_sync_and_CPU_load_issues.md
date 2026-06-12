---
title: "iBook G3: Multimedia, Time sync and CPU load issues"
date: 2007-05-14
forum: Apple PPC Users
---

### Post by Sally on 2007-05-14
Hey there,

I have an iBook G3 and just upgraded to Edgy (and the aim is to upgrade to Feisty later in the week), but I've come up against a few issues since the upgrade:

1. Multimedia, specifically Flash Player -- I followed the instructions under [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ), and have both Gnash and VLC installed, but neither will play downloaded flv files. In fact, I can't get Gnash to run at all, but I do have the latest version installed. VLC will run, but crashes when I try to open flv files.

2. Setting timezones and/or choosing servers to sync with has no affect on the time settings. I can pick my timezone and/or servers, but no changes are applied.

3. Anything I can do to make this less of a CPU hog? I'm using XFCE but the system is VERY slow to respond, so any advice about how to slim things down even more would be great. 

Thank you!

---

### Post by stmiller on 2007-05-14
Only the latest VLC can play flash video files. The VLC version in Edgy must be out of date. :(

How much ram do you have? You could try blackbox (sudo apt-get install blackbox blackbox-themes). It's the fastest of the lightweights. 

As far as the timezones, pick the ubuntu time server only. See if that fixes the problem.

And install the boot-up manager. (sudo apt-get install bum) This will let you disable services that are running which you do not need. (Ex: RAID, ipv6, HP Printer stuff, etc.) Edgy has a lot of crap running all the time by default just to make sure it works on many computers out of the box.


Some other things I do are this:

Edit the file /etc/hosts and comment out the ip6 stuff. Also fix the localhost line so it includes your hostname also. Mine looks like this:

```

127.0.0.1       localhost mahler
127.0.1.1       mahler

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

```

And I disable 3D, b/c that makes my Powerbook slow and buggy. My file /etc/X11/xorg.conf has the line
load dri

commented out like this:

# load dri

---

### Post by Sally on 2007-05-14
Thank you! Time is sync'd and I'm LOVING Blackbox. Will tackle the VLC thing again if/when I upgrade to Feisty.

---

