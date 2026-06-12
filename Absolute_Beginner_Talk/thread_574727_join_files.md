---
title: "join files"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by jayaramk on 2007-10-13
i downloaded files from the internet... mostly a video file which is made split using the hjsplit...... now inorder to join them in ubuntu i need something?? can i know how could i join files in ubuntu.... bcozzzzz i completely shifted to ubuntu and there's no windows in my system!!!!

---

### Post by mali2297 on 2007-10-13
HJSplit is cross-platform. You can find different versions here:
[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

One option is to use the Java version, download hjsplit_g.jar and run from the terminal:
```

java -jar hjsplit_g.jar

```
and you get a simple graphical interface. Of course, you need to have Java installed.

---

### Post by BennBuntu on 2007-10-13
I know it's possible with cat, but not sure if it will come out the same
if they've been split by another program

open a terminal

cat file1 file2 > outputfile

where file1 and file2 are the names of the two halves, and outputfile is the name you want on the output file.

can also have more than 2 files going in.

[http://lowfatlinux.com/linux-join-files-cat.html]("http://lowfatlinux.com/linux-join-files-cat.html")

edit: mali beat me to the punch, his method looks better

---

### Post by vanadium on 2007-10-13
If hjsplit indeed does just binary split the file, then cat will be a proper way to combine the parts again.

---

### Post by richwillal on 2008-01-08
If it helps anyone, you can also use cat combined with xargs and sort to make things a little easier:

find . -name file1*.ext.0?? | sort | xargs -s '{}' cat '{}' >> outputfile.ext

If you test the line up through sort (find . -name file1*.ext.0?? | sort) to make sure each line contains the files you want in the right order, it sometimes makes things easier.  I've tested this with files split using hjsplit and it joins them back just fine.

RDW

---

