---
title: "super mega easy terminal syntax question"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Jeffa on 2007-08-09
OK, I've been trying to figure out how to copy all the new folders and files in one directory to another directory that contains old versions of them, and I can't seem to figure out the right syntax in terminal. Here's an example:

Directoryone
[LIST]
[*]olddirectory1
[*]olddirectory2
[*]OLDFILEONE
[*]OLDFILETWO
[/LIST]

Directorytwo
[LIST]
[*]newdirectory1
[*]newdirectory2
[*]NEWFILE1
[*]NEWFILE2
[/LIST]

I'd like to copy the old directories and files to the new one, but all my attempts have failed thus far. I know this is a super easy question for even a novice Ubuntu user, but alas i am not one. 

Thanks for any help!

---

### Post by Jimmyfj on 2007-08-09
if you are standing at e.g /home/myname/anydir the command will be cp <dirname> /path/<dirname> -r

---

### Post by MenZa on 2007-08-09
Seeing as Jimmy's reply wasn't particularly elaborate, I shall try to explain my best.

Let's assume you have two folders in your home folder, as you describe above. If we change to Directorytwo, we can do *cp -R ../Directoryone* to copy all the files and folders (and subfolders) to Directoryone.

---

### Post by K.Mandla on 2007-08-09
There's also a -u flag for the cp command that will only copy files that need updated. I don't know if that would be of use to you, but if the directories are large and the files have the same names, you might save a little time.

---

### Post by Jeffa on 2007-08-09
This is strange. If i try Jimmyfj's method, i get:

cp: target '/directory1/' is not a directory: No such file or directory

If I Try MenZa's Method I get:

cp: missing destination file operand after '../directory1/'

and I KNOW directory1 is there. I'm looking at it.

---

### Post by MenZa on 2007-08-09
> **Jeffa said:**
> This is strange. If i try Jimmyfj's method, i get:

cp: target '/directory1/' is not a directory: No such file or directory

If I Try MenZa's Method I get:

cp: missing destination file operand after '../directory1/'

and I KNOW directory1 is there. I'm looking at it.

Err right, I messed up. I forgot to define that we want to move all the files in the current directory:

```
sudo cp -R ***** ../directory1
```

Note the little star. :)

---

### Post by Jeffa on 2007-08-09
By George you've done it MenZa!

Thanks. :)

---

### Post by MenZa on 2007-08-09
It's what I'm here for. :)

---

### Post by philinux on 2007-08-09
Isn't it easier to do it the old fashioned way. got to first folder  then Edit >select all >copy.

move to target folder and right click then select paste.

works for me

---

### Post by Jeffa on 2007-08-09
You mean in Nautilus? 

I needed the terminal option.

---

### Post by philinux on 2007-08-09
Why use Terminal when you can just copy and paste.

Sudo nautilus allows root priviliges so its just easier or I'm missing something

---

### Post by Jeffa on 2007-08-09
yes, I'm connecting to the server at my web hosting company through ssh. No Nautilus. Shell access only.

:)

---

### Post by p_quarles on 2007-08-09
> **philinux said:**
> Why use Terminal when you can just copy and paste.

Sudo nautilus allows root priviliges so its just easier or I'm missing something
Why copy and paste when you can just use the console? And that should be gksudo nautilus, by the way. Using sudo for X11 apps can create permissions problems. While unlikely, the consequences can be fairly disastrous.

---

### Post by philinux on 2007-08-09
> **Jeffa said:**
> yes, I'm connecting to the server at my web hosting company through ssh. No Nautilus. Shell access only.

:)

My bad. Didn't realise shell acces only

---

