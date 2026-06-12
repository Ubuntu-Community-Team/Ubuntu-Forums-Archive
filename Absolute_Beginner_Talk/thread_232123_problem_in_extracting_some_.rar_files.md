---
title: "problem in extracting some .rar files"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-08
most of the .rar files I am able to extract using on of the programs :
arhive manager and xarhive manager who I find better
but I cannot extract rar files **in language other then english**

how can I extract them ?

---

### Post by dmizer on 2006-08-08
try the standard rar archiver:
```
sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar
```

---

### Post by u04f061 on 2006-08-08
install the package unrar

sudo apt-get install unrar

to unarchive the file use
 unrar /<file path>/filename

it works 100%on my pc

---

### Post by MaximB on 2006-08-08
> **u04f061 said:**
> install the package unrar

sudo apt-get install unrar

to unarchive the file use
 unrar /<file path>/filename

it works 100%on my pc

thanks
I've tried it but I don't manage to type the correct path
it's kind of complicated for me
I enter :  unrar /maxim/home/music/aria22.rar
and it shows me the help.
I even tried going in that folder and typed : unrar aria22.rar
and still no use
1.how do I do it correctly ?
2.is there a GUI ?

---

### Post by MaximB on 2006-08-08
I know you know ;)

---

### Post by MaximB on 2006-08-09
help ?

---

### Post by MaximB on 2006-08-09
I hate doing this...but I still need help

---

### Post by mushroomcloudwarrior on 2007-12-15
I have Unrar installed already,

However, when i try to extract files that are in two parts;

file(part1).rar, file(part2).rar

It somehow doesn't seem to know what to do!

---

### Post by RomeReactor on 2007-12-15
Hi. Have you tried double-clicking on the first part (FILENAME.part1.rar) to bring up File-Roller, the archive manager?

---

