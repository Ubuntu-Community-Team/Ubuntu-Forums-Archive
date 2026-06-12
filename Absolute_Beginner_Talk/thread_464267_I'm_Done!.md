---
title: "I'm Done!"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by spookyct on 2007-06-04
:mad:

Let me start by saying, I'm done with Windows!  Now I just have a few questions...

My current setup has 2 Hard disks...  One is partitioned NTFS it contains all of my media (120 GB).  My second disk is partitioned 40 GB NTFS (Media),  10 GB Ubuntu, 15 GB NTFS My Windows Partiton.

- s there a way that I can format that 15GB NTFS to something that I can write to with Ubuntu?  Is there a way to write to my other NTFS disks (right now I can only read from them)?

- How in the world do you get media to play in Firefox? Like streaming video in wmv, mov, avi format?  I have downloaded VLC and MPlayer...  can't get them to work with Firefox (most recent version)

- Are there any linux programs out there that are equivalent to DVD Shrink and Nero for DVD burning?

Thanks for your help.

---

### Post by steeleyuk on 2007-06-04
For NTFS write ability you'll need to do:

sudo apt-get install ntfs-3g

To play restricted media formats, see this page:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

IMO the best burning programs I have come across are Brasero and GnomeBaker.

---

### Post by forestpixie on 2007-06-04
Not sure about Brasero but I use k3b - but there are a lot of apps out there.

---

### Post by starcraft.man on 2007-06-04
> **spookyct said:**
> :mad:

Let me start by saying, I'm done with Windows!  Now I just have a few questions...

My current setup has 2 Hard disks...  One is partitioned NTFS it contains all of my media (120 GB).  My second disk is partitioned 40 GB NTFS (Media),  10 GB Ubuntu, 15 GB NTFS My Windows Partiton.

- s there a way that I can format that 15GB NTFS to something that I can write to with Ubuntu?  Is there a way to write to my other NTFS disks (right now I can only read from them)?

[COLOR="Red"]To Format the 15 GB NTFS you have multiple options, you can make it into a seperate partion or merge it into an existing. All options can be done with [GPartedLiveCD.]("http://gparted.sourceforge.net/livecd.php") My favorite partitioner, its very good and free.[/COLOR]

[COLOR="Red"]To write to the other NTFS drives you need NTFS-3g drivers and need to configure it up right. I think this [should get ya through the set up for Feisty]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html"). :)[/COLOR]

- How in the world do you get media to play in Firefox? Like streaming video in wmv, mov, avi format?  I have downloaded VLC and MPlayer...  can't get them to work with Firefox (most recent version)

[COLOR="Red"][This plugin]("https://addons.mozilla.org/en-US/firefox/addon/446") really should be standard for the next release of firefox. You can then run the configuration utility and stream to any player installed on your computer.

To add all the codecs to Totem, [please follow this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs"). Please pay careful attention to notes under title, you do need the extra repositories to get them, follow the link and you will be guided through that as well. VLC of course has playback for almost all of these out of box, so use that if ya like but its still a good idea to install codecs, some programs use totem always.[/COLOR]

- Are there any linux programs out there that are equivalent to DVD Shrink and Nero for DVD burning?
[COLOR="Red"]
For burning, I recommend k3b and Gnomebaker. For DVD movie transcoding look at devede. For DVD Shrink, I think there is handbrake and a few other alternatives. They can all be found on [linuxappfinder]("http://linuxappfinder.com/windows?page=1") the windows alternatives section will let you find alts for any app in windows. Alternatively you can browse the directory from main page.[/COLOR]

Thanks for your help.

Your welcome, all my answers in red. Have fun with Ubuntu :D.

Oh and consult [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for all your learning needs, they explain a lot of things/commands to get ya started. Oh and, [psychocats]("http://www.psychocats.net/ubuntu/") is another good resource, a bit more guided and explained than ubuntuguide.

---

### Post by kelvin spratt on 2007-06-04
I would use ntfs 3g for read write to your ntfs partitions if you get any problems download Automatix and use there version as it works superb.

---

### Post by Zoolie on 2007-06-04
For DVDShrink try this : [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)
its dvdshrink for linux

---

