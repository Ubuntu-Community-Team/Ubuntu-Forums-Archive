---
title: "[SOLVED] 'ln'command not working"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Samrat Rao on 2008-03-10
hello,
i am just learning linux. my 'ln' command is not working. i have 7.10 (32 bit version) installed in my desktop. the error message i get is 'operation not permitted'. even using with sudo does not help. the ln command works only when i am in my 'filesystem' and the link is to be done when the files are in the same folder. in other drives i cannot even do that. 'ln' works in my friend's desktop and he has the same version of ubuntu. pl help.:(
thanks in advance....

---

### Post by Arkenzor on 2008-03-10
May I ask you the exact command you were trying to use?

Also, you should always use ln with the -s option to create symbolic links instead of hards links. Hard links can not reference a file on another filesystem, and will most likely fail even with sudo if you try to link directories instead of files.

Don't forget to read the command's manual page to learn more about its different options:
```
man ln
```

---

