---
title: "how do I log in as root?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by mgh on 2007-05-17
Sorry, brand new to Linux.

Working through a few issues, but first impression of Ubuntu is I like it a lot.

When trying a command line, I get "permission denied".  I presume this is because I am not logged in as root?  For some reason I can not see how to get there.

Can't figure out how I am missing something this basic.

Thanks for any help.

---

### Post by mattva01 on 2007-05-17
In ubuntu you don't log in as root. You use sudo.
Usage:
sudo <command>

It will then ask for **your** password.

---

### Post by Bachstelze on 2007-05-17
You don't login as root. Use *sudo* instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yabbadabbadont on 2007-05-17
Also, "sudo -i", will drop you into a root shell.

---

### Post by Ptero-4 on 2007-05-17
you can use:
```
sudo passwd root
``` 

To enable the root account, but it is not advisable to enable that account because there is the risk of leaving active root shells around (common beginner mistake) which can allow any other person access to your system.

---

### Post by mgh on 2007-05-18
Thank You.

I will try reading more about Ubuntu this weekend!

---

