---
title: "Remove file on mounted partition"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by bardic on 2008-02-04
Hey, 
I have a mounted NTFS partition and I want to delete some files. I know they delete to the .Trash-name and I've been able to delete it in the past. But today I tried to and it told me that the file couldn't be removed...

So I cd'ed there and was going to rm the folder...

sudo rm -r .Trash-bardic
rm: cannot remove directory `.Trash-bardic/***file name here****'': File exists

Any thoughts on why this happened?

---

### Post by oedha on 2008-02-04
how about -rf ?

---

### Post by logos34 on 2008-02-04
maybe it's mounted read-only for some reason?

---

### Post by bardic on 2008-02-04
i tried -rf also. 
And all the other files in the .Trash delete fine. Just one folder within it. 

It has me stumped...

---

### Post by oedha on 2008-02-04
just like logos34 said : maybe it's mounted ro
how if you make it not ro.....sudo chmod 777 /Trash-username ?

wonder : is there any program still using  deleted file(s) ??...hmmmm

---

### Post by bardic on 2008-02-04
just tried the sudo chmod and tried to delete again, but that didn't work. Same error as before. 
And no, nothing is using the file atm.

---

