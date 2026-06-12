---
title: "cut"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-31
i have a file directory called test on my desktop

i wanna cut it and paste it into /media/hdc3 

please list the code used for this

---

### Post by arron on 2007-03-31
You can right click and select cut, then browse to the folder and right click and paste.  If you want to use the prompt, which is a lot quicker:

```
 mv ~/Desktop/test /media/hdc3 
```

mv - command to move
~ - is your home folder
Desktop - is your desktop

if you want to copy:

```
 cp -r ~/Desktop/test /media/hdc3 
```

cp = command to copy -r to copy recursively

---

### Post by eljalill on 2007-03-31
```
 mv /home/ceezax/Desktop/test /media/hdc3/test 
```
or do "cp" instead of mv if you want to be sure, that nothing goes, wrong, that copies, rather than moves the file. After it is, where you want to have it, you can stil delete the file on the Desktop.
you can always check out, how a command works, through looking at the man pages (man command, type "q" to leave the manual).

---

### Post by Maestro23 on 2007-03-31
> **ceezax said:**
> i have a file directory called test on my desktop

i wanna cut it and paste it into /media/hdc3 

please list the code used for this

Code?  You want terminal commands?
> 
cd ~/Desktop

ls (lists contents of Desktop..should see your file)

mv test /media/hdc3 (moves the file to /media/hdc3)

or

cp test /media/hdc3 (puts a copy of the file in /media/hdc3)


---

### Post by Skrynesaver on 2007-03-31
Not sure if this is what you mean but if you wish to move a file from A to B then
```
mv A B
```
or in this case
```
mv ~/Desktop test /media/hdc3
```
you may have to do this as root (sudo) as hdc3 be mounted without global write permission, you can check this by typing 
```
ls -ld /media/hdc3
```
if it comes back with something like
drwxr-xr-x  7 root root 4096 2007-03-28 15:31 /media/hdc3
Only root will have permission to write to it

---

### Post by arron on 2007-03-31
> **Skrynesaver said:**
> 
```
mv ~/Desktop test /media/hdc3
```


you missed a important /.  it should be:
```
mv ~/Desktop/test /media/hdc3
```

by having "mv ~/Desktop test", if you had a test sub directory in the directory you were working in, it would move your ~/Desktop directory into it, and cause a world of hurt.

move works like
mv *positiona* *positionb*, so if you wernt watching it could move your directory unintentionally.

---

### Post by Skrynesaver on 2007-03-31
Thanks Arron,

A that was a typo on my part but it raises an interesting point.  I don't know when I last typed a full pathname as tab completion gets you to the right place every time. In this case typing
~/D then hitting the TAB key then t then TAB would have filled out the path entirely.

---

