---
title: "Backing Up My Music Collection"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-07-03
I'm a recent windows convert and within my system I have two HD's; the first contains all of my windows OS and applications; the second is split between my documents, a BACKUP partition and the Ubuntu bit. Basically when I was using windows I used a program called Synctoy (boo, hiss?) to backup my Music collection from the documents partition to the BACKUP partition. It was a nice simple little program, it would apply any changes that were made in the documents section to the BACKUP section so if I deleted or re-organised my collection it would be re-organised on the BACKUP side. The question is, how can I do this in Ubuntu? I looked at various backup programs but they all seem to be designed to backup my Ubuntu configuration itself which is not what I'm looking for. I need something that will note changes on one side and apply them to the other as well rather than just using "cp" in a terminal (although is there a way to do this just using cp?).

Thanks

---

### Post by koshari on 2007-07-03
use rsync.

its very good, 

heres my line
```

rsync -r --del -u /bigmutha/music /media/usbdisk/music --progress
```

this command will backup the selected directory &#8220;/bigmutha/music&#8221; in /media/usbdisk/music, 

the -r switch means it will do it recurively, (keep directory structure) and the -u means update (will only copy updated/new files making a lot quicker backup.

the --progress switch prints a progress report so you ave an idea how long is left.

some of the benifits of this methood include, 

if i update the tags on a couple of songs, those will be updated because the time stamp will change and they will be seen as newer files.

if i delete some rubbish from my working directory , ie old coverart ect it will be cleaned from the backup, there is one little con with this however, if you accidently delete some stuff you want from the working directory without knowing, it will get deleted from the backup. it will print a list of the files deleted however for you actually see what you deleted.

---

### Post by kpkeerthi on 2007-07-03
Or try unison. It also has a graphical interface if would prefer (unison-gtk). It is in the repository.

```

sudo aptitude install unison unison-gtk

```

---

### Post by Matuku on 2007-07-04
> **kpkeerthi said:**
> Or try unison. It also has a graphical interface if would prefer (unison-gtk). It is in the repository.

```

sudo aptitude install unison unison-gtk

```
Unison doesn't want to work it just comes up with all sorts of errors when I try and synchronise (mostly something about not correct permissions).

---

### Post by Matuku on 2007-07-04
> **koshari said:**
> use rsync.

its very good, 

heres my line
```

rsync -r --del -u /bigmutha/music /media/usbdisk/music --progress
```

this command will backup the selected directory “/bigmutha/music” in /media/usbdisk/music, 

the -r switch means it will do it recurively, (keep directory structure) and the -u means update (will only copy updated/new files making a lot quicker backup.

the --progress switch prints a progress report so you ave an idea how long is left.

some of the benifits of this methood include, 

if i update the tags on a couple of songs, those will be updated because the time stamp will change and they will be seen as newer files.

if i delete some rubbish from my working directory , ie old coverart ect it will be cleaned from the backup, there is one little con with this however, if you accidently delete some stuff you want from the working directory without knowing, it will get deleted from the backup. it will print a list of the files deleted however for you actually see what you deleted.

I've hit a snag in the fact that (because the music files were on a windows directory) the file path contains spaces (/media/sdb1/My Documents/My Music) and it can't handle the spaces; it treats them as separate code. Is there anyway around this (I tried replacing the spaces with underscores in the code itself but it treats it as a completely different (and non-existent) directory)? I'm reluctant to change the folder names as this would probably have adverse effects on my windows installation.

---

### Post by hyper_ch on 2007-07-04
rsync is a file synchronizer.... I use it for my backups also and also for incremental snapshot-style backups.

---

### Post by hyper_ch on 2007-07-04
For the handling of spaces in the path you can write a small shell script

```

#!/bin/sh
FROM="/path/where you want/to backup from"
TO="/path/where/you want/to backup to"

rsync -ra --del -u $FROM $TO

```

---

### Post by Matuku on 2007-07-04
> **hyper_ch said:**
> For the handling of spaces in the path you can write a small shell script

```

#!/bin/sh
FROM="/path/where you want/to backup from"
TO="/path/where/you want/to backup to"

rsync -ra --del -u $FROM $TO

```
Can you walk me through what each step of this does? (Also can I put this straight into the terminal? Or do I have to do something else?)

I was wondering if putting My%20Documents would work (as this is how it works for websites), any thoughts?

---

### Post by xavierzenith on 2007-07-04
Bash handles spaces with escape characters "\ "
So, it would look something like this:
/path/from\ backup
/path/to\ backup
notice the "\ space" before the "backup"

---

### Post by Matuku on 2007-07-04
So for my instance I would put ```
rsync -r --del -u /media/sdb1/My\ Documents/My\ Music /media/sdb7/Music --progress
```

Replacing all spaces in the paths with "\ "

Am I understanding this right?

---

### Post by hyper_ch on 2007-07-04
> **Matuku said:**
> Can you walk me through what each step of this does? (Also can I put this straight into the terminal? Or do I have to do something else?)

well

(1) Create a file called backup.sh
(2) Place the content that I have written above in it (just change the from and to pathes)
(3) open a terminal and run the file by issuing
```

sh backup.sh

```
(4) depending on the permissions of the files you want to backup you need to run it as root... in that case use:
```

sudo sh backup.sh

```

---

