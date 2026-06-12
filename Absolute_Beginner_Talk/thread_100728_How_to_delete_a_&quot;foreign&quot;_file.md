---
title: "How to delete a &quot;foreign&quot; file?"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by EvilBill on 2005-12-08
I d/l'd [Puppy Linux](http://www.goosee.com/puppy/) 1.0.6 iso, & burned it. It is one of those live cd's. Anyhow it plants [this file here](http://tinypic.com/icidk3.png) onto my filesystem. I ntried to delet it or at least edit it, & created this other pup101 by mistake that also has to go.

The pup001 has info in it that leads me to a frozen screen when Puppy is booted up.

I have no idea how to fix it at either end other than by deleting it.
I just wanted the pup as a back-up when I have no operating system during an install etc.

---

### Post by ChrisTheGeek on 2005-12-08
Open a terminal. Type the following:

sudo rm -i /pup001
sudo rm -i /pup101

Press Y to confirm it's about to delete the correct files.

---

### Post by EvilBill on 2005-12-08
Thanks alot, that did the trick. :)

---

