---
title: "Are their 'TEMP' files in Linux to delete?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by valnar on 2005-12-26
This is a general Linux question.  I like to keep my Windows installations pretty tidy and frequently delete things that show up in my "temp" directory, as it's defined in Windows.  Adding programs, uninstalling, unzipping, bad reboots, etc. leave an aftertaste of 100's of files that are pretty easy to delete.  Of course, Windows also requires the occasional defrag and chkdsk as well.

Is there an equivalent to this buggy Redmond phenomenon in Linux?  Will my drive start filling up with junk (somewhere) after a year or so?  I doubt I'd ever really notice, since I tend to re-image a new Ubuntu at least every 6 months, but it's nice to know.

For that matter, what other maintenance things should a good Linux user do?

-Robert

---

### Post by harisund on 2005-12-26
Filling up with junk? I don't recollect my Windows XP collecting junk. 

Anyway, to answer your question, "adding programs, uninstalling, unzipping, bad reboots" etc do leave "an aftertaste" of quite a few libraries "that are pretty easy to delete." even in Linux. 

What I use often is a package called deborphan. 
```

deborphan | xargs apt-get -y remove --purge

```
This would really help if you do a lot of package intalls and purges, since there may be some libraries that get installed as a necessity, but wouldn't get uninstalled. 

There is a /tmp folder which wouldn't hurt much to have a periodic look at. 

Also /var has a /tmp folder and spool folders that might not be of much use. I think the log files are stored here as well. I normally remove the log files once a while

---

### Post by valnar on 2005-12-27
Thank you.  This helps!

Robert

---

### Post by Marshall2day on 2005-12-27
If you are interested in a graphical frontend for this, it's called gtkorphan.

---

### Post by bscbrit on 2005-12-27
For those having problems with getting this to run, try:

sudo deborphan | xargs sudo apt-get -y remove --purge

Thanks to harisund for the original tip.

---

### Post by Kindred on 2005-12-27
Also, you can do deborphan through Synaptic - go to Settings > Filters, add a new filter and just tick the Orphaned box (must have deborphan installed).  Your new filter is then in Custom.

---

### Post by camellochapin on 2008-05-12
> **bscbrit said:**
> For those having problems with getting this to run, try:

sudo deborphan | xargs sudo apt-get -y remove --purge

Thanks to harisund for the original tip.

Thanks a lot for the slight change!  Worked perfectly!

---

