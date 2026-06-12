---
title: "Copying /home drive"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-04-05
I was following the commands from: [http://ubuntu.wordpress.com/2006/01/...own-partition/](http://ubuntu.wordpress.com/2006/01/...own-partition/)
I entered the command: "ubuntu@ubuntu:/home$ find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/"

I got the error message: "cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information."

What does this mean? How do i fix it?

---

### Post by sirisaac87 on 2008-04-05
Is this the right command or should I use another one?

---

### Post by mikeyphi on 2008-04-05
> **sirisaac87 said:**
> I was following the commands from: [http://ubuntu.wordpress.com/2006/01/...own-partition/](http://ubuntu.wordpress.com/2006/01/...own-partition/)
I entered the command: "ubuntu@ubuntu:/home$ find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/

I got the error message: "cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information."

What does this mean? How do i fix it?

Unless you made a typo in that command just in your post  cpio --null --sparse is what it should read (that's two - before each word)

I wasn't able to access that website to confirm your instructions.

---

### Post by sirisaac87 on 2008-04-05
ubuntu@ubuntu:/old_home$ 

Every time I use the terminal that /old_home$ or /home is there...how do I get rid of it?

---

