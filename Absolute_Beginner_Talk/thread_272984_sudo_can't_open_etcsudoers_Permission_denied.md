---
title: "sudo: can't open /etc/sudoers: Permission denied"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by caseymoore on 2006-10-07
I don't know what I've done.
I was mucking around with chmod whilst trying to get compiz working.
Now I can't use sudo. I also can't log in as root because I don't have a root user :(
How do I get sudo back?

---

### Post by Klaidas on 2006-10-07
> I don't know what I've done.

Umm, ok. But we don't know either. If we want to help you, we need to know.
In short, what did you do?

---

### Post by caseymoore on 2006-10-07
I was messing around with chmod I think I typed something like this:
chmod 777 /

---

### Post by Delkster on 2006-10-07
If you know enough about the command line shell to try and fix it, you can boot in recovery mode (hit Esc early in the boot process to get a boot menu, or if you dual boot, you probably get a boot menu anyway). In that mode you always have root privileges.

On the other hand, maybe you could check what's up with the permissions of the sudoers file.

The following command will show the permissions of the root directory:
```
ls -ld /
```
They should probably look like this or so:
```
drwxr-xr-x [some number here] root root
```

How about the permissions of the sudoers file itself?
```
ls -l /etc/sudoers
```
They could be for example this way:
```
-r--r----- 1 root root
```

If you can't even ls the sudoers file, there's something wrong with either the permissions of the root directory or /etc.

By the way, setting the permissions for / to 777 (readable, traversable/executable and **writable** by all) is a rather bad idea.

---

### Post by caseymoore on 2006-10-07
The permissions of the sudoers file look like this:
-r--r----- 1 root root

Is this a bad thing?
How do I change it so that I can use sudo again?

---

### Post by Delkster on 2006-10-10
> **caseymoore said:**
> The permissions of the sudoers file look like this:
-r--r----- 1 root root

Is this a bad thing?
How do I change it so that I can use sudo again?

No, that's how it should be.

What happens when you try to use sudo?

---

### Post by aysiu on 2006-10-10
You have to boot into recovery mode to fix things. If you changed your whole filesystem to 777, though, you should probably just reinstall--it'd take too long to undo the damage.

---

### Post by Delkster on 2006-10-11
> **aysiu said:**
> You have to boot into recovery mode to fix things.
Yes, but it might be a good idea to find out beforehand what's wrong and how to fix it.

> If you changed your whole filesystem to 777, though, you should probably just reinstall--it'd take too long to undo the damage.

Obviously his entire filesystem hasn't been recursively changed to 777 if his /etc/sudoers is -r--r----- (i.e. 440). What on earth has happened to prevent sudo from accessing that particular file is beyond me, though. And yes, reinstalling might still be one of the easier ways to make sure that nothing else is broken even if he gets sudo working.

---

