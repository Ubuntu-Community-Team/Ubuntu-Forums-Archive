---
title: "World of padaman install"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-08
How do i install from the .run file?

---

### Post by GrueTamer on 2007-05-08
WARNING: this process uses the terminal ONLY

Step 1: use the terminal to CD to the directory with the.run file, if it's in the /home/<name> folder, you don't have to do anything.  But if its on the desktop, you would, for example, do ```
cd /home/<name>/Desktop
``` (<name> is your username)

Step 2: use ls -l to determine if the file is executable.  In the directory with the file, just run ```
ls -l
``` in the terminal and find your .run file.  Then look on the far left.  If you see a lot of X's, then it's executable.

Step 3: use chmod.  If the file is executable by default, do ```
chmod -x <file>.run
```  If it is not, then change -x to +x.  You may be able to just skip step 2 and do +x, but step 2 just taught you something :)

Step 4: execute the file.  In the terminal, type ```
./<file>.run
```, and the file should execute properly.  If it doesn't, come back here with more information, or resort to this tutorial again.

I hope this helps!

---

### Post by Clay_Banger on 2007-05-08
open the terminal, cd to the directory worldofpadman.run is, then type:
```
./worldofpadman.run
```

---

### Post by mojo123 on 2007-05-08
./worldofpadman.run
bash: ./worldofpadman.run: Permission denied
alan@alan-laptop:~/Desktop$ sudo ./worldofpadman.run
sudo: ./worldofpadman.run: command not found

---

### Post by Clay_Banger on 2007-05-08
do as GrueTamer says, <file>.run needs to be worldofpadman.run

---

### Post by Grundalizer on 2007-06-04
i found this using the search feature and it contained the solution to my problem.  I followed your terminal commands and it worked, so now i know how to cd to a directory and find a file.  that ls -l is nifty although i don't know how to read what it prints out really.  what was with the -x or +x, and what is chmod?  thanks

---

### Post by Clay_Banger on 2007-06-04
> **Grundalizer said:**
> i found this using the search feature and it contained the solution to my problem.  I followed your terminal commands and it worked, so now i know how to cd to a directory and find a file.  that ls -l is nifty although i don't know how to read what it prints out really.  what was with the -x or +x, and what is chmod?  thanks
chmod can change the permissions on the file, as well as setting different attributes (such as, read-only, hidden etc.)

Using the +x in the chmod, tells it to make the file executable, so that Ubuntu will open it as an application, not a file.

---

