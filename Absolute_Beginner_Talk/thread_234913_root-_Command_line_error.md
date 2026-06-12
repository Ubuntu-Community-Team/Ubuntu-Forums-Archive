---
title: "root- Command line error"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by snutter on 2006-08-12
Hi all, 

I just switched from debian. I don't seem to be able to be able to invoke programs as root- and I get some display error. This means i can't even open a text editor and change my sources.list. I don't have this problem when running as user.

This is what I get:
```

root@snutter-laptop:/etc/apt# gedit sources.list
cannot open display: (null)
Run 'gedit --help' to see a full list of available command line options.

```

---

### Post by jordilin on 2006-08-12
Being root you can't for security. So, it's disabled. The workaround is the following:
Type the following being root:
```
export DISPLAY=:0

```
then
```
gedit sources.list
```
and tell us sth.

---

### Post by uways on 2006-08-12
How does this differ from typing

[PHP]sudo gedit sources.list[/PHP]

?

---

### Post by jordilin on 2006-08-12
> **uways said:**
> How does this differ from typing

[PHP]sudo gedit sources.list[/PHP]

?

with sudo you can, because you are a normal non privileged user allowed to use Gui apps. But root is another user, and for security is not allowed.

---

### Post by uways on 2006-08-12
thanks

still learning...

---

