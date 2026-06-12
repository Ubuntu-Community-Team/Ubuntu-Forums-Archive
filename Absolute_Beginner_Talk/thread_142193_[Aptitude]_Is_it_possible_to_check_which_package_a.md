---
title: "[Aptitude] Is it possible to check which package automatically install 'packageA'?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-09
Suppose when I do a 'aptitude search packagesA',  the following line is returned:

i A packageA - packageA description.

As shown above, packageA is automatically installed by another package. Is there a way to check with aptitude what is the package that install packageA automatically?

Thanks !

---

### Post by Xian on 2006-03-09
I don't know about aptitude, but apt-file should handle this.
For example:

```
$ apt-file -l search dprofpp
libgraphviz-perl
perl
```

---

