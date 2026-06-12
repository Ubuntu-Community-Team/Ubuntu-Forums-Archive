---
title: "[SOLVED] navigating at the terminal prompt"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-07-29
I'm Backkkk,

Some of you may remember me --- complete newbie, maybe even a bit of an idiot, but . . .

Trying some new hardware and would really REALLY like to get more acquainted with Linux -- so here goes:

It's been several months since my first attempt and I've now forgotten how to navigate at the prompt. I'm using the cd command like this

I was able to get from the basic prompt to the Desktop (yes, I remembered Linux is case sensitive) and can run the ls command which shows another folder on the desktop [HP Driver], but when I try to use the cd command again I get the following:
```
lwalper@lwalper-desktop:~/Desktop$ cd Desktop/HP Driver
bash: cd: Desktop/HP: No such file or directory
lwalper@lwalper-desktop:~/Desktop$ ls
HP Driver

```

---

### Post by shen-an-doah on 2007-07-29
You need to escape the space.

The actual command would be ~/Desktop/HP**\** Driver

The easiest way to get to a folder like that without messing around with the backslashes, just type the HP part and then hit Tab.

---

### Post by aysiu on 2007-07-29
The way you're doing it now makes it seem as if Desktop is a folder inside of the Desktop folder. In other words, you're trying to go to ```
/home/*username*/Desktop/Desktop/HP
``` You're already in the desktop folder.

Also, if you have a folder name with spaces in it, you need to do a backslash: ```
cd HP\ Driver
``` Alternatively, type *HP* and hit the Tab key.

---

### Post by lwalper on 2007-07-29
Perfect!! Ya'll ar the GREATEST!! Guess I need to keep at it.

---

