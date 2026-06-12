---
title: "How do I use more than 1 'if'?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-12
```

if [ -f file1 ]; then echo "file1 is present"
if [ -f file2 ]; then echo "file2 is present"
if [ -f file3 ]; then echo "file3 is present"
else echo "no files present"
fi

```
Only one of the file* would be present or none are.  So there is only 4 choices to echo back.

The problem is, the code above would not let me use more than 1 if.  How do I extend it the ifs?

---

### Post by kidders on 2007-02-12
Hi there,

I'm not quite sure what you're trying to achieve. "Only one files is present, or none is" = 2 choices (rather than 4). :confused: How does this look? ...

```
if [ -f file1 -o -f file2 -o -f file3 ]; then
	echo "file 1, 2 or 3 is present"
else
	echo "no files present"
fi
```

---

### Post by mr.v. on 2007-02-12
This isn't exactly "Absolute Beginner Talk" but it looks like you have a syntax problem. I apologize but I can't understand exactly what you're trying to do,  but first of all, each **if** needs a corresponding **fi** Also remember you need to enclose multiple statements in { } if, for instance, you meant to nest those if statements which it appears that did, you have forgotten a bunch of **fi**s.

Say each one is independent then you need the following and assuming the files are variables (you need to prefix variable names with $ to the front)
```

#! /bin/bash
if [ -f "$file1" ]; then
    echo "$file1 is present"
fi
if [ -f "$file2" ]; then
   echo "$file2 is present"
fi

```
now to see if none are present you can use an AND list with the not operator
```

if [ ! -f "$file1" ] && [ ! -f "$file2" ] && <file 3, 4, 5 etc etc etc>
then
   echo "none of the files were present"
fi
```

---

