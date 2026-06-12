---
title: "Terminal commad question"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by erkker on 2007-01-28
Hello all,

I have gotten a XP - Edgy dual boot up and running and I never give XP a thought unless I have to run one or two programs.  And this is a silly question perhaps but...

what is the difference between

~/.icewm/themes

and 

~/icewm/themes

In other words what does the "." do??


Thanks
-E

P.S. - how do you list all running processes from a terminal window??

---

### Post by goatflyer on 2007-01-28
File and directory names starting with '.' are "hidden'.  They don't show up on 'ls', but they do show up on 'ls -a'

Same with nautilus, you have to 'show hidden' in order to see names starting with '.'

---

### Post by thelinuxguy on 2007-01-28
List all running processes:
```
sudo ps -A
```

---

