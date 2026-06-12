---
title: "UBER nub help"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by pwnage101 on 2007-02-16
below is one of my posts from another forum.

> **pwnage101 said:**
> 
[QUOTE=Cyraan;6033864]Heh, I did, I've heard the best is to split whatever you were going to give Linux 30%/70% between root/home.  

/home is where your desktop will be, and you'll also be keeping most of your downloads, media and whatnot there as well, as the other parts of the file system are owned by root, so you'd have to invoke it to do anything more than reading files.

I know this all might sound complicated (owned by root, etc), but after a few days, it'll all make sense.


i was planning on making partitions go like:

[COLOR="Orange"]"D" 4gb (system restore)
"C" 60gb (XP OS & programs)[/COLOR]
[COLOR="Lime"]"Linux" ?gb (the stuff you said, root/home)[/COLOR] <---this is divided into two partitions
[COLOR="DeepSkyBlue"]"name?" RESTgb (all my saved crap, songs, movies, pics, work, etc)[/COLOR]

this is on a 300gb hdd

did you mean that "home" would include all my random files that would go in "my documents" on a windows?  cuz i was planning on putting those in the last partition so they are safe and everything's clean 'n neat for dual boot.  and when you say it'll all make sense, does that mean linux will ask what partitions to install home and root?

sorry i will migrate over to ubuntu forums after this situation

edit: should i dl 6.10 or 6.06? [LINK]("http://www.kubuntu.org/download.php")[/QUOTE]

here is a link to the original thread:
[http://forums.steampowered.com/forums/showthread.php?t=537391](http://forums.steampowered.com/forums/showthread.php?t=537391)

---

### Post by shareMenaPeace on 2007-02-16
Hi,
try to make the partition where you install ubuntu with all the linux operating files and your /home/yourUserName folder which is like myDocs, at least 20 gigabyte or 30gb.

To partition your harddrive boot from the LIVE CD (go ahead try 6.10) and start the installer (link on desktop). Partition "manual" and create at least 

```
1 x (hd0) i suggest arround 20-30gb - partition for main stuff and /home/yourUsername
1 x (hd1) assign the rest.  You can later resize again. The name will be like 
1 x (hd2) linux swap  around 1gb
```

And  here is a tipfor partitioning
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

