---
title: "MySQL"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by bdemsey on 2006-09-11
I get the following message -


Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

when trying to install MySQL Server.

I have Ubunto installed so I don't understand why it doesn't see Breezy Badger.

Answers?

Thanks.

---

### Post by jordanmthomas on 2006-09-11
Have you put the CD in like it asks?

---

### Post by az on 2006-09-11
> **bdemsey said:**
> I get the following message -


Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

when trying to install MySQL Server.

I have Ubunto installed so I don't understand why it doesn't see Breezy Badger.

Answers?

Thanks.

If you have broadband, click on the update-notifier and upgrade to the newest release.

If you don't, you are being asked to put in the Breezy disk you installed from, so that it can install a package (or more than one) from there.  By default, if the package it needs is on the cd, it will get it there instead of downloading it from the net.  Unless there is a newer version on the net in the breezy repository.

If you are expecting to use the Dapper repo, you must get rid of all the breezy repos in your /etc/apt/sources.list and dist-upgrade to Dapper first.

---

