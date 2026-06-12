---
title: "how to unzip"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by slenny on 2006-09-22
I have downloaded a file, but I am unable to unzip it.  Any ideas?


admin@slim:~/Desktop$ uname -a
Linux slim 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux
admin@slim:~/Desktop$ **unzip apex_2.2.1.zip**
Archive:  apex_2.2.1.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of apex_2.2.1.zip or
        apex_2.2.1.zip.zip, and cannot find apex_2.2.1.zip.ZIP, period.
admin@slim:~/Desktop$

---

### Post by goatflyer on 2006-09-22
It says the zipfile is not a complete archive, but only part of one.  You need the other files from the set (from wherever you got your original zipfile).   Or, you just need to find another zipfile which has all parts in the one.

---

### Post by Papa-san on 2006-09-22
The other possibility is that it was just renamed as a .zip file, without actually being one. I know doing this sometimes works with driver files, but as for others, I don't know.

---

### Post by szf on 2006-09-22
How about
[FONT="Courier New"]$ file apex_2.2.1.zip[/FONT]

What does that tell you?

---

### Post by deadgobby on 2006-09-22
Or you can unpack the zip by using archive manager or right click the mouse on the icon scroll down to extract here. 
Gobby
Crips tiem to work 3rd shift. OH JOY!!!!

---

