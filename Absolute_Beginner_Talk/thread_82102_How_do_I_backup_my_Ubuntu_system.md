---
title: "How do I backup my Ubuntu system?"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by iSAWaUFO on 2005-10-25
I'm new to Ubuntu, but I've used Red Hat 8.
There was a dump/restore command on Red Hat that I used to backup the file system to a Samba network share. I don't see dump in the default Ubuntu distro and the dump in Synaptic package manager says for ext2 file system. My Ubuntu is ext3. I started using dump/restore because the backup files got too large to work with tar (> 2GB).

I'm working on migrating my system from Red Hat 8, but one of the first things I need to figure out is how am I going to backup the system. I just need to backup one system in a simple, understandable manner. I like the convenience of doing a backup to a dedicated backup drive (maybe on the network). I've got less than 6 GB of data to backup.

Can anyone recommend a procedure?

---

### Post by the_clown on 2005-10-25
Google helped make this simple program to backup files:
[http://sourceforge.net/projects/sbackup](http://sourceforge.net/projects/sbackup)
Some screenshots are here:
[http://linux.softpedia.com/progScreenshots/SBackup-Screenshot-4630.html](http://linux.softpedia.com/progScreenshots/SBackup-Screenshot-4630.html)

---

### Post by wellery on 2005-10-25
you could use rsync to backup your files:

[http://samba.anu.edu.au/rsync/]("http://samba.anu.edu.au/rsync/")



```
rsync -a <from> <to>
```

---

### Post by cwaldbieser on 2005-10-26
[QUOTE=iSAWaUFO]I'm new to Ubuntu, but I've used Red Hat 8.
There was a dump/restore command on Red Hat that I used to backup the file system to a Samba network share. I don't see dump in the default Ubuntu distro and the dump in Synaptic package manager says for ext2 file system. My Ubuntu is ext3. I started using dump/restore because the backup files got too large to work with tar (> 2GB).

I'm working on migrating my system from Red Hat 8, but one of the first things I need to figure out is how am I going to backup the system. I just need to backup one system in a simple, understandable manner. I like the convenience of doing a backup to a dedicated backup drive (maybe on the network). I've got less than 6 GB of data to backup.

Can anyone recommend a procedure?[/QUOTE]

I just use "tar" on my data directories and burn it to a CD every once in a while.

---

### Post by bionnaki on 2005-10-26
[QUOTE=cwaldbieser]I just use "tar" on my data directories and burn it to a CD every once in a while.[/QUOTE]

yup.

follow this HOW-TO: [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

---

