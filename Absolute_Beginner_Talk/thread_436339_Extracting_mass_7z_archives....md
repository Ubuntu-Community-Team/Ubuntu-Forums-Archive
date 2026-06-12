---
title: "Extracting mass 7z archives..."
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-07
Maybe someone can help. I am trying to extract a few hundred 7z archives in a folder. I navigate to the folder and try:

p7zip -d *

also tried:

p7zip -d *.*

and finally:

p7zip -d *.7z

Does anybody know the command line for mass extraction? Thanks!

---

### Post by zvacet on 2007-05-07
I don´t know if this will help you 

[file:///usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract_full.htm]("file:///usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract_full.htm")

---

### Post by qpwoeiruty on 2007-05-07
How about:

```
for i in `ls *.7z`; do p7zip -d $i; done
```

---

### Post by dpzektor on 2007-05-07
Thanks for the replies. For some reason I don't have the manual and while that code works, it only unzipped have of the files. I did have a brainstorm however. I installed Win32 7zip under Wine and was able to mass extract rather easily. Again, thanks for the input!

---

### Post by psusi on 2007-05-07
The command for 7zip is 7z, not p7zip.

---

