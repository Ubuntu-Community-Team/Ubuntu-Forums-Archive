---
title: "install script"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-20
Hello

how do i run an install script in Linux?

i tried to find out...for 15 minutes....run,execute, DOT sh....etc etc

could not find out

thanks

Vince.

---

### Post by linfidel on 2008-04-20
One thing you may not know about is that, unlike MSDOS, the current directory is NOT in the path.  So, you usually need to enter ./install-script-name.

Some people add the current directory to the path, but I'd recommend against it; it's easy enough to get used to the dot, and if you're not, you may have a problem on a different system, and forget about this.

---

### Post by vinceUUUU on 2008-04-20
Hello

sorry, don't understand your reply.

I have a terminal open and i am in the directory where the program exists...

the program or install script is called........B4S_install......... and it is highlighted in blue color...(does this mean permissions are an issue?)

what do i type at this command prompt to run that install script above?

thanks

VInce.

---

### Post by linfidel on 2008-04-20
> **vinceUUUU said:**
> Hello

sorry, don't understand your reply.

I have a terminal open and i am in the directory where the program exists...

the program or install script is called........B4S_install......... and it is highlighted in blue color...(does this mean permissions are an issue?)

what do i type at this command prompt to run that install script above?

thanks

VInce.
Hmmm, I think blue means it's a directory, not a file.

Type "ls -al" and see what it says on the left column.  If it has a d at the beginning, it's a directory. If so, do a chdir B4S_install and see what's in there.  Once you find the script to run, enter "./script", substituting the script name for "script".

If it's not a directory, the next 3 are one or more of "rwx", for read/write/execute, and it should have at least "r-x" to read and execute.  Otherwise, you would need to use "chmod" to make it executable (chmod 775, probably).  Then, you would enter "./B4S_install".

---

### Post by vinceUUUU on 2008-04-20
Hello

thanks very much

that is a great help....a clear explanation of what to type and look for..

thanks

Vince.

---

### Post by linfidel on 2008-04-21
> **vinceUUUU said:**
> Hello

thanks very much

that is a great help....a clear explanation of what to type and look for..

thanks

Vince.
Glad I could help.  And thanks for letting me know I did.  :)

---

