---
title: "Natty LiveCD doesn't start on MacbookPro 2.1"
date: 2011-05-01
forum: Apple Hardware Users
---

### Post by Romu on 2011-05-01
Hi all,
I wanted to try to Natty 64 on my wife's Macbook Pro 2.1 (Core 2 Duo + ATI X1600) and I got a FAIL.

Indeed the LiveCD doesn't start at all, I don't even get the Try/Install GUI, just a sort of choice:

```

1.

2.
Select CD-ROM Boot Type : 

```

And a blicking cursor, I have no keyboard control at all, and I can't get something other than switching off the Mac.

Any idea? Thank.

---

### Post by piwacet on 2011-05-04
I don't fully understand this, but the 64 bit disks will not boot on some apple hardware, apparently due to problems with efi.  Personally on my macbook 2,1 I've tried the 11.04 64 bit "normal" install CD, the alternate CD, and the mini CD.  All have the same problem.

I think this problem began with the 10.10 release, and there is a bug report which I don't have handy now.

The 32 bit versions are reported to work.

Personally, since I have 4G of ram, I want 64 bits... so I'm installing the 10.04.2 release, and will upgrade from there.

---

### Post by Silmathoron on 2011-05-05
Come on guys, try to do a quick research before creating a new thread... The answer to that problem has already been given at least twice
[http://ubuntuforums.org/showthread.php?t=1746149](http://ubuntuforums.org/showthread.php?t=1746149)
[http://ubuntuforums.org/showthread.php?t=1654993](http://ubuntuforums.org/showthread.php?t=1654993)

When in the install menu, press F6 and chose "nomodeset" then Esc and chose the action you want to do (Try, Install...)
On reboot, when in grub, press "e" and add nomodeset at the end of the line displaying "kernel" then press F10.
Have a nice installation ;)

---

### Post by piwacet on 2011-05-05
Thanks for the help, but this thread is about an entirely different issue, not related to the modsetting issue.  The 64-bit CDs are unable to boot at all.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/633983](https://bugs.launchpad.net/ubuntu-release-notes/+bug/633983)

---

### Post by Silmathoron on 2011-05-06
Sorry, my mistake...
Exactly, what happens ? You insert your CD, reboot, press Alt immediately after, and then ?

---

### Post by mingetch on 2011-05-19
> I don't fully understand this, but the 64 bit disks will not boot on some apple hardware, apparently due to problems with efi. Personally on my macbook 2,1 I've tried the 11.04 64 bit "normal" install CD, the alternate CD, and the mini CD. All have the same problem.

I think this problem began with the 10.10 release, and there is a bug report which I don't have handy now.

Indeed it seems to be started in 10.10 as stated here:

[INDENT][MacBook 2.1 - Basic Installation Instructions]("https://help.ubuntu.com/community/MacBook2-1/Maverick/#Basic%20Installation%20Instructions")[/INDENT]

Although that doc is for Maverick it can lead to a Mac bootable Natty ISO, which is this:

[INDENT][64-bit Mac (AMD64) desktop CD]("http://cdimage.ubuntu.com/releases/11.04/release/ubuntu-11.04-desktop-amd64+mac.iso")[/INDENT]

Almost all the tweaks from the Maverick's tuto (first link) works in Natty, so enjoy your mac :).

---

