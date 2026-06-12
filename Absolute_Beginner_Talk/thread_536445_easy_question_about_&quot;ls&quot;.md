---
title: "easy question about &quot;ls&quot;"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Digitallysick on 2007-08-27
Ok when in the command line "ls" lists all files, how can i do this with a break or pause? like in windows it was dir /p  what is the command for linux so i can show a few files then hit enter to contiune to show a page more.

---

### Post by vambo on 2007-08-27
```
ls | more
```

will scroll a screenful at a time  - <space> to scroll down a screenful

---

### Post by bodhi.zazen on 2007-08-27
ls -C

See man ls  for more options :twisted:

---

### Post by ntlam on 2007-08-27
[http://www.computerhope.com/unix.htm](http://www.computerhope.com/unix.htm)

for some command reference

---

### Post by beercz on 2007-08-27
ls -la | less

Allows you to scroll up and down the list

press q to end the listing

---

### Post by aks44 on 2007-08-27
```
ls | less
``` will allow you to scroll back & forth (up & down arrows, page up & page down, space, q to quit) ( **| less** works with any command BTW)

---

