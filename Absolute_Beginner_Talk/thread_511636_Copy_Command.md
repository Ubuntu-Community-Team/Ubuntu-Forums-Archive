---
title: "Copy Command"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-07-28
Could someone please help me with the command line syntax to do the following .....

I wish to copy all .jpg files which are larger than 100kb from /media/sdb1 directories and sub directories to /media/sdc5.  No need to preserve the directory structure ...  just a copy of the files...

If the file size is a problem I can always sort the copied files and delete the smaller items.

I can work out much of the syntax but I am getting lost with the sub directories and the file size.

---

### Post by cdiem on 2007-07-28
You may try the command:

gksudo nautilus

and then navigate in the directories, sort everything by size, and copy/paste with Ctrl-c and Ctrl-v. Hope this helps.

---

### Post by RomeReactor on 2007-07-28
EDIT: Sorry, forgot the size issue...

---

### Post by expatCM on 2007-07-28
Thanks for your comments but it needs to be command line since there are say 300 directories and who knows how many sub directories and ...  copy and paste will only let me copy a limited number of files (by size)

---

### Post by expatCM on 2007-07-28
no responses .......  is it really so hard to copy jpg files and not others ....?

Or is it that people know only the graphical interface and not the command line.

---

### Post by pmg on 2007-07-29
The **find** command is a good one to get to know for this type of thing.  Try this:
```
find /media/sdb1 -name \*.jpg -size +100k -exec echo cp \{\} /media/sdc5
```
That **echo** in there will make it just write out the cp (copy) commands rather then running them, but that way you can see if it's really what you want, and if so rerun it without the echo in the middle.

Also, the **-name** flag on find can be replaced with **-iname** if you want to make it case insensitive, that is if you want to to find .JPG files as well as .jpg files.

---

### Post by tomcheng76 on 2007-07-29
i found it should be this in order to run
```

find /media/sdb1 -iname \*.jpg -size +100k -exec echo cp \{\} /media/sdc5 \;

```

---

### Post by expatCM on 2007-07-29
Well I must say thank you and I am really very impressed. 

The command not only works but does exactly what I wanted.    I have not yet got up to the Find command in my book, I just had a look at the chapter and it helps me to understand the approach you have taken.    So I have a lot more reading to do but with your help I have been able to solve a pressing problem :)  Thanks again.

---

### Post by pmg on 2007-07-30
Ops, you're right, tomcheng76, I missed a space when typing in the command.  Thanks for catching that.  I fixed it above to avoid any confusion.

---

