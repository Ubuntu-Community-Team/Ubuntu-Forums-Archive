---
title: "how to rename a directory"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-26
I want to rename a directory? 
What command do I use in the terminal of Ubuntu 6.10 ? I don't think that copy and move will be correct.

Thank you for any tips.

---

### Post by prasad_bhatla on 2007-04-26
When renaming directories, you use the mv command exactly the same way as with files:
$ mv dir1 dir2

When dealing with directories, mv works a bit like cp does. If dir2 doesn't exist, the above will rename dir1 to dir2, but if dir2 exists, the directory dir1 will be moved into the dir2 directory under the name dir2/dir1.


Above from ---   [http://www.tuxfiles.org/linuxhelp/dirman.html](http://www.tuxfiles.org/linuxhelp/dirman.html)

So in Ubuntu you would in a terminal:

sudo mv dir1 dir2



Hope that helps.

Prasad

---

### Post by ottawa on 2007-04-27
thank's for the info. One question still:

sudo mv dir1 dir2
will that create a second directory or just rename dir1 to dir2 ?

ottawa

---

### Post by 5-HT on 2007-04-27
> **ottawa said:**
> thank's for the info. One question still:

sudo mv dir1 dir2
will that create a second directory or just rename dir1 to dir2 ?

ottawa

If dir2 does not exist, dir1 will be renamed dir2.
If dir2 does exist, dir1 will be placed within in.

'mkdir' will create directories.

---

