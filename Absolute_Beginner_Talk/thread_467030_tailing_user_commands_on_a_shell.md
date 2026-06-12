---
title: "tailing user commands on a shell"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by imsmark on 2007-06-07
im looking for a  software package to tail all commands of users for my server. so i can make sure the users are not doing anything wrong on my box. basically, i want to see whats going on for each and every person.

---

### Post by Cypher on 2007-06-07
A little paranoid, huh? :)

Anyway, BASH keeps a history of all commands typed. So if you were to type "history" you will get a list of commands. You can control the number of commands logged by modifying the environment variable HISTFILESIZE, with something like
```

export HISTFILESIZE=2000

```
in the global "/etc/profile" file. 

The commands are also stored in the ".bash_history" file in each user's home directory. So as Root, you could take a look at the commands.

---

### Post by imsmark on 2007-06-07
i know that about .bash_history... i mean tailing and keeping track of all users... bash history can be deleted!

---

