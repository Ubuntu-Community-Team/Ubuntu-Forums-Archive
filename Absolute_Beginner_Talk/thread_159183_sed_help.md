---
title: "sed help"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-04-12
```
echo testing.foo | sed 's/.*\.//'
```
How do I get it to print '.foo'?  I take out the period in the command, it would not work.  What way is there to get around it?

---

### Post by xenmax on 2006-04-12
Make your replacement the dot '.' instead of null
```
echo testing.foo | sed 's/.*\././'
```

---

