---
title: "find file with ls in current dir only"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by selwynpolit on 2008-03-25
Hi folks, 
I'm trying to find a file in the current directory and I get a listing of all matching files in all subdirectories also.  Is there a way to not include all subdirectories?

I want to do something like:

dir gr*
and get

group
groups
grumpy
grizelda

so I use:

root@selwynlx2:/etc# ls -l gr*

and I get:

-rw-r--r-- 1 root root  860 2008-02-03 00:32 group
-rw------- 1 root root  847 2008-02-02 23:59 group-

groff:
total 8
-rw-r--r-- 1 root root 854 2006-06-19 16:06 man.local
-rw-r--r-- 1 root root 848 2006-06-19 16:06 mdoc.local

grub.d:
total 4
-rwxr-xr-x 1 root root 219 2007-09-28 06:03 20_memtest86+

Not a huge problem in this case, but I often get long listings that I have to scroll back to find.

thanks for your suggestions.  I didn't find anything in the help screens.
Selwyn

---

### Post by kpkeerthi on 2008-03-25
May be **ls** is aliased to ls -r. What does the below command print?
```
alias
```

---

### Post by selwynpolit on 2008-03-25
Hi kpkeerthi, 
thanks for your prompt reply.
alias results in:

alias ls='ls --color=auto'

I guess I should mention I am running Kubuntu 7.10 amd 64 bit version.


Selwyn

---

### Post by lloyd_b on 2008-03-25
Try "ls -ld gr*.  The "-d" option will prevent "ls" from looking in subdirectories.

Lloyd B.

---

### Post by selwynpolit on 2008-03-25
Thanks Lloyd - that did it.

---

