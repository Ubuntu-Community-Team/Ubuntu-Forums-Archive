---
title: "Error message on bootup"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Spaniard on 2007-05-06
I've spent quite a lot of time checking my hardware making sure everything is working properly on my machine.  Specs are 3.60 Intel P4 CPU, 250 Maxtor SATA Hard Drive, 2 Gigs Ram, Nvidia Geforce 6600 with 512 MB Ram on an ASUS P5GD1 motherboard.

Also; I've burned Feisty to a CD at 4X; I've checked the Image File before Burning with WinMD5Sum, and I did the CD Check on another machine and its good.

Every time I put the Feist CD in this machine and try and boot it this error comes up after the program loader starts:

Busybox v1.1.3 (Debian 1:1.1.3-3 ubuntu3) Built-in shell (ash)
Enter' help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)-

---

### Post by teddybairs1 on 2007-05-06
Two questions:

1)Where did you get your .iso from?
2)Have you tried burning a second disk onto a different cd-r, preferably not from the same batch you got the first one?

It has nothing to do with your hardware. The disk itself is bad it sounds like. Another possibility is to request a disk from the shipit service through the Ubuntu website.

One way to check if it is the disk is to try it on another machine with different specs. If it works, it's your machine, if it does the same thing, it's the disk.

One more question, are you using the Desktop Install CD or the Alternate Install CD?

---

### Post by Spaniard on 2007-05-06
)Where did you get your .iso from?
2)Have you tried burning a second disk onto a different cd-r, preferably not from the same batch you got the first one?

It has nothing to do with your hardware. The disk itself is bad it sounds like. Another possibility is to request a disk from the shipit service through the Ubuntu website.

One way to check if it is the disk is to try it on another machine with different specs. If it works, it's your machine, if it does the same thing, it's the disk.

One more question, are you using the Desktop Install CD or the Alternate Install CD?


I downloaded my iso off the ubuntu site, don't remember which site though.
The CD has worked on several different desktops and laptops  and has put ubuntu on all of them flawlessly.
When I got the error on this machine I got another Hard Drive and installed ubuntu on it on a different machine just to re-check the CD, it worked fine.

I'm using the Desktop install CD.

It has got to be something with this machine.  The CD works everywhere else I try it.  Dapper and Edgy both started fine on this machine, thats why I'm baffalled over this error.

---

### Post by teddybairs1 on 2007-05-06
Spaniard,

I did some checking on your motherboard on the forum. It seems like this isn't the first time you've had trouble with this system. there was another post on another thread where someone had trouble with the same motherboard:

> I mentioned earlier there may be hardware issues. Installing Ubuntu in the first place was rather involved due specifically to the system board I am using-an ASUS P5GD1-VM. Though it has 2 IDE channels, it only supports 2 IDE drives which must both be on the primary IDE channel, when there are not SATA drives also present, something that is not acknowledged in the user manual, something I discovered as I wanted to set up an IDE slave drive with Windows98 on it, figuring it would be easier to integrate the data files on it into, if not export them to, the Ubuntu drive as most are in formats not needing a Windows98 enviroment to use. No settingss in the BIOS or hardware configuration would eliminate a "cannot find CD" error when I attempted to install Ubuntu until I elmiinated the second IDE hard drive and set the IDE CD drive as slave on the same channedl as the hard drive.

As noted earlier, my problems resulted in an attempt to switch from the GNOME desktop of Ubuntu to the KDE interface of Kubuntu. I made several attempts to download and install Kubuntu, as well as Opera, but the best I was able to do was install some KDE games (which I would have preferred not to install since I am unlikely to play them) and a drawing program. Since the KDE interface is a better "fit" for my "style", I kept trying to install its desktop, but utlimately managed not only to fail in the same, but also "locked" myself out of the Ubuntu desktop. I got numerous reports of errors, too many to consider listing, beginning with "file system seems to be mounted read only". I ended up at a command line prompt, but I was unable to determine what command options were available to me (the list command would not work), much less which, if any, might resolve the problem(s).


I don't know if this helps or not, but it was all I could find.

Here are some links to threads of people with similar problems:
[http://ubuntuforums.org/showthread.php?t=393275&highlight=ASUS+P5GD1](http://ubuntuforums.org/showthread.php?t=393275&highlight=ASUS+P5GD1)
[http://ubuntuforums.org/showthread.php?t=151214&highlight=ASUS+P5GD1](http://ubuntuforums.org/showthread.php?t=151214&highlight=ASUS+P5GD1)
[http://ubuntuforums.org/showthread.php?t=118291&highlight=ASUS+P5GD1](http://ubuntuforums.org/showthread.php?t=118291&highlight=ASUS+P5GD1)

Try browsing through them and see if they had any solutions. In general it seems to have something to do with the IDE on the motherboard.

---

