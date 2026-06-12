---
title: "system monitor showing strange filesystems"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-04-07
hi, when i load up the system monitor, it shows this (on screenshot)

/dev/sda1 is my usual filesystem thing
//iomega-01b44c/public is a networked, mounted HD

the others i haven't a clue about...

N.B. I do **not** have 'show all filesystems' enabled

any help?

---

### Post by Michael.Godawski on 2008-04-07
When you go the location Filesystem > proc > fs > nfsd or vmblock > mountpoint, are there some files or are the directories empty?

Are you experiencing any problems with your system?

---

### Post by Fire_Chief on 2008-04-07
One looks to be related to any remote fileshares mounted via NFS. It appears you don't have any mounted.
The other one I'm not sure about (does not appear in my list on Gutsy). But it may be related to virtual memory usage? or swap space?

Odds are you don't have to worry about either one really.

---

### Post by benji.ijneb on 2008-04-07
> **Michael.Godawski said:**
> When you go the location Filesystem > proc > fs > nfsd or vmblock > mountpoint, are there some files or are the directories empty?

Are you experiencing any problems with your system?

when i go there, there is only a directory called 'nfsd' and one called 'fs'

nfsd has about 15 tiny files in it, fs has one

i am not experiencing any problems, just wondering....

---

### Post by canthus13 on 2008-04-07
Seeing as nsfd is the network filesystem daemon, I would think that /proc/fs/nfsd would simply be the location in the filesystem that references the daemon.  Simliar for the other unidentified one.  see this article for more info about /proc: [Exploring /proc.]("http://www.freeos.com/articles/2879/")

--Me

---

