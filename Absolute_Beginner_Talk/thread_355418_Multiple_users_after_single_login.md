---
title: "Multiple users after single login?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Trebaruna on 2007-02-07
Just a quick question by a puzzled user. By now I feel I am getting more acquainted with Ubuntu, but I recently noticed something:

When I type users into the terminal it tells me I am logged in twice. Before I rebooted just now it even told me there were four instances of me.

Could anyone please tell me why/what that is? Also, is there a way to see which instance is doing what? top only lists the user, but that obviously won't help seeing as how they're all the same.

I expect this is perfectly normal and that I am overlooking something critically simple and straightforward, but I can't seem to be able to figure out the right keywords to search with.

---

### Post by taurus on 2007-02-07
When you log in, there's one.  And when you open a terminal, that's two.  And if you have two terminals open, than that's three.  I think you get the idea.  From a terminal, see how many sessions you have with

```
finger -l
```

---

### Post by Trebaruna on 2007-02-07
Ah, that makes a lot of sense, thanks :)

---

