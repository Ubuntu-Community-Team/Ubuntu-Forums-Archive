---
title: "display first line of output"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-28
How do I just display the first line of an output...

i.e.:

```

a='locate "file"'

```
would only make a= to the first line of the output of locate "file"

---

### Post by nick_h on 2007-10-28
Use the head command.
```
locate "file" | head -1
```

---

