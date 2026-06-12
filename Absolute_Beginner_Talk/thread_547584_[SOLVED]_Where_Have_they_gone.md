---
title: "[SOLVED] Where Have they gone??"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by johnbull on 2007-09-10
Using Synaptic I downloaded and installed httrack and the httrack document file. Now I can't find the doc file to read it.
Where has feisty put it?

---

### Post by BrendanM on 2007-09-10
You can use [find]("http://unixhelp.ed.ac.uk/CGI/man-cgi?find") to locate it. Also, in synaptic, you can right-click on any installed package, go to "properties" and then the "installed files" tab will show you all the files from that package and where it put them.

---

### Post by southernman on 2007-09-10
You can also use whereis, like this:
> 
whereis httrack

---

### Post by por100pre1 on 2007-09-10
...or

```
which httrack
```

and create a launcher with the result.

---

### Post by johnbull on 2007-09-10
Thanks all, we're getting there. I've found it - now I'll have to find out how to create the launcher! (Grren as grass -if you hadn't guessed already)

---

### Post by johnbull on 2007-09-10
Once again, thanks. I've sorted the application end but I still can't find/read the doc file.

---

### Post by BrendanM on 2007-09-10
Try using the find command. You can use -name and wildcard characters like * to find the file you're looking for.

---

### Post by southernman on 2007-09-10
> Also, in synaptic, you can right-click on any installed package, go to "properties" and then the "installed files" tab will show you all the files from that package and where it put them.

Do the above as BrendaM suggests.

Normally though, docs are placed in /usr/share/doc

Not sure if it will work but try:

> man httrack

in a terminal window

PS... we were all new at some point. Me, still new! :p

---

### Post by johnbull on 2007-09-10
Thanks S-man. Yep, I've foundit and the manhhtrack command sorta works in that it gives me a dump of what looks vaguely like html (or something) In short I must now hunt down some graphical editor that can display it.
All this digging about - learning something new all the time!

---

### Post by johnbull on 2007-09-10
Great!   It WAS html ans (naturally) firefoz can read and display.

. . . . . Now, I just have to learn how to mark this thread **SOLVED**

---

### Post by johnbull on 2007-09-10
Solved

---

### Post by southernman on 2007-09-10
> **johnbull said:**
> Great!   It WAS html ans (naturally) firefoz can read and display.

. . . . . Now, I just have to learn how to mark this thread **SOLVED**

Superb... 

To mark as solved, go to your original post right side and find the "Thread Tools" link. Click it and move down to Mark this post as solved. Viola. ;)

---

