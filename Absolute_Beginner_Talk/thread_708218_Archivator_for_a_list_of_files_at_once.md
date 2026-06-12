---
title: "Archivator for a list of files at once"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Julita on 2008-02-26
Dear all, is it possible, using, for example, 7zip, to work with a list of files simultaneously (one-line command)? E.g., create archives?

---

### Post by es@urito on 2008-02-29
If you need to archive multiple files at ones you can do it simply using tar and gzip/bzip.
It's the fastest and easiest way:

```


tar cvfz archive.tgz file1.txt file2.txt file3.txt


```

Have a look at tar handbook 

```
man tar
```

For other useful options you can use. Remember that you can use tar in combination with other compression utilities thanks to the power of the bash shell.

Good luck!

---

### Post by Julita on 2008-03-11
Es@urito, thank you very much!!!

---

