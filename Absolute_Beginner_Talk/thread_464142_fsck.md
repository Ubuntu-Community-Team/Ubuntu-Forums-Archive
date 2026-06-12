---
title: "fsck"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2007-06-04
this just started recently, about once or twice a day my ubuntu kicks itself into read-only mode and i cant do anything when i restart it starts scanning the HD for errors, and then it quits part way through and says i should run fsck manually so i type fsck and it does a series of scans comes up with something about a Buffer I/O error on dev/hda2 and then more errors about short reads and usually says something about incorrect inodes and bitmaps or something its becoming quite frequent and fairly annoying, i assumed after a few times of running it manually itd be fixed but it keeps happening I need some seriously help here, i backed up all my data in case i lose any but i dunno how to fix this ?

---

### Post by phr0ze on 2007-06-04
Your hardware could be failing. Is it taking longer to boot these days? If you listen closely to your computer do you hear some repeated clicking noises? Lastly, I'm not sure whats on that partition but you could try to reformat it. This may involve reinstalling Ubuntu.

---

### Post by gregcha117 on 2007-06-05
i had tryed reformatting it already and it hasnt stopped, when i run sudo badblocks alot of entires come up is there anyway to correct this or am i screwed?

---

### Post by southernman on 2007-06-05
You might be able to fix the drive using [SystemRescueCD]("http://www.sysresccd.org/Main_Page") (credit to Aysui, found the link in one of his how-to's)

Your definately about to loose a HDD, it sounds like.

---

