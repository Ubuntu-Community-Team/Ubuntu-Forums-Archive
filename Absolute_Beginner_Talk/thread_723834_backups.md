---
title: "backups"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by niko123 on 2008-03-13
hi everyone....how woulr i entirely back up EVERYTHING on my hardrive on to a cd..? just incase i have to re-install ubuntu i dont want to loose any of my information....and if i back it up when or if i have to install ubuntu...will the CD be bootable...or ??? i dont know a thing about how to make a back up cd...and if there bootable....so if anyone can provide me a good how to guide...or give me some information it would me AWSEOME

thanks!!!

---

### Post by finer recliner on 2008-03-14
```

sudo tar cvzf backup.tar.gz /

```

will make a backup up of everything in a compressed tarball (like a zip file, but more commonly used in linux). not bootable.

---

### Post by FreewareFan on 2008-03-14
What you need is a program called Remastersys.  It will do a total and complete backup, including your personal files and settings, and make it to be just like a Live CD !! It autoboots, just like the Live CD, in fact, it really is your personal version of Ubuntu.  You can even distrubte it to friends if you want.  In my case, it's a Live DVD, because of all the personal files and settings I have.  It's a very very good program, and I've used it several times now, and it always works perfectly!  Do a search on Google for it, and it will provide all the instructions for how to use it.  You'll love it, guarenteed.  

FwF

---

### Post by kpkeerthi on 2008-03-14
1. [Tar]("http://www.linuxmint.com/forum/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a")
2. [Partimage]("http://www.psychocats.net/ubuntu/partimage") *
3. [Clonezilla]("http://clonezilla.sourceforge.net/") *

* Use [gparted-clonezilla Live CD]("http://gpartedclonz.tuxfamily.org/")

I personally prefer Method 1 (tar) so it is easier to automate the backup process with a cron job. Manual intervention is not required and the backup process can run transparently behind tthe scenes.

---

### Post by erginemr on 2008-03-14
If you are not after a bootable Live CD, I suggest the following method which just works:
[http://ubuntuforums.org/showthread.php?t=35087&highlight=restore+howto](http://ubuntuforums.org/showthread.php?t=35087&highlight=restore+howto)

---

