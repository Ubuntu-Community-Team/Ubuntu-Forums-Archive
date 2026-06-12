---
title: "mounting iso files"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by oveh on 2005-12-29
Is it possible to mount an iso file in linux? In windows I use daemon tools to mount my iso/bin/img files like cd-rom's so I don't need to burn everything on a cd and then install it.

Thanx anyway,
Ove

edit: found something on google:
```
sudo mount -o loop cdimage.iso /mnt/cdrom
```
will this work? gooing to try it out, wish me gl.

---

### Post by deNoobius on 2005-12-29
Good luck and, more importantly, would you report back on whether it works?  I like to do this in OSX as well and it would be great to know how in Linux--and I can't help but think others might also.

---

### Post by Nameless on 2005-12-29
I found this but I haven't had the chance to try it yet: 

[http://www.ubuntuforums.org/showthread.php?t=87369](http://www.ubuntuforums.org/showthread.php?t=87369)

---

### Post by oveh on 2005-12-29
excellent nameless :D it works!

---

### Post by oveh on 2005-12-29
now the problem is that i need to mount the iso image with the unhide parameter to show hidden files on the image... how do i do that?

---

