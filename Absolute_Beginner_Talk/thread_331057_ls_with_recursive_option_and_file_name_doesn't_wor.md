---
title: "ls with recursive option and file name doesn't work"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by FromFPan2Fire on 2007-01-04
I am having a very basic problem with the ls command.

Version:  Ubuntu; 6.06 LTS (Dapper D)

Entering ls command from a terminal window:

When I do "ls -R"  I get what I expect, a recursive list of all files

When I do "ls a*" I also get what I expect - list of files starting with "a" in the current directory

But when I combine them:  "ls -R a*"   looking for a list of all files starting with a in the current directory and all subdirectories, it appears to ignore the "-R" option, only returning results from the current directory.

For another example, I know I have files in a subdirectory beginning with W;  But when I do "ls -R W* " it says No Such File or Directory;  If I do  ls -R then I can see files starting with W.

What is it that I'm not getting? ](*,) 

Thank You

---

### Post by girishv on 2007-01-04
Hi,

the command works correctly for me. For example,
ls -R G*
lists all the files under GP recursively. I am using edgy

Girish

---

### Post by Wim Sturkenboom on 2007-01-04
*ls* takes your file/directory argument as the starting point. If it can't find it, it stops. So you will only see output if the argument exists.
If you don't pass a file or directory, it takes the current directory which obviously exists and it will continue from there.

If you want to search for a file, you can use
```
find . -name "a*" -print
```
or
```
ls -R |grep "^a"
```
Both will find files starting with 'a', starting from the current directory.

---

### Post by FromFPan2Fire on 2007-01-04
Thank You
I appreciate your assistance.
That's what I was looking for.

---

