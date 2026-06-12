---
title: "imagemagick resize help"
date: 2007-04-22
forum: Art &amp; Design
---

### Post by steharg on 2007-04-22
i am trying to resize a load of images so they are no more than 150x150px

i am currently using

```
convert -resize 150x150\> *.jpg
```

but it is renaming all the files to that of the last image then adding a number after each one...
lastfilename.jpg.1
lastfilename.jpg.2
etc

how can i get it to keep its original file name? or even go back over to rename it without the numbers on the end?

---

### Post by kidders on 2007-04-23
Hi there,

The behaviour you describe is what you would expect, bearing in mind that "*.jpg" would be expanded by Bash into a list of matching filenames, the last of which **convert** will use as its output file. (See **convert**'s man page.)

You could try using **find**, or a **for** loop, so each **convert** command would only have two filenames in it.

---

