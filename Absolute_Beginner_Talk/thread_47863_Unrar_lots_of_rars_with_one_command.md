---
title: "Unrar lots of rars with one command"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Nasso on 2005-07-10
I got like 150+ rar files in one directory and i whould like to unrar them all at once. how do i do?

i have tried
> 
nasso@nasso:~/xx/yy$ unrar e *.rar

UNRAR 3.40 freeware      Copyright (c) 1993-2004 Alexander Roshal


Extracting from bb.rar

Skipping    bb.ss                             
No files to extract


it extracts the first file and then stops :/

---

### Post by UbuWu on 2005-07-10
I think this should do the job:

for i in *.rar; do unrar e $i;  done

---

### Post by rwabel on 2005-07-10
[QUOTE=Nasso]I got like 150+ rar files in one directory and i whould like to unrar them all at once. how do i do?

i have tried


it extracts the first file and then stops :/[/QUOTE]
 [unp]("http://ralph.n3rds.net/index.php?/archives/33-Extracting-multiple-archvies.html") does a a great job and not only for rar archives

---

### Post by Nasso on 2005-07-11
[QUOTE=rwabel][unp]("http://ralph.n3rds.net/index.php?/archives/33-Extracting-multiple-archvies.html") does a a great job and not only for rar archives[/QUOTE]
 omg! unp is SOOOOO sweeet! ^_^ this is a keeper! im never going to use anything else :) big thanks!

---

### Post by a_hippie on 2006-10-14
I agree.  I just installed "unp" and ran it on a movie archive.  Wow, it was too easy.

I love tools that just work!

Thanks loads for posting this message.

Wishing you well.

---

### Post by Hemmer on 2006-11-26
wow unp is so easy - thanks for the heads up! :D

---

### Post by 56phil on 2006-11-26
Thanks, Ralph. unp is really nice.

---

