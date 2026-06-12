---
title: "[SOLVED] File Shred without the -u option.  Purpose"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Kappity on 2007-12-01
When looking for a secure delete option, I found several threads about the "shred" command.  I played around with it and it works, but there's something I'm curious about.

You have to use the -u option to remove a file after shredding.  For example "shred myletter.txt" overwrites the file with random nonsense, but I have to do "shred -u myletter.txt" to remove the file after shredding it.

Why would you want to shred the file if you weren't going to get rid of it?  If you shred it without removing it, can it still be recovered somehow?

---

### Post by aun on 2007-12-01
I have wondered the same.  Actually the answer is in the man page:

> Delete FILE(s) if --remove (-u) is specified.  The default  is  not  to
       remove  the  files because it is common to operate on device files like
       /dev/hda, and those files usually should not be removed.  When  operat-
       ing on regular files, most people use the --remove option.

[http://www.linuxcommand.org/man_pages/shred1.html]("http://www.linuxcommand.org/man_pages/shred1.html")

---

### Post by Kappity on 2007-12-01
> **aun said:**
> I have wondered the same.  Actually the answer is in the man page:



[http://www.linuxcommand.org/man_pages/shred1.html]("http://www.linuxcommand.org/man_pages/shred1.html")

I see.  So the "file" might represent an actual device or partition, and you want to leave that in place, scrambled data or not.  It's scary when this stuff actually begins to make sense. :)

---

