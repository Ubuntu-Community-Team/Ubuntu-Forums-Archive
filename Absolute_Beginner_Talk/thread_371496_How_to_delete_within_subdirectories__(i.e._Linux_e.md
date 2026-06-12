---
title: "How to delete within subdirectories?  (i.e. Linux equivalent of del *.ext /s)"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-02-27
Basically what the title said, a rm equivalent of del *.ext /s from Windows.

I want to be able to delete all files of a certain extension within the current and all subdirectories.

---

### Post by Adramelech on 2007-02-27
rm -R *.ext

man rm for more options

---

### Post by AncientPC on 2007-02-27
I did man rm.  The -r / -R options are used to remove directories, not traverse within them.

If I have:
~/1.txt
~/test_dir/2.txt

Running "~/rm *.txt -r" will only delete 1.txt and not 2.txt.

---

### Post by Adramelech on 2007-02-27
You are right, sorry :(

try this way:

find . -name '*.txt' | xargs rm

---

### Post by AncientPC on 2007-02-27
Thanks, that worked perfectly!

---

