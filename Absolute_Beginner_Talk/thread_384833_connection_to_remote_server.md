---
title: "connection to remote server"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-03-14
I have an account on my university's server and I would like to mount it directly so that I can access my files like any other file on my computer. I tried using sshfs but it never seemed to work right. I can connect my using Connect To Server under the Places menu. So what I am really asking is if there is a way to auto mount or something so that I don't have to type in my information every time I want to connect? Thanks!

---

### Post by finer recliner on 2007-03-15
use the shell's built in ftp command:

```
ftp server.school.edu
```

or download a gui ftp client if text based is too cumbersome

i also like to connect to my school's servers from my home computer, but never felt the need to try to mount my personal directory (if even possible). i just ssh or ftp

---

