---
title: "Mounting drive question."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-09-03
If I have a drive that has my OS (ubuntu) installed on it and I mount a second drive to /var/ and save a file to /var/ will it save on the first drive or the second drive?

The reason I ask is if I need to add more storage to /var/ for myth-tv.  Can I just add a new drive and mount it on /var/ and then have more storage?

---

### Post by rickycodie on 2007-09-03
your first drive should be mounted to /mnt, so i don't think so. but i don't thnk that you can mount a drive to /var. i'm pretty sure that it has to be under /mnt.

---

### Post by schorsch on 2007-09-03
/var is in use as soon as you start up your computer (for syslog, lastlog, etc ) so it is a really bad idea to mount a drive to /var after the computer has booted as this could cause some system processes to crash. Either mount it to another mountpoint or make sure that it is ALWAYS mounted to /var when you start up the computer.

---

