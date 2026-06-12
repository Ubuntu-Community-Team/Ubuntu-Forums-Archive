---
title: "Must have applications"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by ukulele_ninja on 2007-07-29
So what are some 'Must have' apps and games for Kubuntu? I would really like a good multi-track program as I am a musician and heard there are a lot of good linux programs, anything like pro tools or cubase? Also, just an other general apps that are must haves!

---

### Post by mikewhatever on 2007-07-29
There are no must have applications. You can look in Applications>Add/Remove, read the descriptions and install what you like. You may also be interested in Ubuntu studio. [http://ubuntustudio.org/](http://ubuntustudio.org/)
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty)

---

### Post by ukulele_ninja on 2007-07-29
I went to that link but I got this when I tried to do it, do i need to download something else?

ryan@Ted:~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop
ryan@Ted:~$

---

### Post by ukulele_ninja on 2007-07-29
bump

---

### Post by Nekiruhs on 2007-07-29
Tremulous is an awesome game. Its an RTS FPS combination. its aliens vs humans, you build your base from first person, then defend, attack, expandm and repair all in first person. Its really cool, you buy weapons and upgrads for humans, and evolve as aliens. If you've ever played StarCraft, its sort of like that only a first person shooter.

---

### Post by mikewhatever on 2007-07-29
> **ukulele_ninja said:**
> I went to that link but I got this when I tried to do it, do i need to download something else?

ryan@Ted:~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop
ryan@Ted:~$

Well, you have to follow the instructions from the beginning and not from somewhere in the middle. The package is not found because the repository for the package has not been added.

---

### Post by DM was on fire! on 2007-07-29
> **ukulele_ninja said:**
> I went to that link but I got this when I tried to do it, do i need to download something else?

ryan@Ted:~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop
ryan@Ted:~$

Sounds like it's not in your repositories. :( I unfortunately can't help you, though, but that's what it looks like.

Must-haves...XMMS, Konqueror (if Firefox ever goes on the kafritz), MPlayer, RealPlayer, all of which should be in your repositories.

> sudo apt-get xmms konqueror konqueror-nsplugin mplayer realplayer

I **think**. XD

And last, but not least, if you're a DDR person, I **definitely** suggest StepMania.
You should be able to download the binary file straight from StepMania's site and run it in your home folder. :)

---

### Post by ukulele_ninja on 2007-07-29
> **mikewhatever said:**
> Well, you have to follow the instructions from the beginning and not from somewhere in the middle. The package is not found because the repository for the package has not been added.


Actually I started from the beginning...here:

ryan@Ted:~$ sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
Password:
ryan@Ted:~$ wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add -
OK
ryan@Ted:~$ sudo apt-get update
Get:1 [http://debs.vorian.org](http://debs.vorian.org) feisty Release.gpg [189B]
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/extras Translation-en_US
Get:2 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/deb Translation-en_US
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/http://archive.ubuntustudio.org/ubuntustudio Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/feisty Translation-en_US
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Hit [http://debs.vorian.org](http://debs.vorian.org) feisty Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Err [http://debs.vorian.org](http://debs.vorian.org) feisty Release

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Translation-en_US
Get:7 [http://debs.vorian.org](http://debs.vorian.org) feisty Release [6796B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://debs.vorian.org](http://debs.vorian.org) feisty/extras Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/deb Packages
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/http://archive.ubuntustudio.org/ubuntustudio Packages
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/feisty Packages
Ign [http://debs.vorian.org](http://debs.vorian.org) feisty/main Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/deb Packages
  404 Not Found
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy-amd64 Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/http://archive.ubuntustudio.org/ubuntustudio Packages
  404 Not Found
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/feisty Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Err [http://debs.vorian.org](http://debs.vorian.org) feisty/main Packages
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Sources
Fetched 6991B in 1s (5186B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://debs.vorian.org/dists/feisty/deb/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/deb/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/http://archive.ubuntustudio.org/ubuntustudio/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/http://archive.ubuntustudio.org/ubuntustudio/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/feisty/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/feisty/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://debs.vorian.org/dists/feisty/main/binary-amd64/Packages.gz](http://debs.vorian.org/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://debs.vorian.org](http://debs.vorian.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 20F4742122130E65
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ryan@Ted:~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop
ryan@Ted:~$

---

### Post by nhandler on 2007-07-29
It looks like it isn't in your sources.list correctly. Could you post a copy of that file?

```
sudo cat /etc/apt/sources.list
```

---

### Post by RudolfMDLT on 2007-07-29
sorry for bumping in, in the middle of a fix! :) Remove the comments in front of all the URL's in your sources list and add other sources by hand! :)

Anyway - you might want to look here:

[http://www.getdeb.net/app.php?name=Ardour](http://www.getdeb.net/app.php?name=Ardour)

This site has a couple of cool things!

Also - for KDE - download Super Karamba, it is in the repo's!

Cheers,

Rudolf

---

