---
title: "Sort command information."
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by ce41635 on 2006-11-03
I need some information about the requirement of the unix sort command. I have to sort a 20Go file and i need to know the disk space required  for sorting this big file. 

I also need to know the disk space requirement for sorting a 30Go file, during the creation of the temporary file.

Thank's for your help.

---

### Post by po0f on 2006-11-03
ce41635,

You can [split](http://unixhelp.ed.ac.uk/CGI/man-cgi?split) the files before you [sort](http://unixhelp.ed.ac.uk/CGI/man-cgi?sort) them, might make it easier on memory.  :)

Sort also has a [FONT="Courier New"]--buffer-size=SIZE[/FONT] argument that looks like what you're looking for as well.

---

### Post by jpeddicord on 2006-11-03
As po0f said, ```
sort --buffer-size=SIZE
```should work for this. Just remember that it will take a long time. Try using this for the buffer:```
sort --buffer-size=256K
```

Jacob

---

### Post by ce41635 on 2006-11-08
Thank's for your answser. But what i need to know is the disk space required during the sorting process of the 30Go file.  After some research on the internet, i never find the disk space required for the temporary space during the sort process.

Thank's.

---

