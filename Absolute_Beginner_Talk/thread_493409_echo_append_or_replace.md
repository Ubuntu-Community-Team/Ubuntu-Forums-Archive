---
title: "echo: append or replace?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-07-05
Hi. If i were to do a command like ```
echo "foo bar" > ~/foo
``` Would it append foo bar to the file or replace the contents of the file with foo bar?
I was thinking of making a command to add repos to my sources.list from the terminal.

---

### Post by capitalistpiglet on 2007-07-05
That will overwrite the file with "foo bar" to append it to the end of the file this is what you want
```

echo "foo bar" >> ~/foo

```

---

