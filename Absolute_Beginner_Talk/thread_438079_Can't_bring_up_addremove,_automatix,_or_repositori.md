---
title: "Can't bring up add/remove, automatix, or repositories"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by alfredeneuman on 2007-05-09
I have been using Ubuntu 6.06 LTS for about 2 months and have been able to manage okay as a total novice as long as I keep it very simple. An issue has emerged recently when I try to bring up the following: 1) add/remove programs off of the application menu, 2) automatix, and 3) repositories in synaptic package manager.

The terminal screen just flashes, giving me barely enough time to read part of the first line about not being able to open and then closes at the same time as the called-up screen. All this happens very quickly.

I've searched the forum and haven't been able to find anything quite like my problem. I have used alt/F2 to bring up alacarte menu but can't add/remove programs with that option. Anyway the problem seems deeper than that and obviously interconnected.I have Firefox 2.0.0.3. Any advice you can give me? Thanks.

---

### Post by Nythain on 2007-05-09
what happens when you type sudo aptitude update in the terminal???

---

### Post by alfredeneuman on 2007-05-09
Thanks. When I put sudo aptitude update in the terminal, I get this:
______

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
______

---

### Post by Nythain on 2007-05-09
nothing that looks like this:
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US
Get:2 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
before???

---

### Post by alfredeneuman on 2007-05-09
Thanks again. Nice links. I followed them and was able to update wine. I went into 'repository how to' and ran this:

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/dapper.list](http://medibuntu.sos-sts.com/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list then sudo apt-get update then apt-get update.

This is what I got:

-10:18:15--  [http://medibuntu.sos-sts.com/sources.list.d/dapper.list](http://medibuntu.sos-sts.com/sources.list.d/dapper.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 88.191.26.58, 88.191.42.241, 88.191.13.100, ...
Connecting to medibuntu.sos-sts.com|88.191.26.58|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 245 [text/plain]

100%[====================================>] 245           --.--K/s

10:18:20 (19.47 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [245/245]
sharon@sharon-desktop:~$ sudo apt-get update
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release.gpg [189B]
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release

Get:2 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release [7232B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper/non-free Sources
Fetched 7421B in 10s (690B/s)
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
sharon@sharon-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)

I didn't know what to do with your last 2 links. Your intervention has resolved the synaptic package update issue, but I still can't bring up add-remove or automatix. Unfortunately, I have to go to work now and will have to look in later.

I appreciate your help.

---

