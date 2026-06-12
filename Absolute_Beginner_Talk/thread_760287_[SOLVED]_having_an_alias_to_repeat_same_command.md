---
title: "[SOLVED] having an alias to repeat same command"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by crazyfuturamanoob on 2008-04-20
I make scorched3d maps often, but to do that, 
I need to type twice gksudo nautilus. Im too lazy to
explain why, so I just get into the business:
I tried this:
```

alias gk=gksudo nautilus && gk sudo nautilus

```
It didn't work. For some reason
it ran only once. I want it to run twice.
So how to have alias "gk" to run 
twice command "gksudo nautilus"?

---

### Post by PointyWombat on 2008-04-20
put it in quotes like so:

```
alias gk="gksudo nautilus && gksudo nautilus"
```

---

