---
title: "Changing folder in Terminal with Name &quot;abc def&quot;"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-17
Hi,

I want to change to a folder in the terminal. The problem is that the folder name contains a space.

"cd abc def" is not working.

What is the correct syntax?

---

### Post by Orivel on 2008-01-17
You must use a backslash followed by a space. In the example you used, to change to "abc def" you would use ```
cd abc\ def
```

---

### Post by ben22 on 2008-01-17
thx

---

### Post by bodhi.zazen on 2008-01-17
Or use quotes

cd "abc def"

Or use tab completion

cd ab<tab> which yields cd abc\ def

---

