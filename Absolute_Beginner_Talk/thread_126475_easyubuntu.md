---
title: "easyubuntu"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by synnr on 2006-02-06
First time to use linux, and i like it very much so far.  Ubuntu had made it about as easy as can be.  But i'm still linux dumb.  That said, I'm stuck on how to install software not in the standard library of programs.  I ran across easyubuntu and downloaded it.  So now i have the easyubuntu-latest.tar.bz2.  I know this is a compress file, but what the heck to i do with it now.  I've tried uncompressing it, but I just don't know what to do next.  Thanks in advance.

---

### Post by nik on 2006-02-06
Well, wht did you get from extracting it? I'm guessing something called easyubuntu.sh?
If so, you need to make it executable

chmod +x easyubuntu.sh (or whatever)

and then probably run it

./easyubuntu.sh

you might have to run it as root (don't know with that script)

sudo ./easyubuntu.sh

EDIT: If you didn't get to extract it, it should work in file-roller (just double-click the compressed file and choose extract)

---

### Post by robotgeek on 2006-02-06
[QUOTE=synnr]First time to use linux, and i like it very much so far.  Ubuntu had made it about as easy as can be.  But i'm still linux dumb.  That said, I'm stuck on how to install software not in the standard library of programs.  I ran across easyubuntu and downloaded it.  So now i have the easyubuntu-latest.tar.bz2.  I know this is a compress file, but what the heck to i do with it now.  I've tried uncompressing it, but I just don't know what to do next.  Thanks in advance.[/QUOTE]

These steps should get you up and running. 

```

cd 
mkdir easyubuntu
cd easyubuntu
wget http://easyubuntu.freecontrib.org/EasyUbuntu-lastest.tar.bz2
tar -jxf easyubuntu-lastest.tar.bz2
gksudo ./easyubuntu.py

```

---

