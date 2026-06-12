---
title: "using the FIND command"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2007-11-04
Ok guys

I now need to do the following: (from my textbook)

[COLOR="DarkGreen"]create a single find command that lists all files within the /usr/bin directory that have file permissions set to 755 and have more than three hard links to them. The find command should print out to STDOUT (the screen) the last access time, size in 1k blocks, and the file name of each matching file, with each of these three items separated by a tab.[/COLOR]

This is homework. Thus far I have been able to figure out how to use the command to give me the ones with permissions set to 755, beyond that, I am stuck.

Anyone can help with this? 

thanks

---

### Post by nick_h on 2007-11-04
Have a look at the man page for find.
```
yelp man:find
```
You will need the options -type -perm -links and -printf

---

### Post by shredfitz on 2007-11-04
I have already researched the man page for find. I cannot find an answer. Perhaps I am overlooking it, or am not interpreting it correctly.

---

### Post by Zeosa on 2007-11-04
Normally I'd loathe doing someone's homework for them, but for some reason I've got a soft spot tonight.....


Try something like this (between this and the man pages you should be able to figure it out if it doesn't exactly suit you)


find /usr/bin/ -links 3 -perm 755 -printf '%a\t%k\t%f\n'

---

### Post by shredfitz on 2007-11-04
you didn't do the homework for me, although your help was tremendous. It helped me understand and decipher what is going on. I really do want to learn the material and retain it, I am not just trying to get through cheaply. Thanks again.

---

### Post by nick_h on 2007-11-04
Yes - I was thinking of adding *-type f* to list files only.

---

### Post by Zeosa on 2007-11-04
> **shredfitz said:**
> you didn't do the homework for me, although your help was tremendous. It helped me understand and decipher what is going on. I really do want to learn the material and retain it, I am not just trying to get through cheaply. Thanks again.

Glad to hear it!\\:D/

---

