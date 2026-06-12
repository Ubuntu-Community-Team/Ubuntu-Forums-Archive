---
title: "Real Player"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by geovino on 2006-10-30
I have tried many times to install Real Player and I still can't get it to work. Can someone please explain what needs to be done. I have gone in the to ask before and nothing has worked. It should not be hard to install.

When trying to install in Synaptic I get this error:

realplayer:
 Depends: xlibs  but it is not installable

What do I do?

---

### Post by Iarwain ben-adar on 2006-10-30
Hi,
did you try to install from the repo's?

```
sudo aptitude install realplayer
```


Iarwain

---

### Post by geovino on 2006-10-30
This is what I get:

davek@davek-desktop:~$ sudo aptitude install realplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  realplayer
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.5kB of archives. After unpacking 213kB will be used.
The following packages have unmet dependencies:
  realplayer: Depends: xlibs which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
davek@davek-desktop:~$

what do I do?

---

### Post by Perfect Storm on 2006-10-30
```
sudo aptitude -f install realplayer
```

But realplayer is old. Instead grab the commercial source for Ubuntu and install "realplay" (version 10 gold).

Or better yet let mplayer handle all the realplayer stuff.

---

### Post by geovino on 2006-10-30
How do I get mplayer to play the real player files?

I tried your command and realplayer is broken. 

right now i'm installing kmplayer. maybe that will work

---

### Post by Perfect Storm on 2006-10-30
Install mozilla-mplayer

```
sudo aptitude install mozilla-mplayer
```

---

### Post by geovino on 2006-10-30
Thanks, I installed that, but when I play this one file I only get audio, no video.

why?

Also some video ask for flash. where can I install that? synaptic?

---

### Post by Perfect Storm on 2006-10-30
Make sure you have installed w32codecs

---

### Post by geovino on 2006-10-30
I installed it. thanks. hope this helps.

---

### Post by Perfect Storm on 2006-10-30
Because w32codecs aren't free. If Ubuntu should put them on the CD we have to pay for it. Also w32codecs contains alot of close source formats.

Check here to get it: [http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

---

### Post by geovino on 2006-10-30
I see, I was able to install it. Now mplayer works! Thank you!

What about flash? how do I install it?

---

### Post by Marsolin on 2006-10-30
In case you aren't aware, the commercial repository that contains [RealPlayer 10]("http://linuxappfinder.com/package/realplayer") is located [here]("http://archive.canonical.com/ubuntu/").

---

### Post by Marsolin on 2006-10-30
> **geovino said:**
> What about flash? how do I install it?

sudo apt-get install flashplugin-nonfree

---

### Post by Perfect Storm on 2006-10-30
Ubuntu philosophy, geovino. [http://www.ubuntu.com/ubuntu/philosophy?highlight=%28philosophy%29](http://www.ubuntu.com/ubuntu/philosophy?highlight=%28philosophy%29)

---

### Post by fishpie on 2006-10-30
to install flash

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by geovino on 2006-10-30
> **Marsolin said:**
> In case you aren't aware, the commercial repository that contains [RealPlayer 10]("http://linuxappfinder.com/package/realplayer") is located [here]("http://archive.canonical.com/ubuntu/").

It said error denpency is not satisfiable: xlibs 

How do I fix that problem?

---

### Post by Marsolin on 2006-10-30
Have you tried installing realplay instead of realplayer?

---

### Post by geovino on 2006-10-31
Realplay wasn't listed in Synaptic, only Real Player. where would it be?

---

### Post by Marsolin on 2006-10-31
You need to add the following line to your sources.list file. You can also type it into Synaptic if that is easier for you. See [here]("http://linuxappfinder.com/addrepo") for a demonstration.

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

If you have already upgraded to Edgy just replace dapper with edgy in that line.

---

### Post by geovino on 2006-10-31
Thanks, I added the line to my sources.list But when I hit reload in Synaptic I got this error:

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

Where do I get the public key?

Maybe it doesn't matter. I was able to install RealPlayer 10! Yeah!

Oops! spoke too soon, I tried playing something in Real Player but I only got audio, but no video. And when I try to play a ram file I get the mplayer instead. where do I go to change it? 

And how do I get Real Player to play audio and video?

---

### Post by wpshooter on 2006-11-25
> **Artificial Intelligence said:**
> Because w32codecs aren't free. If Ubuntu should put them on the CD we have to pay for it. Also w32codecs contains alot of close source formats.

Check here to get it: [http://doc.ubuntu-fr.org/doc/plf](http://doc.ubuntu-fr.org/doc/plf)

I can not even read what is displayed on this page ???

---

### Post by 3kravinarayan on 2006-12-13
i have real player installed but have the following issues

1 it does not play vcd and avi files. also does not play rtsp streams

when i click on say bbc radio, totem layer coems on line and i cannot choose real player

help pl

Ravi

---

### Post by Perfect Storm on 2006-12-13
> **3kravinarayan said:**
> i have real player installed but have the following issues

1 it does not play vcd and avi files. also does not play rtsp streams

when i click on say bbc radio, totem layer coems on line and i cannot choose real player

help pl

Ravi

Uninstall totem mozilla plugin, then install mplayer and mplayer mozilla plugin and w32codecs and you're rolling.

Also check: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by funsnail on 2006-12-13
> **Marsolin said:**
> You need to add the following line to your sources.list file. You can also type it into Synaptic if that is easier for you. See [here]("http://linuxappfinder.com/addrepo") for a demonstration.

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

If you have already upgraded to Edgy just replace dapper with edgy in that line.

This repository doesn't seem to contain anything for Edgy. I am unable to find anything in it.

---

### Post by funsnail on 2006-12-13
> **Artificial Intelligence said:**
> Uninstall totem mozilla plugin, then install mplayer and mplayer mozilla plugin and w32codecs and you're rolling.

Also check: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Under Edgy if you try to uinstall totem-mozilla plugin it also wants to uninstall ubuntu-desktop.

---

### Post by Perfect Storm on 2006-12-13
Doesn't really matter. Just install ubuntu-desktop if you gonna make a dist-upgrade in the future. It's a meta-package.

---

### Post by funsnail on 2006-12-13
> **Artificial Intelligence said:**
> Doesn't really matter. Just install ubuntu-desktop if you gonna make a dist-upgrade in the future. It's a meta-package.
I don't understand what you just said.

---

### Post by Perfect Storm on 2006-12-13
It means it's safe to uninstall ubuntu-desktop package, but you need ubuntu-desktop package if you want to dist-upgrade (upgrading like ubuntu 6.10 to ubuntu 7.04)

---

### Post by 3kravinarayan on 2006-12-14
Thanks to Artificial Intelligence am rolling.  

Cheers

Ravi

I did just what you said, installed w32codecs

---

