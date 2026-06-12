---
title: "/etc/fstab not found"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by AlP36 on 2007-11-07
I am using Ubuntu 6.06 and trying to get the hard drive with my legacy os to mount at startup, but I cannot find /etc/fstab file. Are some files hidden? 

Thanks

---

### Post by taurus on 2007-11-07
What's the output of this command from a terminal?

```
ls -la /etc/fstab
```

---

### Post by AlP36 on 2007-11-07
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /etc/fstab
```

This is the output:
-rw-r--r-- 1 root root 398 May 30  2006 /etc/fstab

---

### Post by taurus on 2007-11-07
As you can see, it's there.

```
cat /etc/fstab
```

---

### Post by AlP36 on 2007-11-07
> **taurus said:**
> As you can see, it's there.

```
cat /etc/fstab
```
Thanks. Still not sure why I couldn't see it in gnome, but I will figure it out.

---

### Post by taurus on 2007-11-07
What do you mean when you said you could not see it in Gnome?  were you using nautilus?  Were you in the right directory?

---

### Post by AlP36 on 2007-11-07
> **taurus said:**
> What do you mean when you said you could not see it in Gnome?  were you using nautilus?  Were you in the right directory?
As I said I will figure it out -- I just did as I was typing a reply to you I realized that I was looking at the folders in /etc, not looking for a file. Thanks for helping.

---

### Post by philinux on 2007-11-07
If you need to edit fstab then in terminal

sudo gedit /etc/fstab

---

### Post by Inxsible on 2007-11-07
> **philinux said:**
> If you need to edit fstab then in terminal

sudo gedit /etc/fstab```
gksudo gedit /etc/fstab
``` would be a better option :)

---

### Post by Maestro23 on 2007-11-07
> **Inxsible said:**
> ```
gksudo gedit /etc/fstab
``` would be a better option :)

Yes, gksudo when using gedit.

---

### Post by AlP36 on 2007-11-07
> **Maestro23 said:**
> Yes, gksudo when using gedit.
Thanks to all who replied. I felt kinda' foolish after I realized what I was doing.

---

