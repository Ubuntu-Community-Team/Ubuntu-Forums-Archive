---
title: "awk list"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by eliora on 2007-06-18
i have a directory with files that are of the format    number.word.word
some of the numbers are the same and i want to make a file list but only of the numbers
and using uniq

something like 
ls -1 awk -f ` { print $1 } > filename
where $1 is the number

ie 

directory contians
11290329.JUH.IUQ
11290329.ASD.QWE
2138209318.EWQ.OFD
2138209319.WEW.PRW


i want file list of
11290329
213809318
213809319

---

### Post by Damanther on 2007-06-18
the command 'uniq' should be available on pretty much any linux distro

use your awk command and pipe it through uniq like this

ls -1 awk -f ` { print $1 } | uniq > filename

---

