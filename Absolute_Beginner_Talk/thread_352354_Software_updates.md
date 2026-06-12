---
title: "Software updates"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by varkenslachter on 2007-02-03
I'm given the following error message by the software update utility;

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

anyone know what I should do next ?

kind regards,

---

### Post by tocleora on 2007-02-03
Ummm, did you try running 'dpkg --configure -a'? ;)  Open up a terminal window and paste that in.  Post the results here in case that doesn't resolve the problem.

---

### Post by moshuptrail on 2007-02-03
Probably will need sudo in front of that command.

---

### Post by varkenslachter on 2007-02-03
wow you guys are quick...

I get this:
dpkg: requested operation requires superuser privilege

I thought I was the administrator...

and what is a sudo ? Thanks very much

---

### Post by tocleora on 2007-02-03
sudo stands for "superuser do",  it's how to run a command as superuser (or root).  So put sudo in front like this:

```
sudo dpkg --configure -a
```

It will ask you for your root password, I believe at first this is just your regular password or it may have asked you for a root password when you set it up.

Ubuntu doesn't have a root account (you can log into) if I'm not mistaken so your account wouldn't be administrator, thus the need for "sudo".  Post the results if you continue to have problems.

---

### Post by lamego on 2007-02-03
You need to read [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/root-and-sudo.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/root-and-sudo.html) .

---

### Post by jvc26 on 2007-02-03
This is always a useful link RE: SU:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Il

---

### Post by Srirangan on 2007-02-03
sudo is like viagra for ubuntu commands. I solved all my permissions probs with sudo chown :)

---

