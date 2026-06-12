---
title: "turn off the boot-up image"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-11-01
okay, if they see this, I know that some of the ubuntu developers are gonna want to kick my ass real hard but, 

I enjoyed seeing the messages rolling off the monitor while booting the computer. how do I turn off the nice splash (?) image to see those ugly (they are ugly) messages? preferably using a gui tool?

I read about gnome-splashscreen-manager but I could not really decide (language problem) whether that was the thing I was looking for...

thanks.

---

### Post by heimo on 2005-11-01
This should help:
[http://www.ubuntuforums.org/showthread.php?t=76704](http://www.ubuntuforums.org/showthread.php?t=76704)

Hopefully that does it. 
```
sudo gedit /boot/grub/menu.lst
```
(remove word splash)

That should do it, if you want, you can also remove the usplash package, but I guess that's not neccessary.
```
sudo apt-get remove usplash
```

---

### Post by towsonu2003 on 2005-11-01
that should work, thanks so much. 

PS. I have to learn how to use keywords to search the forum... :rolleyes:

---

### Post by cantormath on 2007-03-04
nice.

---

