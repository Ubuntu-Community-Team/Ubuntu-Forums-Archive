---
title: "Right kernel?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-02-28
I found this:
> Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux.

Note the i686. Have I got the wrong kernel?

---

### Post by David Corrales on 2006-02-28
For compatibility, ubuntu by default installs the 386 kernel image. Go into synaptic, and look for a package called linux-686 and install it.

---

### Post by Lux Perpetua on 2006-02-28
The 386 kernel isn't exactly "wrong"; it is compatible, but it isn't exactly right, either. The 686 kernel will be better optimized for i686, and if you have more than 800 MB of RAM (I think that's right), you will need the 686 kernel to get to it. 

(I had the exact same question a few months ago :))

---

### Post by Jimmey on 2006-02-28
Thankyou :)

---

