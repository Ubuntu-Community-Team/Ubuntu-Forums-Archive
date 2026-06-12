---
title: "Downloading files from the internet from the command line"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-08-28
Is there a way to download files from the internet (not HTML files, mp3 and that stuff) from the command line? The problem is that I have to download 40 files named 1.mp3, 2.mp3, etc. and its a tedious work with firefox.

---

### Post by Mornedhel on 2007-08-28
wget does what you want, but it will not bypass robots.txt, so you may have to call it again and again to download an entire folder instead of being able to use the handy recursive option. Or, you could write a Perl/Python/sh script around to retrieve the directory, extract the links, and match against mp3 files or jpg or whatever. PM me if you want an example of how it might be done in Perl.

---

### Post by HereInOz on 2007-08-28
Have a look at wget.

Type:

man wget

in a terminal and read up on it.  It may do what you want it to do.

---

### Post by eeeeepuk on 2007-08-28
The wget command will let you do so, though I don't believe it supports wildcards, meaning you'll still have to download each file inidividually (I'm sure someone will correct me quickly enough if it does)

---

### Post by por100pre1 on 2007-08-28
wget should be useful. Read wget manual:

```
man wget
```

(Press q when finished)

EDIT: Sorry, too late...

---

