---
title: "Making HTML files non executable"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by shafin on 2007-07-30
How do I make all HTML files non executable?Its really annoying as each time I want to open one,I've to go through the dialog or right click and disable execution

---

### Post by troos on 2007-07-30
try chmod 666 <filename>

---

### Post by shearn89 on 2007-07-30
you could probs do it with a script - i'll get back to you...

---

### Post by shearn89 on 2007-07-30
here we go - try this; make a file called htmlscript, and put this in it:
```

#!/bin/bash
locate *.html | while read line; do chmod -x ${line}; done

```
If you want it to be system-wide, cd to / and run it "sudo"

You'll have to chmod +x it first.

---

### Post by asmoore82 on 2007-07-30
are these HTML files on a UNIX partition or on NTFS/FAT?

---

### Post by shafin on 2007-07-30
> **asmoore82 said:**
> are these HTML files on a UNIX partition or on NTFS/FAT?
Both types

---

### Post by shafin on 2007-07-30
> **shearn89 said:**
> here we go - try this; make a file called htmlscript, and put this in it:
```

#!/bin/bash
locate *.html | while read line; do chmod -x ${line}; done

```
If you want it to be system-wide, cd to / and run it "sudo"

You'll have to chmod +x it first.
Thanks a lot

---

### Post by shearn89 on 2007-07-31
no trouble - i didn't actually know it off the top of my head, but any chance to learn a little bash script is always welcome!

---

### Post by asmoore82 on 2007-07-31
> **shafin said:**
> Both types

files on NTFS/FAT partitions will always show as executable because NTFS/FAT can't store UNIX file permissions

---

