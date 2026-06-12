---
title: "Bash isn't working"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-04-26
I can no longer use ls, emacs or anything command line related.

---

### Post by auroraborealis on 2006-04-26
can you do `echo $PATH` ?

---

### Post by Silver-revo on 2006-04-26
yes I can

---

### Post by auroraborealis on 2006-04-26
What does it output?

---

### Post by Silver-revo on 2006-04-26
here is not much how do you reset it?
> clyde@PortableMAGIK:/$ echo $PATH
"/"


---

### Post by auroraborealis on 2006-04-26
Put this in your ~/.bashrc file

export PATH=:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

then do `source ~/.bashrc` or close the shell and open a new one.

---

