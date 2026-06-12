---
title: "cd command in terminal"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by oceanp on 2006-03-06
Hi,
I give the command "cd rt7" and i get the reply "No such file or directory".
The file rt7 is right in front of me on the desktop?  What am I missing?
I'm sorry to ask such basic questions but I don't know where to look for answers to such basics.
TIA

---

### Post by transactionlogfiller on 2006-03-06
Are you sure it's a directory and not a file?

```
ls -l
```

and is it definately in the direcory you are in, not some other directory? You didn't put a / in front of it?

---

### Post by Klaidas on 2006-03-06
Make sure you use the right name (case-sensitive) :)
Make sure you are in the Desktop folder too :)

---

### Post by transactionlogfiller on 2006-03-06
I think Klaidas might have put his finger on it there. The home directory is not the same as the desktop.

```
cd Desktop
``` (capital D is important)

---

### Post by oceanp on 2006-03-06
Thank you for your replies.  Giving the code set me straight. I was not in the Desktop.

---

### Post by ncappel1 on 2006-03-06
whenever you switch to a new directory you need to input the exact name (case sensitive) of the place you want to go with slashes. the command needs to take the form of: cd /path/of/directory

for example, moving to my personal desktop would be: "cd /home/nicola/Desktop"
(note: my user name is "nicola")

to move to my home folder I would type: "cd /home/nicola"
or to my homework folder "cd /home/nicola/homework"

this can get pretty tiring after a while, because the same folder names end up being used over and over and over again. to use some VERY helpful shortcuts use ./ (dot slash) ../ (double dot slash) and ~/ (tilde slash)

To move deeper in a direcotry you are in, simply type "cd [name of folder]

./ is also a shortcut to the directory you are in **right then and there**, so if I am in /home/nicola/homework and I want to change to my past homework, a sub-folder I created, I would simply input
```
cd ./oldhomework
```

../ is the more useful shortcut for the parent directory. If I am in the folder /home/nicola/homework/oldhomework, and I want to move the the parent directory, Instead of typing "cd /home/nicola/homework" I would just type ```
cd ../
```
and voila! I am in the parent directory. and also, "cd ../AnotherDirectory" to go up one directory and down into another one.

~/ is your home directory. if for some random reason I am in the deep, imaginary directory: /some/random/place/that/is/deep/in/the/dir/tree you can go straight back to your home, by using ```
cd ~
``` or if I wanted to, into my homework directory "cd ~/homework/oldhomework, or desktop "cd ~/Desktop"

you can use these commands to quickly and easilly navigate through your folders in the terminal, or to impress your friends who don't use linux and have them think you are a computer guru/wiz. Remember that you can use ./ ../ and ~/ in any command where you are specifying directories.

I hope this hasn't been too confusing!

---

