---
title: "How do I find a file with a specific string in it in gnome?"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-12-12
How do I find a file with a specific string in it?

---

### Post by aysiu on 2006-12-12
```
grep -inr *string* /*directory/to/look/in*
``` For example, let's say you're looking for the string *uriah and cat* in your home directory files: ```
grep -inr "uriah and cat" ~/
```

---

