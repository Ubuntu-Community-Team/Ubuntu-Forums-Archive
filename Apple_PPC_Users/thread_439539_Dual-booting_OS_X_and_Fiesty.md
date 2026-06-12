---
title: "Dual-booting OS X and Fiesty"
date: 2007-05-10
forum: Apple PPC Users
---

### Post by iMacThere4iAm on 2007-05-10
I'm trying out the new Ubuntu (very cool!) and I've installed it to my spare partition so as not to have to remove OS X. However, I can't work out how to actually boot into it now! Can someone maybe link me to a guide on dual-booting Mac OS and Ubuntu? I'm sure I've done it before on a different PPC Mac and using an older version of Ubuntu, but I just can't remember how!

---

### Post by Auria on 2007-05-10
Yo ucan hold down alt key during boot and it will show you the list of available systems to boot from.

---

### Post by stmiller on 2007-05-10
So you currently have Ubuntu and OS X installed? And cannot boot into Ubuntu? Or cannot boot into OS X?

---

### Post by iMacThere4iAm on 2007-05-10
stmiller: I cannot boot into Ubuntu.

Auria: I will try that but I thought that only worked for Mac OS partitions.

---

### Post by Auria on 2007-05-10
> **iMacThere4iAm said:**
> 
Auria: I will try that but I thought that only worked for Mac OS partitions.

At least here it works :)

---

### Post by zalberico on 2007-05-11
I had a similar problem, THREE times in a row.
I installed feisty and then it wouldn't let me boot into it.  I think it was because I messed with the startup disk thing in system preferences in mac.
I reinstalled Feisty and then viewed my partition table when I saw that it was strangely messed up (13 small freed partitions)  After deleting them and reinstalling it worked fine.
I'm sure there is a way to fix it without reinstalling, but I couldn't find it.

Edit: I have it dual booting, it worked fine after the reinstall.  Good luck!

---

### Post by iMacThere4iAm on 2007-05-12
Good news, Auria's idea worked fine. Thanks!

zman: Yes, Ubuntu by default creates 3 partitions when it installs. I guess you were deleting only the large one and not the two small ones it uses for boot and swap. Glad you got that sorted.

---

