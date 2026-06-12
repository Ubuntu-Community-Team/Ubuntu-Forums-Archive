---
title: "Loading a bin file"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by izvie on 2006-10-30
I have downloaded a .bin file called:

MarbleBlastGoldDemo-1.4.1.sh.bin

from:

[http://www.garagegames.com/pg/product/view.php?id=15](http://www.garagegames.com/pg/product/view.php?id=15)

I thought if I loaded it into my home directory and double-clicked on it, then it would just work.  Apparently not.  What steps do I need to take to load this demo?

Thanks! :-D

---

### Post by catlett on 2006-10-30
First make it executable
```
sudo chmod +x MarbleBlastGoldDemo-1.4.1.sh.bin 
```
Then launch it in the terminal with the run command ./

```
./MarbleBlastGoldDemo-1.4.1.sh.bin 
```
This is assuming the file is in your home folder. If it is in a different directory, you would have to change to that directory but you said it was in your home file so just open a terminal and enter the commands.

---

### Post by corstar on 2006-10-30
This is where unix-like systems and winblows differ.
For most binary files you download, you need to manualy make them executable.
The easiest meathod is:
1/ right click on the .bin file
2/click the "permisions" tab
3/ change the state for "user" to "execute"
4/ then click ok and use the file by clicking on it or in a terminal use this command infront ./

The"./" tells the terminal to execute the binary

Hope this helps

---

### Post by izvie on 2006-10-31
Thanks catlett and corstar!

---

