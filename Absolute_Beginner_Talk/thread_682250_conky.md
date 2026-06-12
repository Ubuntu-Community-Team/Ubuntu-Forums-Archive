---
title: "conky"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2008-01-29
I have a question how would I move my conky up and on the right side?

---

### Post by spiderbatdad on 2008-01-29
you would edit .conkyrc,  a hidden file in your home directory...also there is a great conkyrc thread to check out.[http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=.conkyrc)

---

### Post by bcrom on 2008-01-29
Open .conkyrc in your home directory (It's hidden, press Ctrl+H to reveal it) find the line that says "alignment" and change it to line ```
alignment top_right
```

Uncomment the line if it has a '#' character in front of it, and if you can't find the line at all, just add ```
alignment top_right
```
 to the beginning of the file.

---

