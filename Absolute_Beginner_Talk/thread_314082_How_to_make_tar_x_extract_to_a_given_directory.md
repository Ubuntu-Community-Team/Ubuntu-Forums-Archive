---
title: "How to make tar x extract to a given directory?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by jamadagni on 2006-12-07
How to make tar extract to any given directory instead of the current directory? For example, I have a file winc.tar.gz in my home dir (on /dev/sda8) that I want to extract to /mnt/sda1/. How do I do that?

I don't want to copy the file to /mnt/sda1 since it is very big and the partition sda1 is not big enough to contain both the tgz and its expanded for. 

tar xvzf winc.tar.gz tries to extract to the current dir on sda8. Then I am forced to do a separate move operation to move the files to sda1. Instead, I want to directly make tar to extract to sda1. How?

---

### Post by linuchsan on 2006-12-07
-C option

---

### Post by charles.g.moore on 2006-12-07
i think you can do this:

for gzip files :  tar -xvzf <path>/package.tar.gz
for bzip2 files :  tar xvjf <path>/package.tar.bz2

---

### Post by aysiu on 2006-12-07
More specifically: ```
cd ~/
tar -C /mnt/sda1 -xvzf winc.tar.gz
```

---

### Post by Voxxi on 2006-12-07
> **jamadagni said:**
> How to make tar extract to any given directory instead of the current directory? For example, I have a file winc.tar.gz in my home dir (on /dev/sda8) that I want to extract to /mnt/sda1/. How do I do that?

I don't want to copy the file to /mnt/sda1 since it is very big and the partition sda1 is not big enough to contain both the tgz and its expanded for. 

tar xvzf winc.tar.gz tries to extract to the current dir on sda8. Then I am forced to do a separate move operation to move the files to sda1. Instead, I want to directly make tar to extract to sda1. How?

Why don't you just cd to /mnt/sda1 first? Then, just use the tar command, except give it the full file path (Like /home/yourusername/winc.tar.gz) and then put a dot after the command:

```
tar -xvzf /home/yourusername/winc.tar.gz .
```

Hope I've got it right ;) .

---

### Post by Bachstelze on 2006-12-07
> **aysiu said:**
> More specifically: ```
cd ~/
tar -C /mnt/sda1 -xvzf winc.tar.gz
```

Actually, the -C has to be at the end, like this :

tar xzvf filename.tgz -C /mnt/sda1

---

### Post by aysiu on 2006-12-07
> **HymnToLife said:**
> Actually, the -C has to be at the end, like this :

tar xzvf filename.tgz -C /mnt/sda1
If that's the case, you'd better correct this page:
[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by jamadagni on 2006-12-08
Thanks all for the tips.

---

