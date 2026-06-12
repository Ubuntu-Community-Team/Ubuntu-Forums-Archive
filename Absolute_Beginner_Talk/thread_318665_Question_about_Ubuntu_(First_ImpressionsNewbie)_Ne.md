---
title: "Question about Ubuntu (First Impressions/Newbie) Need help"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by agx on 2006-12-14
Ok.

So I downloaded 6.10 from work, came home installed it.  Through all my music/songs/certain files on my 250 gig sata lacie hd.  Installed Ubuntu, learned enough about the shell to get my nvidia graphics card updated, learned enough to know how to edit the xorg.conf to allow my 24 inch to be at 1920 x 1200.

Well last night, since I have 6.10 ubuntu, my friend said install automatrix.  Downloaded it, then noticed it was deleting or removing a lot of the Gnome modules.  Oh crap.

Restarted, started up into a orange screen... crap. 

So I am at work.  My question is this, I was downloading automatrix to install some apps.

How in the hell do you install Deluge.  I got it of the repo, but then it said I needed python-libtorrent , so I downloaded it.  I am un familiar since it looks like source code, but has a "makeit" and "installit" also a "debianit"  the readme doesn't explain anything.  Is their a certain folder I need to put the source in for it to install?

When I get home I am going to reinstall 6.10 and start over.  No more automatrix.

I need the best video program, music player, a thing to put ipod video/music on ipod, a converter to make .avi(xvid,divx,etc) into ipod video format.  

Thanks for the help!

---

### Post by scrooge_74 on 2006-12-14
This is only muy opinion on how to do things.  I started using DEBIAN about 10 months ago and just recently switch to UBUNTU. I do all my installing and updates either from command line using apt or from inside GNOME using Synaptics.  Enable all repositories for different types of packages (Multiverse, Universe, etc)

I use TOTEM plus downloading and installing (using synaptics) all codecs I need (I few things still don't play but I don't care), for music I use XMMS (and I install what ever I need for it)

Currently TOTEM plays any AVI file a I have, only have problems with Real Media FIles because I have not installed the requiere codecs or what ever.

I am not familiar with DELUGE which I did not find in the repos for packge, you found it with the source repositories?

But for torrents I just find any I like click on it and let the default one in GNOME do the job. So far it has done the job for me

---

### Post by mykalreborn on 2006-12-14
i don't know what happened with automatix. i've used it so many times, but nothing bad happened - except installing "bad" codecs :p-
if you want a good music player, you should use amarok. it's the best by far. you should see it in applications>add remove programs... it has library, lastfm player support, ipod support and much more.
about the best video player. you should get mplayer[(link)]("http://www.mplayerhq.hu/design7/info.html"). it's a little tricky to install, at least for me, bacause i have an ati card and the driver didn't work. but since you say you have nvidia it should work with no problem.
unfortunately i don't know of any programs for transforming into ipod format, but i'm sure there are numerous choices. just search these forums.
oh... and since you managed to configure your nvidia driver, i guess you're not a newbie any more ;)

---

### Post by agx on 2006-12-14
Ok what is synaptics?

I also tried double clicking the .torrent, and nothing happened.  So I guess I needed a torrent client.

---

### Post by scrooge_74 on 2006-12-14
> **agx said:**
> Ok what is synaptics?

I also tried double clicking the .torrent, and nothing happened.  So I guess I needed a torrent client.

Look in >System>Administration>Package Mananger Synaptic

It will become your best friend very soon.

I learn that when I click on a torrent file, I tell Firefox to download the file or choose the default torrent manager.

When I have the torrent file in a folder I click on it and the default torrent will go to work and continue the download

---

### Post by mykalreborn on 2006-12-14
> **agx said:**
> Ok what is synaptics?

I also tried double clicking the .torrent, and nothing happened.  So I guess I needed a torrent client.

synaptics is the package manager for ubuntu. you find it in system>administration.
it takes a long time to explain how to use it. the main idea is that it contains data about software you can install in your ubuntu machine.
also, a good torrent client would be azureus [(link)]("http://azureus.sourceforge.net/")
unfortunately i don't think it's that easy to install it. try it and if you get any problems post it here.

---

### Post by gunksta on 2006-12-14
I don't know when it will hit the repos, but according to this

[https://launchpad.net/products/edgy-backports/+bug/75018](https://launchpad.net/products/edgy-backports/+bug/75018)

Deluge will be backported to Edgy.

This means that one of the developers is going to repackage it and let you install it via Synaptic.

The previous comment sad synaptic is hard to use. I would disagree. I think it's a snap to use. The selection can be a little overwhelming, but it's not hard to use.

--andy

---

### Post by mykalreborn on 2006-12-14
> **gunksta said:**
> I don't know when it will hit the repos, but according to this

[https://launchpad.net/products/edgy-backports/+bug/75018](https://launchpad.net/products/edgy-backports/+bug/75018)

Deluge will be backported to Edgy.

This means that one of the developers is going to repackage it and let you install it via Synaptic.

The previous comment sad synaptic is hard to use. I would disagree. I think it's a snap to use. The selection can be a little overwhelming, but it's not hard to use.

--andy

yeah. i guess you're right. it is easy to use. mustn't have paid attention to what i was writing :D

---

### Post by mcduck on 2006-12-14
Seems like this is one more thread where this link is needed: ;)

[How to install *ANYTHING* in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Rodneyck on 2006-12-14
You can also try Exaile music player, my fav.  It has ipod support...

[http://www.exaile.org/](http://www.exaile.org/)

---

