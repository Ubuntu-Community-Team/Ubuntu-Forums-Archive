---
title: "maximum number of files in a directory"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by dacium on 2008-02-09
What is the maximum number of files allowed in directory?

I have some code running now and I expect it to finish with about 35,000 output files all about 50kb each. Will this cause problems with the file system? What is the maximum I can go to? My next level of code will need to split each of those to 15 files, for a total of about 500,000 files in one directory.

---

### Post by asmoore82 on 2008-02-09
at a certain point, you lose the ability to view the files graphically via `nautilus`,
the GNOME "explorer" "file broswer"
but I don't think it would be a problem for the rest of the OS.

when this did happen to my `nautilus`, it gave a graceful error message, no major meltdowns.

---

### Post by asmoore82 on 2008-02-09
if not *top secret*, what purpose does your code serve?

---

### Post by Christmas on 2008-02-10
It's probably 32 000. From [here](http://lists2.ssc.com/pipermail/linux-list/2007-October/029383.html). It says to look after this define EXT3_LINK_MAX in /usr/include/linux/ext3_fs.h.

---

