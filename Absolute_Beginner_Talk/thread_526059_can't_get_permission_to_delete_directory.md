---
title: "can't get permission to delete directory"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by urvaksh on 2007-08-15
I did a backup in Ubuntu using the Backup and Restore utility. 
I saved it on the desktop and it showed up with a lock. When I tried to delete it or move it off the desktop, it said I didn't have permission to do either. 
It's saved as a directory in my home folder and it says is empty. How do I get rid of this directory or at least get it off the desktop.
Thanks

---

### Post by HereInOz on 2007-08-15
Open a terminal and type:

gksudo nautilus

then enter your password when asked.

This will open the Nautilus file manager as root, and should allow you to delete the file.

---

### Post by urvaksh on 2007-08-15
HereInOZ, 
It worked perfectly. Thank you. After deleting the directory and emptying the trash, I closed the terminal. Does that take me out of root?

---

### Post by urvaksh on 2007-08-15
HereInOz,
I have one more question: I have installed Ubuntu on a Windows machine using an application called Wubi. I'm not sure how it works, but it gives me a fully functioning Ubuntu and a choice of OS to boot from.
However, I cn't hibernate from Ubuntu. When I hit hibernate, the screen goes dark and a cursor flashes contantly. The computer hibernates fine from Windows.
Is there a solution to this.
Thanks
Also, my mousepad is really sensitive in ubuntu. I have to turn it off when I type long messages:)

---

### Post by Arthur Archnix on 2007-08-15
There is a Wubi forum, I think, though I can't find it. Can't anyone help point me and OP in the right direction?

---

### Post by rich.bradshaw on 2007-08-15
Hibernate doesn't work if you install with Wubi.

---

### Post by rich.bradshaw on 2007-08-15
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

