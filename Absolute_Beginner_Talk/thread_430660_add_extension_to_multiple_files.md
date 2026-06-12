---
title: "add extension to multiple files?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by MNR25 on 2007-05-02
Hello :)

I have a bunch of files without an extension, and I want to convert them all to .txt files

But i cannot figure out how to do this with the [ rename ] command (i tried man rename but dont get it)

I checked the "check if already posted" threads but dont seem to locate a similar problem

---

### Post by Cypher on 2007-05-02
Are all of these files within a single directory and do ALL of them need have the .TXT file, AND are there no other files in this directory that already have other extentions? If all of the above is true..then only
```

for file in `ls`; do mv $file $file.txt; done

```
If there are other files in this directory and you don't want to mess with, do not run this command..come back to us and sombody might have a better 'script'..

---

