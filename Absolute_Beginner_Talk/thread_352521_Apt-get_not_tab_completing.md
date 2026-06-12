---
title: "Apt-get not tab completing"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Blond_Knight on 2007-02-03
Hey guys I really pride myself on trying to search the forum and avoid posting unless I cant find the answer.

My problem is Im running three Ubuntu 6.10 servers, two at home and one at work.  On one of the servers when I try to run apt-get it doesnt tab complete.  Usually when I type apt-get and hit tab it gives me the list of options (install, remove, update, upgrade, etc).  Then when I type in a few letters of the package I want to install and hit tab it will give me a list of possible matches.  However on this server when I type apt-get and hit tab is shows me the contents of the current directory.
Anyone seen this before?

---

### Post by Regel on 2007-02-03
I think that's what it's supposed to do.  Use apt-cache search to look for packages.

---

### Post by lamego on 2007-02-03
The the default bash shell tab auto completes with filenames/directories not with command options as you believe it did. You were probably doing some confusion.

---

### Post by Rui Pais on 2007-02-03
> **lamego said:**
> The the default bash shell tab auto completes with filenames/directories not with command options as you believe it did. You were probably doing some confusion.

hi, not exactly... what Blond_Knight actually said it was tab completion for possible packages, not filenames or directories ;)

Blond_Knight you probabilly need to comment out or add to your .bashrc:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

---

### Post by Blond_Knight on 2007-02-03
> **Rui Pais said:**
> Blond_Knight you probabilly need to comment out or add to your .bashrc:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```
Thank You my Portugese friend,
Thats exactly what it was, I just had to uncomment that in bash.bashrc and log back in and its doing like it should.  Regel's suggestion is good too, if you say apt-cache search all |sort > packages.txt it gives you not only the package listing but a short description of what the thing is. 
Back to lurk mode. ;)

---

