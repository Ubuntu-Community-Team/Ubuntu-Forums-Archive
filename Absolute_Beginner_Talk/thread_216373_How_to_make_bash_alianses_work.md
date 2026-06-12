---
title: "How to make bash alianses work?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Xecuter on 2006-07-15
How do I make bash alianses that are saved to a file (.bash_alianses) work?

---

### Post by infoburner on 2006-07-15
do you mean bash aliases?
for example "alias 'ls'='ls -la'"?
one thing you could do is append them to then end of your ~/.bashrc
if you want to have a single alias file that has nothing but aliases in it you could do something like this:
```

----- ~/.bash_aliases -------
#!/bin/bash
alias 'ls'='ls -la'
alias 'rm'='rm -i'

----- append to ~/.bashrc --------
~/.bash_aliases

```
and then run "chmod +x ~/.bash_aliases" and the next time you boot up those aliases should be remembered

---

### Post by Kurt` on 2006-07-15
Thanks for that post infoburner, I forgot that my aliases file needs to be executable!

---

### Post by Xecuter on 2006-07-15
> **infoburner said:**
> do you mean bash aliases?

Wooops :oops: Well, there might be an alianse between the bashes. (I don't know.)

Anyways, thanks! :D

---

### Post by infoburner on 2006-07-15
glad to help :)

---

