---
title: "Only find files, not directories with find"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-05-25
Hello. Iv runed the command find * | wc -l to count
all the files and folders in the standing directory.

Question 1.)
How do I only count files and exclude counting directories ?

Question 2.)
How do I count only directories and exclude counting files ?

---

### Post by nalmeth on 2006-05-25
type "man" before the command (exluding your directories and such) to bring up the manual for the program

example:

man aptitude

---

### Post by DeadEyes on 2006-05-25
-type d
for directories

c character
d directory
l link

for others try **man find**

---

