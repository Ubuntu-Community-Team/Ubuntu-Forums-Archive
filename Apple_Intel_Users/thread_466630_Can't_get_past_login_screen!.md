---
title: "Can't get past login screen!"
date: 2007-06-06
forum: Apple Intel Users
---

### Post by LieToPurify3 on 2007-06-06
I just installed Ubuntu on my Macbook with parallels and it booted fine the first time.  However, now when I try to start up my Ubuntu VM, I type in my username and password, and if I type my password in correctly, it goes black and flashes back to the startup screen for a sec before going back to the login screen.  This happens no matter how many times I type in my name and password.  I was able to get a screenshot of what goes on when it crashes after I put in my password, even though it only flashes for a split second.  Here's what comes up:

* Activating swap...    [ok]
* Checking root file system...
fsck 1.39 (29-May-2006)
/dev/mapper/Ubuntu-root: clean, 104181/706816 files, 496689/1411072 blocks
                                   [ok]
* Checking file systems...
fsck 1.39 (29-May-2006)
/dev/hda1: recovering journal
/dev/hda1: clean, 30/124496 files, 28816/248976 blocks
                                   [ok]

I don't know if that tells you anything, but I figured it wouldn't hurt.  Thanks!

---

### Post by ronocdh on 2007-06-07
Have you tried using a failsafe session to login? Perhaps you could get around the issue like that and launch X from the command line, but given it's throwing a fsck message, I don't think that will do it. (Please try anyhow!)

The reference to journaling is odd... the /dev/hda1 is your Ubuntu virtual drive, correct? Meaning that it's referring to ext3 journaling rather than HFS+ journaling on your OS X installation?

I would search for more information on fsck journaling errors. Sorry I can't offer more help at the moment, but start searching and see what you come up with. We'll all be here in the meantime, hopefully. =)

---

