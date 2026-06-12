---
title: "meoncoder -lavcopts unrecognized option"
date: 2012-06-23
forum: Any Other OS
---

### Post by vlad2005 on 2012-06-23
I try'it to make some conversion with mencoder. My command is:
```
mencoder -ovc lavc -oac lavc -lavcopts vcodec:mpeg4:vqscale=4:aspect=16/9 -ffourcc xvid "in.webm" -o "out.avi"
```

But i get error
```
Error parsing option on the command line: -lavcopts
```

Spec:
OS - Linux Mint 13, 32bit
MEncoder svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team

What it's wrong?

---

### Post by fixitdude on 2012-06-23
vcodec=mpeg4

Did you try google and look at other people's commands?

---

### Post by vlad2005 on 2012-06-23
Upss!
Thanks, this is my fault!!!
Work ok, thanks again!!

---

### Post by Perfect Storm on 2012-06-23
Moved to Other OS/Distro Talk.

---

