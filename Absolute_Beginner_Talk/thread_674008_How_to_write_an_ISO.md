---
title: "How to write an ISO"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by markusgrey on 2008-01-21
Can someone give me a command line to burn ubuntu-7.10-desktop-i386.iso onto a cd?

---

### Post by BluePlum on 2008-01-21
hey i think you just right click the file and click burn to disk ( blank disk needs to be in there )

---

### Post by CupofDice on 2008-01-21
No need. Just right click on the iso and select Write to Disc or download GnomeBaker which is a burner with more options.

---

### Post by markp1989 on 2008-01-21
i used this and it seems to work, but i normaly do what the last few posts suggested 
```
cdrecord -v speed=47 dev=/dev/cdrom /path/to/file.iso 
```

---

