---
title: "[SOLVED] Update manager problems"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by itix on 2008-01-06
My Update Manager is acting all wierd. I have quite recently formatted my HD to Ubuntu-only with Feisty since the install is more stable (I get these really big fonts in the window top bars with gutsy). I thereafter tried to update to gutsy as usual, but when i was downloading the updates for feisty I lost connection with the DNS and it all went out of control. 

I later (after yelling at my ISP for an hour or so) resumed my updating and it all went ok until the update was complete and the UM said that some of the packages couldn't be found. I tried to check for new updates to see if i could try again with the unsuccessful packages and it started saying that it: "Could not download all repository indexes". I have tried almost everything; reinstalling the UM, force updating to Gutsy. It's the same thing with synaptic when I try updating with it instead.

---

### Post by taurus on 2008-01-06
Can you run these two commands from a terminal and post the outputs here?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by itix on 2008-01-06
Update:
```

itix@itix-laptop:~$ sudo apt-get update
Get:1 http://se.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://se.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://se.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://se.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://se.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://se.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://se.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://se.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://se.archive.ubuntu.com feisty Release       
Hit http://se.archive.ubuntu.com feisty-updates Release
Ign http://se.archive.ubuntu.com feisty/main Packages               
Hit http://se.archive.ubuntu.com feisty/restricted Packages
Hit http://se.archive.ubuntu.com feisty/main Sources
Hit http://se.archive.ubuntu.com feisty/restricted Sources
Hit http://se.archive.ubuntu.com feisty/universe Packages
Hit http://se.archive.ubuntu.com feisty/universe Sources
Hit http://se.archive.ubuntu.com feisty/multiverse Packages
Hit http://se.archive.ubuntu.com feisty/multiverse Sources
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Hit http://se.archive.ubuntu.com feisty-updates/main Packages
Hit http://se.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://se.archive.ubuntu.com feisty-updates/main Sources
Hit http://se.archive.ubuntu.com feisty-updates/restricted Sources
Get:4 http://se.archive.ubuntu.com feisty/main Packages [1307kB]
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
99% [Working]                                  
gzip: stdin: not in gzip format
Err http://se.archive.ubuntu.com feisty/main Packages
  Sub-process gzip returned an error code (1)
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 4B in 0s (11B/s) 
Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Upgrade:
```

itix@itix-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by taurus on 2008-01-06
Maybe the mirror site, se.archive.ubuntu.com, is down.  Go into synaptic (Settings -> Repositories) and change to another site.  See if that fixes the problem.

---

### Post by itix on 2008-01-06
wohooo. Thanx. Internet sure is a strange thing...

---

