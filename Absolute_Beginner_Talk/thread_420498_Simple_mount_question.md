---
title: "Simple mount question"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by kagy on 2007-04-23
Hi all,
I'm trying to figure out how to set a user as the owner of a dev when it's automounted. Its an ntfs drive fstab entry as follows 
```
/dev/sda1       /windows/C       ntfs    auto,user,ro,noexec 0   0

```
However, when ever I try to view it or cd into it I get a access denied message.
I can type /windows$ sudo chown -hR karl:users C and it seems to run through the files (but each has the warning readonly file system)

how can I set me as the owner when mounting, or how can I start a superuser graphical file management?

Thanks

---

### Post by jfinkels on 2007-04-23
> **kagy said:**
> Hi all,
I'm trying to figure out how to set a user as the owner of a dev when it's automounted. Its an ntfs drive fstab entry as follows 
```
/dev/sda1       /windows/C       ntfs    auto,user,ro,noexec 0   0

```
However, when ever I try to view it or cd into it I get a access denied message.
I can type /windows$ sudo chown -hR karl:users C and it seems to run through the files (but each has the warning readonly file system)

how can I set me as the owner when mounting, or how can I start a superuser graphical file management?

Thanks

You probably need to install the ntfs-3g tools to be able to write to your NTFS partition. Do a search on the forums for ntfs-3g.

---

### Post by kagy on 2007-04-24
Ok I'll try that after I upgrade to Fiesty. I don't actually want write access to this drive though. Is there a way to set the ownership during mounting? or to start a superuser nautilus

---

### Post by kagy on 2007-04-26
> **kagy said:**
> or to start a superuser nautilus
To answer my own question:
gksu nautilus

go me.....:-D

---

