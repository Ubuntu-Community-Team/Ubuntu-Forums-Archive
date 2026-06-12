---
title: "How do i switch to root?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Northie351 on 2007-07-04
I have recently installed 7.04 AMD 64 on my AMD 64 bit computer and am trying to install things.

Most threads I have read tell me that I have to be root to install anything

I ususally log on with my user name and password

I cannot log on as root as it tells me the log in details are incorrect

The ubuntu website says that, by default, root has no password

Very confused, many thanks for any help

---

### Post by lbelloq on 2007-07-04
Root logins are disabled by default in Ubuntu as a security measure.
If you need to do a root-only action, just log in with your normal user account and use "sudo [command]" in the terminal. For GUI, the system will ask for a password to run privileged tasks; just use you account's password.

---

### Post by mjwhitfield on 2007-07-04
prefix any commands that need to be run as root with
```
sudo
```

---

### Post by Outrunner on 2007-07-04
You can't login as root in Ubuntu by default, but with a bit of work, you can enable the root account. THIS IS NOT RECOMMENDED!

Instead, prefix a command with 'sudo' or, for graphical apps, with 'gksudo'. For instance, to install gparted
```

sudo aptitude install gparted
```

and to launch Nautilus as root

```
gksudo nautilus
```

Good luck and have fun :D

EDIT: Looks like i was too slow (again) :(

---

### Post by lbelloq on 2007-07-04
Yay, 1st ^^

---

