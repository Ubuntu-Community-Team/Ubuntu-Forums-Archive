---
title: "Hardrive/File Syncing/Backup Software?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-25
So I never keep any of my files on my laptop.

I have a portable hardrive that I keep strapped to my laptop at all times that I put all my files in,
and a desktop external hardrive I keep at home.

I want the files on the portable hardrive to be synched with the hardrive at home, so that when I plug in my home harddrive to the laptop all the files from the portable hardrive get coppied into/synced with the home hardrive.

Does anyone know what program I could use under Ubuntu?
(I have OSX and XP also if you know any programs those too)

Is there some kind of script I could write to do this?

Thanks guys

---

### Post by freebeer on 2008-02-25
rsync works really well for me.

---

### Post by justleen on 2008-02-25
I like[ unison]("http://www.cis.upenn.edu/~bcpierce/unison/") (available in the repros) quite well.. does two way syncing.

---

### Post by Xarok on 2008-02-25
> **freebeer said:**
> rsync works really well for me.

Could thiss allow me to have files added to my harddrive be synched throuhg the internet to the hardrive at home, if it's attacted ot a computer?

---

### Post by freebeer on 2008-02-25
Most likely, if set up right.

I use rsync to back up (daily) 6 Windows machines at the office to a Ubuntu server.  The server then rsyncs to another Ubuntu server at home (off-site storage) over the Internet.

Note: in my particular case, the last step is not yet fully implemented.  Only because I don't want to try to rsync some 60 gigs over the Internet. ;) I'll back up the office server to an external drive, take it home, and copy it to the server there.  Once that's done, I can use rsync for the incremental backup.  (Much less bandwidth) :)

I've never tried unison, as justleen has suggested.  That may be a viable option for you as well.

---

