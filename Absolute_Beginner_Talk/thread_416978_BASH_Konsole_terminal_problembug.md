---
title: "BASH Konsole terminal problem/bug ?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by thedoors on 2007-04-21
Here's my problem :
I am using this as PS1
```

PS1='${debian_chroot:+($debian_chroot)}[\u@\h \W]\[\033[31;40m\]$\[\033[0m\] '
```
It appears as 
[username@hostname ~][COLOR="Red"]$[/COLOR] command
Which is what i want.. but
when something is printed at the terminal without a newline eg, 

[username@hostname ~][COLOR="Red"]$[/COLOR] echo -n "test"
[username@hostname ~][COLOR="Red"]$[/COLOR] ~][COLOR="Red"]$[/COLOR]
[username@hostname ~][COLOR="Red"]$[/COLOR] echo -n "testing"
[username@hostname ~][COLOR="Red"]$[/COLOR] me ~][COLOR="Red"]$[/COLOR]

This does not happend with this PS1:
```

PS1='${debian_chroot:+($debian_chroot)}[\u\[\033[31;40m\]@\[\033[0m\]\h \W]$ '

```

What am i doing wrong ?

---

### Post by thedoors on 2007-04-22
Any ideas?

---

### Post by Pobega on 2007-04-22
I really don't even understand the question. Maybe try explaining it a bit more?

---

### Post by thedoors on 2007-04-22
Okay here's a picture, i hope you understand the problem now
[img]http://xs314.xs.to/xs314/07160/problem.jpg[/img]

ps. i like your signature :P

---

