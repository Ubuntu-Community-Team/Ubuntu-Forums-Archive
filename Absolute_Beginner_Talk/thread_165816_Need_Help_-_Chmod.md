---
title: "Need Help - Chmod"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Mr Wrath on 2006-04-25
well...I was at the :/ directory as root (yes I know...stupid, I forgot to exit out of root](*,) 
) anyways...to make a long story short, I hit this command while at that directory.

Fileserver:/ chmod -v 755 *

I need some help changing permissions by using symbolic representation...I have only used octal representation in the past and I know the only way to change a sticky permission (rwt=others) is by symbolic rep. ...
Here is one of the changes that was made...

was tmp=drwxrwxrwt |  now tmp=drwxr-xr-x

I was quick to learn that my [man] pages wouldn't pull up unless I was logged in as root.  If anyone could give me an example of how to make these type of changes...that would be of great help...Thanks in advance.

---

### Post by cgjones on 2006-04-25
This link covers it quite well.

[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)

---

### Post by Mr Wrath on 2006-04-25
hey thanks...very helpful...:)

---

