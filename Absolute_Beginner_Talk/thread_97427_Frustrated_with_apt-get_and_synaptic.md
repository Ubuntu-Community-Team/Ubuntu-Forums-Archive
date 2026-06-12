---
title: "Frustrated with apt-get and synaptic"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-12-01
I posted on this yesterday as well.

Here's my current sources.list file, which I got from [source-o-matic]("http://www.ubuntulinux.nl/source-o-matic").  (For the record, I've gone through several source.list's in the last few days trying to work this out.  My gratitude to the folks who tried to help me through this yesterday.)

[QUOTE=]# Ubuntu community supported packages (sources)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages)
deb [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources)
deb-src [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# Bleeding edge wine packages (packages)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Bleeding edge wine packages (sources)
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
[/QUOTE]

I'm still getting these.

> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
--
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://wine.sourceforge.net/apt/binary/Release.gpg:](http://wine.sourceforge.net/apt/binary/Release.gpg:) Could not connect to wine.sourceforge.net:80 (1.0.0.0), connection timed out
[http://wine.sourceforge.net/apt/source/Release.gpg:](http://wine.sourceforge.net/apt/source/Release.gpg:) Could not connect to wine.sourceforge.net:80 (1.0.0.0), connection timed out

And that's about all I know.  Someone yesterday offered the idea that it may be my network settings, and yet Firefox works.  Any thoughts on this?

---

### Post by aysiu on 2005-12-01
I can't say I'm a big fan of the sources you have in your sources.list, but that's not the problem.

The timeout thing, from what I've seen in other posts, has to do with proxy settings or firewall settings. I don't know much about that stuff, though. Someone else?

---

### Post by Murgle on 2005-12-01
Try removing the us. in front of all your sources, I recall this was a common problem right around when breezy came out.  Also have you had this problem for a couple days?  For some people the problem just dissapeared after a day or so.

---

### Post by TeeAhr1 on 2005-12-01
[QUOTE="aysiu"]I can't say I'm a big fan of the sources you have in your sources.list...[/QUOTE]

How so?  Full disclosure, I didn't even know what a sources.list file was until two days ago.  Any critique/advice would be accepted most graciously.

[QUOTE="murgle"]Try removing the us. in front of all your sources, I recall this was a common problem right around when breezy came out. Also have you had this problem for a couple days? For some people the problem just dissapeared after a day or so.[/QUOTE]

It's been...well, more than sporadic, but sometimes I'd get through just fine.  I did remove the "us" from the sources of the original (installed) sources.list file on someone else's advice last night, which seemed to help.  After a couple of tries, Synaptic did connect, and all was well for a little while, and then it popped up again.

Let me try this again, though.

[I]moments later...[I]

Okay, now it's just these ones.

> [http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg:](http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg:) Could not connect to seveas.ubuntulinux.nl:80 (1.0.0.0), connection timed out
[http://wine.sourceforge.net/apt/binary/Release.gpg:](http://wine.sourceforge.net/apt/binary/Release.gpg:) Could not connect to wine.sourceforge.net:80 (1.0.0.0), connection timed out
[http://wine.sourceforge.net/apt/source/Release.gpg:](http://wine.sourceforge.net/apt/source/Release.gpg:) Could not connect to wine.sourceforge.net:80 (1.0.0.0), connection timed out
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to ftp.free.fr:21 (1.0.0.0), connection timed out

...but browsing through, there's nothing there!  All Synaptic lists is what's already installed.  WTF?

---

### Post by aysiu on 2005-12-01
The only way I can know whether it's a proxy/firewall/network configuration thing or the sources.list being bad is if you have what I consider a proper sources.list.

Follow the instructions in the first link in my sig--they include a command for backing up your current list (so it won't be lost). Then, see if you still get the timeout error.

With that sources.list from my sig, I just did an update a few seconds ago: ```
sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:6 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 59.4kB in 1s (30.6kB/s)
Reading package lists... Done
```

---

### Post by TeeAhr1 on 2005-12-01
Okay, your list seems to work in both Synaptic and the command line.  Until proven otherwise, I'm going to assume that it was my list that was bad and not my connection settings.  As always, Aysiu, thanks for your help.

-pete

---

