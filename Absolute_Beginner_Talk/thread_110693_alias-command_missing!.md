---
title: "alias-command missing!"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by bernoulli on 2005-12-31
Hi, i just installed Ubuntu a few days ago, and i like it very much. However; for some reason i dont have the "alias" command on my computer! I try "man alias" and it says "No manual entry for alias". I try "alias list 'ls -l | more'", but i just get some "command not found"

What should i do?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=bernoulli]Hi, i just installed Ubuntu a few days ago, and i like it very much. However; for some reason i dont have the "alias" command on my computer! I try "man alias" and it says "No manual entry for alias". I try "alias list 'ls -l | more'", but i just get some "command not found"

What should i do?[/QUOTE]
"alias" is built into the bash shell.  From bash, try:
```

$ help alias

```

---

### Post by bernoulli on 2006-01-02
Ok, i found it out. I didn't realize that the aliases dissappear when you log out, and i have to use the syntax: alias new='command'. I simply put the commands i need at the .bashrc file in my home-directory (or in /etc/bash.bashrc so that it affects all users)

I found this site to be useful:
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

