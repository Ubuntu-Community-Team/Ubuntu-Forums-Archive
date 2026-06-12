---
title: "accidentally removed the administrator privileges from my (only) account"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by tzach on 2008-03-17
Newbie mistake:
I use the GUI to accidentally removed the administrator privileges from my (only) account.
Now I can't get the user/group to retrieve it.
What should I do?

Thanks

---

### Post by jordanmthomas on 2008-03-17
Reboot into recovery mode (select it right as your computer is booting up)
Then, run this once it's booted up
```
gpasswd -a yourusername admin
```
then reboot.

---

### Post by Tomatz on 2008-03-17
You generally dont have admin privileges in a user account (security reasons).  To execute programs/commands with administrator privileges type "sudo" (w/o quotes) before the command then enter your password.  Alternatively open a terminal and type   sudo apt-get install nautilus-gksu   enter your password then type (in the terminal)  killall nautilus  then you will be able to rclick on a file/folder and open/run it with admin privileges.

[edit]OK didn't read post correctly forget that (its early here you know)

---

### Post by jordanmthomas on 2008-03-17
> **Tomatz said:**
> You generally dont have admin privileges in a user account (security reasons).  To execute programs/commands with administrator privileges type "sudo" (w/o quotes) before the command then enter your password.  Alternatively open a terminal and type   sudo apt-get install nautilus-gksu   enter your password then type (in the terminal)  killall nautilus  then you will be able to rclick on a file/folder and open/run it with admin privileges.

I think he has lost his sudo rights.

(edit)
You have now edited your post, making mine useless.  :)

---

### Post by Tomatz on 2008-03-17
> **jordanmthomas said:**
> I think he has lost his sudo rights.

(edit)
You have now edited your post, making mine useless.  :)

At least its not as useless as my first post lol :(

---

### Post by tzach on 2008-03-17
Thanks, I will try it

---

### Post by SkyPioneer on 2008-03-17
Did it work?

---

