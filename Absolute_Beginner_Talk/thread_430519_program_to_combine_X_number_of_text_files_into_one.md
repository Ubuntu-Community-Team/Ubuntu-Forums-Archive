---
title: "program to combine X number of text files into one?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by uncreative on 2007-05-02
Hi,

Is there a program in Ubuntu that combines X number of text files into one large text file?  A few years ago when I was on windows I had something to do this, but....windows has been long gone for a while now.

Anyway, thanks in advance for the help!

---

### Post by riminicat on 2007-05-02
copy and paste

---

### Post by uncreative on 2007-05-02
> **riminicat said:**
> copy and paste


Was this really necessary?  I was very clear in what I was asking for, so if you don't have a serious reply please just move on.

---

### Post by xwipeoutx on 2007-05-02
If you're happy to use the command line you can do the following:
```
cat file1 file2 file3 > joinedfile
```

which will join file1 file2 and file3, putting them into joinedfile

obviously, change the filenames for your purpose

---

### Post by Jonne on 2007-05-02
in the command line:

file1.txt >> allofthem.txt

you can write a loop if they're all in the same directory. Basicly >> tells linux to concatenate the contents of file1.txt to the end of allofthem.txt

---

### Post by uncreative on 2007-05-03
> **xwipeoutx said:**
> If you're happy to use the command line you can do the following:
```
cat file1 file2 file3 > joinedfile
```

which will join file1 file2 and file3, putting them into joinedfile

obviously, change the filenames for your purpose


Perfect thank you.

And Jonne thank you as well -- This is for a web based app so I am goign to write a little php script to do what I need.

Thanks again Ubuntuers for the great help

---

### Post by Jonne on 2007-05-03
If you're going to use php anyway, you can use this: [http://www.tizag.com/phpT/fileappend.php](http://www.tizag.com/phpT/fileappend.php)

The bash shell supports looping and variables too, you could look into that. I'm a n00b in bash, but there's a lot you can do in bash without using another scripting language.

---

