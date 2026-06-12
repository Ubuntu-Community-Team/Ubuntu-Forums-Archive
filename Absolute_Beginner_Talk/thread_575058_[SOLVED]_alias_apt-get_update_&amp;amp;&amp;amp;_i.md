---
title: "[SOLVED] alias apt-get update &amp;amp;&amp;amp; install"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-10-13
Hi all,


  Would it be safe to create these aliases?


```
########################
### personal aliases ###
########################

# Basics
alias cp='cp -v -i'
alias rm='rm -i'
alias mv='mv -i' 
alias utar='tar -xvf'
alias utarz='tar -xzvf'
alias tarz='tar -czvf'

# SSH
alias ssh-pluto='ssh user@IP -p 224'
alias ssh-server='ssh user@IP'
alias ssh-smooth='ssh user@IP -p 222'
alias ssh-maite='ssh user@IP'

# Software Management
alias aptl='sudo apt-get update && sudo apt-get install'
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias inst='sudo apt-get install'
```


Thanks,

Vic.

---

### Post by bodhi.zazen on 2007-10-13
yes you should be fine ...

---

### Post by victorbrca on 2007-10-13
Thanks!!  :)

---

### Post by victorbrca on 2007-10-14
I have another one. Would the following alias be ok as well:

```
alias gnome-terminal='gnome-terminal --geometry 104x32'
```

I would like to have all my terminal windows opening with that specific size!!!

**Edited** - Or should I add "--geometry 104x32" to preferred apps?

Thanks,

Vic.

---

### Post by bodhi.zazen on 2007-10-15
Either should be just fine :)

---

### Post by victorbrca on 2007-10-15
> **bodhi.zazen said:**
> Either should be just fine :)

Thanks again!!!  :)

---

