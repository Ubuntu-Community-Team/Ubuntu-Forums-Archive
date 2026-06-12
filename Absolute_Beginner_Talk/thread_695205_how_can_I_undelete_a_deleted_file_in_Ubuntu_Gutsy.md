---
title: "how can I undelete a deleted file in Ubuntu Gutsy?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-02-12
Hi, I copied a .dmg file to another location and then deleted the original. It turns out the new copy is corrupted when I try to convert it to an img. Is there a way to undelete the original file? It's not in waste basket. Totally deleted. Thanks

---

### Post by randy78 on 2008-02-12
> **iansane said:**
> Hi, I copied a .dmg file to another location and then deleted the original. It turns out the new copy is corrupted when I try to convert it to an img. Is there a way to undelete the original file? It's not in waste basket. Totally deleted. Thanks

I'm not too sure if it will work, but there is a program called PhotRec that comes with the TestDisk package that has the ability to recover most known filetypes, after they have been deleted.

If, however, the space that the deleted file was occupying has already been overwritten by the disk, you will be unable to reclaim it.

sudo apt-get install testdisk

then in a terminal do:
photorec

Good luck! :popcorn:

---

### Post by iansane on 2008-02-12
thanks I'll give it a try

---

### Post by iansane on 2008-02-12
Hey, that's a great program!! I haven't recovered the dmg file yet but it recovered tons of pic's, video, and txt files among other things. I'll have to try it again with my external drive as the output directory. I ran out of disk space cause like a dummy I used my home directory.

If anyone has any info specifically  about recovering dmg, img, and iso please let me know. Thanks

---

### Post by randy78 on 2008-02-12
> **iansane said:**
> Hey, that's a great program!! I haven't recovered the dmg file yet but it recovered tons of pic's, video, and txt files among other things. I'll have to try it again with my external drive as the output directory. I ran out of disk space cause like a dummy I used my home directory.

If anyone has any info specifically  about recovering dmg, img, and iso please let me know. Thanks

Just do a Google search for Linux File Recovery

You should be able to find some good stuff ;)

Take Care:)

---

### Post by spiderbatdad on 2008-02-12
Potentially a dangerous program for inexperienced users....fill home directory with 1000's of files that the user wont have permissions with, depending on how the scan is done.

---

### Post by iansane on 2008-02-17
> **spiderbatdad said:**
> Potentially a dangerous program for inexperienced users....fill home directory with 1000's of files that the user wont have permissions with, depending on how the scan is done.

Right. That's why I was glad I had the sense to watch my disk usage while it worked. I had no idea I had that many deleted files since the OS was a fresh install about a month ago. It recovered files from apps that had been removed too so there were thousands of pics and txt files.

I just used gksudo nautilus to view them in my home directory before I deleted them all again. 

It never did recover the image file I was looking for. Oh well, I'll just have to wait for the torrent to download again. 6 Gigs takes a long time to download.

---

