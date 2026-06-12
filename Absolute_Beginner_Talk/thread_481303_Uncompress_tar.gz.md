---
title: "Uncompress tar.gz"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2007-06-22
I'm trying to uncompress a tar.gz that I downloaded to my desktop. This is what I get
```
kyle@Lappy386:~$ gunzip teatimer-1.1.tar.gz
gunzip: teatimer-1.1.tar.gz: No such file or directory
kyle@Lappy386:~$ 

```

is gunzip the right command for this, what the heck am I doing wrong?

---

### Post by LaRoza on 2007-06-22
Type "cd Desktop", before doing that or move the file to your home folder.

You could use 
```

tar -xzvf Desktop/teatimer-1.1.tar.gz

```

just copy and paste

---

### Post by Majorix on 2007-06-22
You have downloaded the file to the desktop? Then you have to cd to there, and untar:
```

cd Desktop; tar -zxvf teatimer*.tar.gz

```

---

### Post by amazingtaters on 2007-06-22
cool thinks, all sorted out now

---

### Post by LaRoza on 2007-06-22
Remember, the directory "Desktop" is not the same as "desktop", Linux is case sensitive, unlike Windows.

---

### Post by mikewhatever on 2007-06-22
Try this one 'tar -zxvf teatimer*.tar.gz'

---

### Post by Old Pink on 2007-06-22
Or just go to your desktop, open the file and click extract, if you're looking to avoid terminal. :)

---

### Post by Nikron on 2007-06-22
Also, nowadays you don't have to be that specific about what kind of archive it is 'tar -xf ' will work on anything

---

