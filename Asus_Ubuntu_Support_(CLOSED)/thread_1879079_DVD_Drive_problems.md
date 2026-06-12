---
title: "DVD Drive problems"
date: 2011-11-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by JeremyT on 2011-11-10
I'm having problems while booting Ubuntu 10.04.3.  I can't get it to boot when I have the DVD drive plugged in.  I've tried two different IDE cables and two different drives and it doesn't fix the problem.  When I disconnect the drive it boots to the login screen very quickly.

Some of the errors I'm getting during start-up:
[   52.816024] ata1: lost interrupt (Status 0x58)
[   27.856016] ata1: link is slow to respond, please be patient (ready=0)
[   Nums here] ata1: soft resetting link

and more.  I'd do a straight copy/paste but I can't seem to find those logs (New to Ubuntu)

Like I said, the problem is fixed when I disconnect the DVD drive, however I still need to use that drive.  I can get it to boot by typing "exit [enter]" but that is really just a temporary "fix" and it appears that the DVD drive works once it's booted.

Sometimes, depending on how long I wait, if I press enter it will go to a screen with a "(initramfs)" prompt saying it gave up waiting for root device.  [Similar to this]("http://i35.tinypic.com/30jp8c0.jpg")

Anyone know what to do to fix this problem?

I've scoured these forums a bit searching for answers, and a few others have had the same problem.  But none of the fixes seem to work.

Setup:
Old 2005 computer.
Asus Pundit-R AB-P2800
P4 2.3 or 4ish GHz
1GB Ram (2x512MB)
Win xp + Ubuntu 10.04
LG DVD drive w/ Light Scribe (Fairly new drive)

Extra notes:
I've also noticed that I can eject the disk drive while it's having it's boot temper tantrum and it'll do it, but I cannot close the tray until it gets over it's tantrum.

I read somewhere else where they replaced their IDE cable and it worked beautifully, so I'll see if I have another cable laying around somewhere.

This same problem seems to happen (but not as bad) when booting a USB Live image on this computer

---

### Post by JeremyT on 2011-11-11
Update: After hours more of googling, I found the answer!  It helps to search for more than just one "error" you're getting.  The winning search was "ata1: lost interrupt (Status 0x58)".

Fix: [http://ubuntuforums.org/showthread.php?t=1549579](http://ubuntuforums.org/showthread.php?t=1549579)

---

