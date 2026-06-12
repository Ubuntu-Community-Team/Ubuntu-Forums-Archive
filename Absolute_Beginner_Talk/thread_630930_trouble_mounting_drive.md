---
title: "trouble mounting drive"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-12-03
I have been trying to mount 2 hard drives. every time I try they come up OWNED by the "root" and I can't change access or open.

What am I doing wrong?

---

### Post by fenian on 2007-12-03
You need to set the ownership and permissions use these commands...

>  sudo chown -R user:user /storage
sudo chmod -R 755 /storage


change user to your username and /storage to the path to your drive.

---

### Post by kelbizzle on 2007-12-03
nevermind, that'll do it.

---

### Post by davidexe on 2007-12-03
I did that and it went through the entire drive changing the files and printing the names in the terminal editor.  Then when it got done it had changed nothing.  WHen it changes anything it refers to it as "READ ONLY"

---

