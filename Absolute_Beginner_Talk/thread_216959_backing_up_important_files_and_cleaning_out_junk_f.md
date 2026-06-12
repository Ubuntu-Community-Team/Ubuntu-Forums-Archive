---
title: "backing up important files and cleaning out junk files?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-16
Hi, just wanted to know what files are important to back up? i have a couple of back up programs installed but dont know exactly what except for /home. 

somehow a few days ago i erased all my settings and had to go searching for all my firefox plugins and lost all my folders nothing big since i moved my media files to my xp partition but i did lost my pictures. so i want to avoid that again. 

also in the / partition, can i manually go in there and delete unneeded files? if so what files can be removed since my /tmp folder was the reason i had my problems. is there a program i can get that will automatically clean all junk files for me?

---

### Post by mostwanted on 2006-07-16
For file managing as root do this:

```
gksudo nautilus
```

All your settings live in your home folder in hidden folders and files (files and folders prefixed with a dot). You can select View &#8594; View hidden files in Nautilus to see them, or just do a

```
ls .*
```

in your home folder.

---

### Post by maddbaron on 2006-07-16
> **mostwanted said:**
> For file managing as root do this:

```
gksudo nautilus
```

All your settings live in your home folder in hidden folders and files (files and folders prefixed with a dot). You can select View &#8594; View hidden files in Nautilus to see them, or just do a

```
ls .*
```

in your home folder.

thanks...from what i see my root only has 349 mb's free but my other paritiuons have gig's free. i went to the tmp folder in root and it had stuff in there that looked essential.  what is safe to delete in root? i'm going to burn a copy of my home folder just to save myself. is it possible to have root use from other partitions? like i have a documents folder which is empty at 3.6gigs anyway to have that partition share space with root?

---

