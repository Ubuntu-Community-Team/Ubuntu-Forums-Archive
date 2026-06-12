---
title: "How make ls only show directories?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Physicist on 2007-07-05
Hi, I want to find out all the directories in my home path, how do I do it?

And a following-up question is how do I change all the directories recursively to have permissions of 755?

---

### Post by Skrynesaver on 2007-07-05
```

find ~/ -type d -exec chmod 755 {} \;

```

---

