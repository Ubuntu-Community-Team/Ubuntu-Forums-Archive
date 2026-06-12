---
title: "Network folder copier?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by arron on 2007-04-27
I read before somewhere that someone had a folder on their laptop that automatically copied to a server and kept itself updated whenever connected.

I would like to do this for both a Ubuntu and XP pc's  It is not for huge files, but just work stuff, and i already have a dvdrw backup on the server (Debian).  What I do now is copy the file over manually, but i would love to have this done automatically.

I read that someone somewhere did this, but I cant find any information on this.  For some reason i think it was a command line app, but like i say its been a while since i read about it.

Can anyone help out for both ubuntu and xp to do this?

---

### Post by dfreer on 2007-04-27
rsync should upload a folder to a remote destination, and the next time it is run it will scan for changes and then copy only those changes. I believe you can then call it in a cron job so that it will check for changes every day/every week/etc.

---

