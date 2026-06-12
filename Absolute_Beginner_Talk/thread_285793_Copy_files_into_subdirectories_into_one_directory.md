---
title: "Copy files into subdirectories into one directory"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Pilsner on 2006-10-27
How do I copy files from subdirectories into one directory.

The problem is that the files in these subdirectories has same filename.

For example

/home/pilsner/wildsea/wildsea1/01.jpg
/home/pilsner/wildsea/wildsea1/02.jpg

/home/pilsner/wildsea/wildsea2/01.jpg
/home/pilsner/wildsea/wildsea2/02.jpg

I have tried different commands with cp but the problem is that it overwrite existing file.

Is there a way to give it a new name into the directory so all files will come to that directory.

Hope understand what i mean

/ Pilsner.

---

### Post by Arndt on 2006-10-27
> **Pilsner said:**
> How do I copy files from subdirectories into one directory.

The problem is that the files in these subdirectories has same filename.

For example

/home/pilsner/wildsea/wildsea1/01.jpg
/home/pilsner/wildsea/wildsea1/02.jpg

/home/pilsner/wildsea/wildsea2/01.jpg
/home/pilsner/wildsea/wildsea2/02.jpg

I have tried different commands with cp but the problem is that it overwrite existing file.

Is there a way to give it a new name into the directory so all files will come to that directory.

Hope understand what i mean

/ Pilsner.

You can use 'mmv' for such tasks (you may need to install it first). But first you have to decide which files have to change their names and how.

---

### Post by Pilsner on 2006-10-27
> **Arndt said:**
> You can use 'mmv' for such tasks (you may need to install it first). But first you have to decide which files have to change their names and how.

I have now installed mmv. And I would like to give new name for all files. Lets say put a letter "a" before and increase with "b" and "c" etc.

---

### Post by Pilsner on 2006-10-27
Just want to have all files into one directory. If its same name. Give it a new name automatically.

---

### Post by Arndt on 2006-10-27
> **Pilsner said:**
> Just want to have all files into one directory. If its same name. Give it a new name automatically.

I don't know if mmv can rename automatically if there is a clash. Look at the man page. But you can use it like this (mcp copies, mmv moves):

```
$ ls foo bar
bar:
a1  a2

foo:
a1  a2
$ mkdir foobar
$ mcp 'foo/*' foobar/foo-#1
$ mcp 'bar/*' foobar/bar-#1
$ ls foobar
bar-a1  bar-a2  foo-a1  foo-a2
```

---

