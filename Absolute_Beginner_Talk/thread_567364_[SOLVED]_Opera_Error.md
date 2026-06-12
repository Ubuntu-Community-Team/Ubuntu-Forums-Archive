---
title: "[SOLVED] Opera Error"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by grabyourhosting on 2007-10-04
I get the following Error message........

```

ralph@ralph-desktop:~$ sudo apt-get remove opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.
ralph@ralph-desktop:~$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.
ralph@ralph-desktop:~$ 

```

Well My Package/Update Manager don't work.

---

### Post by por100pre1 on 2007-10-04
How did you installed Opera? If you downloaded it from the opera portal do so again and try to reinstall it first. :-k

---

### Post by grabyourhosting on 2007-10-04
I tried from the Opera portal but it don't work.....

---

### Post by por100pre1 on 2007-10-04
> **grabyourhosting said:**
> I tried from the Opera portal but it don't work.....

Did you use the same Opera version? :-k

---

### Post by grabyourhosting on 2007-10-04
I used the Ubuntu Feisty Fawn Version thats on Opera.Com

---

### Post by por100pre1 on 2007-10-04
> **grabyourhosting said:**
> I used the Ubuntu Feisty Fawn Version thats on Opera.Com

I mean the version number... :-k

---

### Post by grabyourhosting on 2007-10-04
Opera 9.23 for Linux i386

---

### Post by por100pre1 on 2007-10-04
> **grabyourhosting said:**
> Opera 9.23 for Linux i386

Try this then:

```
sudo dpkg-reconfigure opera
```

or do this:

```
sudo dpkg --remove --force-remove-reinstreq opera
```

---

### Post by grabyourhosting on 2007-10-04
```

sudo dpkg --remove --force-remove-reinstreq opera

```

Worked. Thanks!

---

### Post by por100pre1 on 2007-10-04
> **grabyourhosting said:**
> ```

ralph@ralph-desktop:~$ sudo dpkg-reconfigure opera
Password:
/usr/sbin/dpkg-reconfigure: opera is broken or not fully installed
ralph@ralph-desktop:~$ 

```

Edited my previous post... :-k

EDIT: Glad to help! 8)

---

