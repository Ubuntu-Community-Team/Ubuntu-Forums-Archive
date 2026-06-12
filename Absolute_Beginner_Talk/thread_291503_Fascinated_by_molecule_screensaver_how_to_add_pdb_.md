---
title: "Fascinated by molecule screensaver: how to add pdb files??"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Cannaregio on 2006-11-02
Can anyone explain me HOW you can see more PDB (Protein Data Base) files as input?

It seems you theoretically can:
[http://www.linuxcommand.org/man_pages/molecule1.html](http://www.linuxcommand.org/man_pages/molecule1.html)
but infact I can still only see the pdb molecules that are hardwired into thescreensaver.
I made a subdir with pdb files, 
that I found here:
[ftp://ftp.rcsb.org/pub/pdb/data/structures/all/pdb/](ftp://ftp.rcsb.org/pub/pdb/data/structures/all/pdb/)
I tried redirecting and piping. No luck.
What am I doing wrong?

----
November:
found out: you have to ditch gnome-saver and switch to the real wscreensaver.
Then you create an extra subdir with the pdb files, and then you can see all of them when the screensaver kicks in.
-----
June 2007:
Let's see if I can explain this in a more useful way:
First of all you have to enable the real wscreensaver adding the following code to your session start appz
System => Preferences => Sessions => New
```
xscreensaver -display :0.0 -nosplash
```

Then make sure you nuke/eliminate the **gnome-screensave**r and instead download/use **xscreensaver** through synaptic.

Then run the command
```
xscreensaver-demo
```

and decide, using the 'advanced' settings,* inter alia*, where you will have your own pdb folder. 
Now you must fill/populate that very folder with any pdb file you like.

You can find **tons**/**zillions** of pdb files on the web, for instance at [http://www.rcsb.org/pdb/results/results.do]("http://www.rcsb.org/pdb/results/results.do").
ALas:  in molecule you won't see atom names and bindings whenever those molecules pdb files you downloaded are too big.

---

### Post by Chymera on 2007-07-30
i dont seem to be able to unarchive the files from that site (format .ent.Z)

---

### Post by Salmonman on 2007-07-30
.Z is the old unix compression algorithm (not archiver) called *compress* which was superceded by *gzip*. Just type ```
uncompress file.ent.Z
```
and you will uncompress the file to file.ent which is one of the formats used by the molymod screensaver [http://filext.com/file-extension/ent]("http://filext.com/file-extension/ent")

EDIT

Wait a second, a page like[ http://www.rcsb.org/pdb/explore.do?structureId=2EZE]("http://www.rcsb.org/pdb/explore.do?structureId=2EZE") for example (search: DNA) has the PDB file immediately available (click the page icon with a blue arrow pointing downwards on it)  and they are all .pdb files. Not sure where you are getting this .ent

---

### Post by Chymera on 2007-07-30
im getting the .ent.z's from 
[ftp://ftp.rcsb.org/pub/pdb/data/structures/all/pdb/](ftp://ftp.rcsb.org/pub/pdb/data/structures/all/pdb/)

Is there any gui controller for xscreensaver? because i cant find anything listed in place of the gnome-screensaver in prefs

---

### Post by Chymera on 2007-07-30
woah wait, i dont want those immense protein models, i was looking for a larger database of smaller compound models (eg toluen, dextrose, phenylalanine). any idea where i can find some of those?

---

### Post by Chymera on 2007-08-04
anyone?

---

### Post by anandus on 2007-09-14
Bump, I'd like to know that as well :)

---

### Post by Cannaregio on 2007-09-15
Try this as well :)

[ftp://ftp.wwpdb.org/pub/pdb/data/structures/all/pdb/]("ftp://ftp.wwpdb.org/pub/pdb/data/structures/all/pdb/")... a bazillion files :)

---

