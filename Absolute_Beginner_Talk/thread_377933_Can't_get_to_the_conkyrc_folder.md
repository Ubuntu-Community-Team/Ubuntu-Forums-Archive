---
title: "Can't get to the conkyrc folder"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by IgnacioMiller on 2007-03-06
I can't figure out how to get into my conkrc folder. When I do an ls -A in my home folder I see conkyrc and conkyrc~. But when I try to cd conkyrc or conkyrc~ It tells me:

dan@dan-desktop-linux:~$ cd conkrc
bash: cd: conkrc: No such file or directory

What am I doing wrong?

Thanks in advance,
Ignacio

---

### Post by Waappu on 2007-03-06
Hi

I think conkyrc is file not folder. Sorry if I'm wrong or don't understand your probelm.
See if these links can help you
[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky+howto](http://ubuntuforums.org/showthread.php?t=205865&highlight=conky+howto)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Brunellus on 2007-03-06
.conkyrc is not a directory.  it is a file.  the dot at the start of the name is significant:  all files that begin with dots are hidden unless you look for them specifically with ls -a

remember, once again it's

.conkyrc

NOT

conkyrc

---

### Post by IgnacioMiller on 2007-03-06
Ah, haha, that would explain why I can't cd into it. Thanks for the help guys! :D

---

