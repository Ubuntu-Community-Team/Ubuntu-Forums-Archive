---
title: "[SOLVED] Hidden Folders"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ibbill on 2007-11-01
I enabled hidden folders and found  Avg.

Was going to install it and told I really did not need it. Is there anyway to remove that. I used 

[HTML] ls -a[/HTML] have the terminal open now. Thanks again and again.

Bill

---

### Post by haldean on 2007-11-01
Do you mean that you found a folder in your home directory called .avg? If yes:
The fact that you have the .avg folder in your home directory does not mean that you have AVG installed; that just means that you did in the past. That directory probably just has configuration files from when you had it installed left in. If you're absolutely sure that AVG is uninstalled, it's perfectly safe to delete it in Nautilus, or by running
```
rm -r .avg
``` in the terminal.

---

### Post by ibbill on 2007-11-01
awesome that worked it was a old file left over I guess. 

Thanks again Bill

---

### Post by haldean on 2007-11-01
No worries ;)

---

### Post by ibbill on 2007-11-01
Oops spoke to soon it is still there. Will post a pick see couple of others there also

---

### Post by haldean on 2007-11-01
not sure if you already did this, but the command i gave you before should actually be ```
rm -r ~/.avg7
```?
if that doesn't work, what's the output of ```
ls ~/.avg7
```?

---

### Post by ibbill on 2007-11-01
oh my what have I done thanks again for your help

---

### Post by ibbill on 2007-11-01
looks like its gone have the 2 here hi lighted tried your code did not work for these 2 darn sorry for all the trouble.

---

### Post by haldean on 2007-11-01
The same code should work... 
```
rm -r .checkgmail
rm -r .ies4linux
```
You should only delete those directories if you've uninstalled libcheckgmail and Internet Explorer for Linux, though!

---

### Post by ibbill on 2007-11-01
Yes I removed  them the ie was a see if I could t crikey that worked. But did not want ie for sure.
Well I add a Y at the end of each line and  they are both gone thanks again. I sure appreciated the help don't seem enough to just say thank you but I am sure you know how I feel about the help.

Bill

---

### Post by haldean on 2007-11-02
No worries ;)

---

