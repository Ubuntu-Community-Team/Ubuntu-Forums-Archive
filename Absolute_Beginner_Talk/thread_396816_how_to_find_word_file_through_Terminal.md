---
title: "how to find word file through Terminal"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-03-29
I created, naively, a word file using gedit (text editor), I named it ".bash_aliases_ 
how do I find this, and delete it, I forgot where I saved it too.

---

### Post by Parasitesss on 2007-03-29
this is what I get:

john@john-desktop:~$ cat .bash_aliases
alias cp='cp -i'
alias ln='ln -s'
alias mv='mv -i'
alias rm='rm -i'

doesn't this mean that .bash_aliases exsists?
if so, how do I delete this arbitrary file?

---

### Post by chili555 on 2007-03-29
Do:```
sudo updatedb
locate .bash_aliases_
rm /path/to/.bash_aliases_
```updatedb will take a few seconds or more, depending on the size and number of your files. Good luck!

---

### Post by Parasitesss on 2007-03-29
thanks much,

---

### Post by qpwoeiruty on 2007-03-29
This should do it

sudo updatedb
locate .bash_aliases
rm -i <path to bash aliases file that you made>

Ed: Beat to it!

---

### Post by zvacet on 2007-03-30
```
whereis filename ls
```

---

### Post by freebird54 on 2007-03-30
Nice answers you guys - for finding a lost file.  However - he can CAT that file right where he is - so:

```
rm .bash_aliases
``` or

```
sudo rm .bash_aliases
```

if it refuses to go away.  Those should remove it just fine.  I suspect the 'hidden' file worked on him just fine. :D

also this might help..

```
ls .b*
```

would have shown him what he made... along with a few other things no doubt.

---

