---
title: "Filenames: &quot;_20&quot; to &quot; &quot;?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Aurdal on 2006-08-04
So, I've a lot of folders and files which have been named with "_20" instead of spaces. Does anybody know how I can change this fast? That is atleast semi-automatic...

Thanks
-Aurdal

---

### Post by professor_chaos on 2006-08-04
open a terminal and change to that directory and execute the following command. That should do it. 


```
for i in $( ls *_20* ); do x=`echo $i | sed 's/_20/ /'`; mv $i "$x"; done
```

---

### Post by Aurdal on 2006-08-06
Thanks, but I get this error message (where "_FILENAME_" is the name of the current file) for every file and directory:

```
mv: cannot stat `_FILENAME_': No such file or directory

```

---

### Post by professor_chaos on 2006-08-07
Can you paste the filename of one of the files you want to change as well as the proposed rename of that file. Perhaps I misunderstand exactly what you want.

---

### Post by Aurdal on 2006-08-09
Sure.

Say, one of my files is named "This_20is_20a_20file.ext". I would like that file to be named "This is a file.ext"

---

### Post by Tomosaur on 2006-08-09
rename s/_20/\ / *

should do the trick (use it while in the directory of the files you want to change, otherwise alter the wildcard to reflect where you actually are)

---

### Post by Aurdal on 2006-08-10
Thanks, I rewrote the first method to change the moving part to the rename method.

That did the trick. Thanks.

---

