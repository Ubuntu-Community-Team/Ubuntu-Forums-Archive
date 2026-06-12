---
title: "Simple Script"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-25
does anyone know if i could write a script in which i can do this...

i have a text file with 15 links to videos in it. they are separated by a line break
i want to use wget to download them to my home directory

any guidance on how this could be done if at all?

---

### Post by 23meg on 2007-01-25
You don't need a script; you can use wget's -i option to do it. ```
wget -i /path/to/file
```

---

