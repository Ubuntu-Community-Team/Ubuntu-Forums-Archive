---
title: "Batch converting icons, help please?"
date: 2009-07-05
forum: Art &amp; Design
---

### Post by Fzang on 2009-07-05
I have a lot of .png icons. I need to batch resize them all into 20x20 and put "small-" in front of all names.

Is there something that can do that for me?

---

### Post by unutbu on 2009-07-05
Many people recommend Phatch (a GUI program) for doing batch resizing (and other operations). I don't know if it can rename the files too.

An alternative is to use the command-line:

Install the imagemagick package

Make a copy of the originals:
```

rsync -a /path/to/source/ /path/to/dest
```

Batch resize the pngs:
```

cd /path/to/dest
mogrify -resize 20x20! *.png

```
Rename the pngs:
```

rename 's//small-/' *.png
```

Note that if the image files end in .PNG rather than .png, then you have to change 'png' --> 'PNG' in the commands above. In other words, the commands are case-sensitive.

---

