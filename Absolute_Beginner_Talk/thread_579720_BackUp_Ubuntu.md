---
title: "BackUp Ubuntu"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-18
I want to " Image " my whole Ubuntu installation to a Bootable DVD.
How can I do this?

I use Ghost to do this with my Windows Xp Professional.
I like this because when something goes wrong, you can
just blast the image back to the drive and your up and
running with no additional work.

---

### Post by overdrank on 2007-10-18
> **Orbital75 said:**
> I want to " Image " my whole Ubuntu installation to a Bootable DVD.
How can I do this?

I use Ghost to do this with my Windows Xp Professional.
I like this because when something goes wrong, you can
just blast the image back to the drive and your up and
running with no additional work.

Hi maybe this link will be of some interest 
[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)

---

### Post by mthaddon on 2007-10-18
I use rsync to do this to an external hard drive. Something like this:

rsync -avz --delete --exclude-from=your-hostname_exclude / /media/disk/your-hostname

your-hostname_exclude would look something like this:

/boot/
/lib/modules
/etc/modules
/etc/lilo.conf
/etc/fstab
/etc/mtab
/proc
/dev
lost+found/
/var/log/
/sys
/media
/tmp

(You don't have to exclude these. I do because it means I can do a fresh install, and then restore from backup and I'm all there)

---

