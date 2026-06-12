---
title: "Why doesn't this backup tar exclude correctly?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by rpommier on 2007-03-22
tar cvpzf rodbackup.tgz --exclude=/var/www/torrentflux/html/downloads/ --exclude=/dev --exclude=/media --exclude=var/cache --exclude=/var/spool --exclude=/var/tmp --exclude=/home --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

I would like to skip the /var/www/torrentflux/html/downloads, because it gets large.  All I want is the important stuff so that I can recover easily.  Is there a way to either exclude files over a certain limit or get the tar to exclude directories correctly? 

Is there maybe a depth limit for --exclude?

Thanks,
Roderick

---

### Post by lloyd_b on 2007-03-23
Will tar accept multiple "--exclude" directives?  I've never tried that.

At any rate:  Try creating a file with a list of those directories, and use the "--exclude-from=filename" option and see if it works better.

Lloyd B.

---

### Post by rpommier on 2007-03-23
Here is the contents of my backupscript.txt

/var/www/torrentflux/html/downloads
/dev
/media
/var/cache
/var/spool
/var/tmp
/home
/proc
/lost+fond
/backup.tqz
/mnt
/syS

Then I do a **tar cvpzf rodbackup.tgz --exclude=backupscript.txt /**

Is that correct?

vr,
Roderick

---

### Post by lloyd_b on 2007-03-23
> **rpommier said:**
> Here is the contents of my backupscript.txt

/var/www/torrentflux/html/downloads
/dev
/media
/var/cache
/var/spool
/var/tmp
/home
/proc
/lost+fond
/backup.tqz
/mnt
/syS

Then I do a **tar cvpzf rodbackup.tgz --exclude=backupscript.txt /**

Is that correct?

vr,
Roderick

"/syS"?  Was that a typo in the post?  Other than this , it looks fine to me.

Lloyd B.

---

### Post by silkstone on 2007-03-23
For what it's worth, my backup script is...

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media/windows --exclude=/home/silkstone/Photos --exclude=/home/silkstone/Music --exclude=/home/silkstone/Desktop/Downloads / 
```

That works fine.

---

### Post by rpommier on 2007-03-23
yes /syS is a typo :) **/sys**

Everything looks to be working fine.  Thanks for the help.  My backup finally made it past my torrent download section.  My goal is to be able to get the server back the way I have it now and throw the files back on there from DVD if need be.  I just don't want to avoid all the configuration again.

Roderick

---

