---
title: "GIMP can't write thumbnails due to permission problem"
date: 2007-06-29
forum: Art &amp; Design
---

### Post by insert_name_here on 2007-06-29
I deleted all of the contents of the my .thumbnails folder (due to some poorly-organized torrenting, I couldn't log into X, and had to find something of significant size to delete from the recovery console).  Now, GIMP can't make thumbnails, and so when I open gimp, I get an error message: > Failed to open '/home/merrillj/.thumbnails/normal/gimp-thumb-3610-c672ef4f' for writing: Permission denied

How might I fix this?

---

### Post by jack@tortuga on 2007-06-29
Give  write permission to the owner of the .thumbnails and all lower directories/files.

```
chmod -R u+w /home/merrillj/.thumbnails
```

Make sure you're running Gimp as yourself ( I assume 'merrillj'. )

---

### Post by insert_name_here on 2007-08-15
that worked, thank you

---

