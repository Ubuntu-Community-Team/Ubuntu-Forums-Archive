---
title: "Navigating pass home directory in terminal problems"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-02
This may seem like incredibly stupid question to most of you, however, I am having trouble getting to any directories past my home directory. 

for example, in terminal, when I type"cd /home/martin/documents"   I get a message that says "no such file or directory". I can get to any directory outside of my home directory, such as say "cd /bin" or "cd /dev", and any directory within those directories. I just can't get past my home directory (/home/martin). What am I doing wrong?

---

### Post by jken146 on 2007-12-02
You can use the ```
ls
``` command to list the contents of any directory.
You can also type ```
gksudo nautilus
``` to get a file browser with root permissions.

Check that your directory /home/martin/documents actually exists.

---

### Post by totalnub on 2007-12-02
linux is case sensitive. watch out for that.

```
cd ~/Desktop
``` (not desktop) or ```
cd Documents
``` from inside home folder

---

### Post by fmbugdadi on 2007-12-02
oh, ok, duh, that worked form me. I was not worrying about lower  case or upper case.thanks again guys...

---

