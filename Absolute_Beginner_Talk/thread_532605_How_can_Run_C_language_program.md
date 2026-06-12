---
title: "How can Run C language program"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mthalis on 2007-08-22
My computer had gcc cmpiler. I used gcc -o test test.c comand then 
terminal gave below error message. Is this comand it run. I'm looking for quick answer

gcc -o test test.c
test.c:1:18: error: stdio.h: No such file or directory
test.c: Infunction 'main':
test.c:4: warning: incompatible implicit declaration of built-in function 'printf'

---

### Post by russell.h on 2007-08-22
try running the following command:
```
sudo aptitude install build-essential
```
Then try compiling again.

---

