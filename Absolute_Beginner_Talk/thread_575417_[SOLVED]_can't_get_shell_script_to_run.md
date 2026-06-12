---
title: "[SOLVED] can't get shell script to run"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by spearfish on 2007-10-14
Hi,  I'm trying to install the MonetDB database program.  In order to get it installed, I have to run a shell script file.  My problem is getting the shell script to run.  This is what I get:

root@computer:/home/spearfish/MonetDB# ls -l
total 4
-rwxr-xr-x 1 spearfish spearfish 274 2007-10-13 22:43 monetdb-install.sh
root@computer:/home/spearfish/MonetDB# monetdb-install.sh --help
bash: monetdb-install.sh: command not found
root@computer:/home/spearfish/MonetDB# bash monetdb-install.sh --help
monetdb-install.sh: line 1: syntax error near unexpected token `newline'
monetdb-install.sh: line 1: `Usage: command-not-found [options] <command-name>'
root@computer:/home/spearfish/MonetDB# 

My instructions are very clear.  It says on my install sheet:

RUN

> monetdb-install.sh --help

however, it isn't working.  any suggestions?  by the way, we are told to run the script with --help first, so we can see all the options it comes with.

thanks!

---

### Post by thelocust on 2007-10-14
Try
```
 
./monetdb-install.sh

```

---

### Post by spearfish on 2007-10-14
sadly, that didn't work.  (sigh)  thanks though. :)  here is what happens:

spearfish@computer:~/MonetDB$ ./monetdb-install.sh --help
./monetdb-install.sh: line 1: syntax error near unexpected token `newline'
./monetdb-install.sh: line 1: `Usage: command-not-found [options] <command-name>'

everything I do results in this 'newline' error.  Ug.

I did a chmod +x on the shell-script to make it executable, and I added the current directory to my bash $PATH.  Neither of those seemed to work.

thanks

---

### Post by aysiu on 2007-10-14
Looks as if you're executing the script just fine but the script itself is badly written or has syntax errors in it.

---

### Post by spearfish on 2007-10-14
Hi,

Hey, I think that was it.  The script I downloaded only had part of the comments, but it was missing the bulk of the actual script.  dang.  that was an hour wasted!  haha

thanks for your help.  bad script.  that was it.

cheers!  :)

---

### Post by mindtrick on 2007-10-14
The right command should be
> sh monetdb-install.sh

---

