---
title: "SSH - SCP file transfer help!"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by bamf on 2006-10-04
Hey,

So Im trying to use ssh in terminal to pull a file from a server from the unix server at school.

I figured out I had to use the 'scp' command but couldnt figure out how to grab the file and put it on say my desktop?

When I log in its in 'mydocuments' so I cd to that... but thats about as far as I got... I tried this but it didn't work...

> scp [email]borrivik@flop.engr.orst.edu:mydocuments/file.ext[/email] ~/Desktop/file.ext

Any help?

Thanks,
Kiley](*,)

---

### Post by andiii on 2006-10-04
> **bamf said:**
> 
scp [email]borrivik@flop.engr.orst.edu:mydocuments/file.ext[/email] ~/Desktop/file.ext


Use this:

scp [email]borrivik@flop.engr.orst.edu:~/mydocuments/file.ext ~/Desktop/file.ext[/email] .

(assuming that mydocuments is in your home folder)

---

