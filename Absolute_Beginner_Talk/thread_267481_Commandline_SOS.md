---
title: "Commandline SOS"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by ZERO_SHIFT on 2006-09-28
I need some help in the following:

How do I go to a previous directory after I open one in { cd <filename> } ??

What (while installing) is the difference between --> sudo bash, sh, and ./

thanks in advance (tia).

---

### Post by lamego on 2006-09-28
> How do I go to a previous directory after I open one in { cd <filename> } ??
cd ..

> What (while installing) is the difference between --> sudo bash, sh, and ./
sudo means it runs the next command with root (admin) privileges
bash means it should run the script with bash
sh means it should run the script with sh (which is an alias to bash)
./command meants it should run the command with whatver is the interpreter defined on the first line if it is a text file, it should run the binary if it is a Linux ELF bin

---

### Post by pbaehr on 2006-09-28
I am not familiar with that interpretation of ./. Maybe it is a usage I have not encountered. The most common use of the preface ./ I've encountered is to tell the computer that you are running a command in the current directory.

For example, if you have a script called 'ls' (which would be confusing) typing 'ls' at the command line would run the list command, rather than the ls script you have made. However, if you are in the same directory as your custom 'ls' script, typing ./ls would run that command instead. The dot refers to the current directory. For example, typing 'cd .' would leave you in the same place as when you started.

Also, you need to preface custom scripts with ./ (if you're in the same directory) or the full path of the script. Otherwise, Ubuntu will just look in your PATH for the script you're trying to run. It's a bit of a hassle, but it's a security feature.

---

### Post by lamego on 2006-09-28
About my desctiption of the ./command I forgot to mention that the described behavior is for the command present on the current directory :P

---

### Post by eeGhoong0ais on 2006-09-28
> **ZERO_SHIFT said:**
> How do I go to a previous directory after I open one in { cd <filename> } ??

```
cd ..
``` will take you up one level in the directory tree. If you want the equivalent of hitting the back button on a browser, ```
cd -
``` is the correct command, in bash at least. Other shells might not support it.

---

### Post by ZERO_SHIFT on 2006-09-29
Thanks everyone question answered.

---

