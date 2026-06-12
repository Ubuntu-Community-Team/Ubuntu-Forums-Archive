---
title: "Ununtu won't boot"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Mt Dew on 2007-07-06
Is there a way I can run a program from the Live CD to check for errors in the file system or the hd.  I can't get my Ubuntu to boot.  It start to boot but it goes to a black screen like the terminal command, spits out a bunch of stuff.  Says something about apt-get :command not found, then stops at root@username...

Thanks!

---

### Post by Mt Dew on 2007-07-07
BTW, the last thing I did was install Frostwire, but it was shut down  times before it did this.  Seemed like it was running fine.

---

### Post by deadgobby on 2007-07-07
At the root@username... prompt try 
sudo fsck
 and see if it will repair the problem.

---

