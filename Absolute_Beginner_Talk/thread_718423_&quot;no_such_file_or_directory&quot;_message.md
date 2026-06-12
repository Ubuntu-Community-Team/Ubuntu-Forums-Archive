---
title: "&quot;no such file or directory&quot; message"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Pawel Andrzej on 2008-03-08
I am an absolute beginner. Here's my absolute-beginner problem:

I downloaded a file called RealPlayer10GOLD.bin and placed it in a Downloads folder in the /home directory. Then, I tried to open the file using the following command:
[CODE] sudo ./RealPlayer10GOLD.bin [CODE]

In response, Terminal showed the following message:
[CODE] ./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory [CODE]

I wonder what "no such file" refers to -- the RealPlayer10GOLD.bin file (which *is* there) or the libstdc++.so.5 ?

Any advice on what to do to open the .bin file?

---

### Post by szymon_g on 2008-03-08
type

sudo aptitude install libstdc++5-dev

if you are using .bin files, try to run them like that

chmod +x file.run 
sudo sh ./file.run

---

### Post by darkworld on 2008-03-08
It was trying to run missing a library.

---

