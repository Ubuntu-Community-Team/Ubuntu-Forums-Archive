---
title: "Only 'root' can do that...."
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Niloc on 2006-08-19
What does this mean? Do I have to change folders to somewhere, do I have to login as 'root'... I am only trying to copy a file off a memory stick and I have to 'mount' the device but it keeps telling me than the mysterious 'root' is the only one who can do it...

---

### Post by aysiu on 2006-08-19
In general for system folders:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

I don't see why your memory stick isn't mounting correctly (it usually does just fine), but you can do a manual override of that. These tutorials are for partitions, but the same principle applies for drives as well:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by crash331 on 2006-08-19
There is no root in ubuntu.  Just type sudo in front of everything you do that needs root access.

---

### Post by scxtt on 2006-08-19
'root' is the administration account - just preface any command that you want to use w/ **sudo** and enter your password, that way you can act as 'root' ...

note: this is "dangerous" if you don't know what you're doing (but that's how you learn :p)

---

