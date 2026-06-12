---
title: "Move /home between partitions"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by paladinhugo on 2006-06-30
Hello all!

I want to move /home directory to the main partition. This is my partition structure:

/dev/hda1 >> /
/dev/hda2 >> /home
/dev/hda3 >> linux-swap

I want to move /home directory into /dev/hda1, because I need to clear /dev/hda2 in order to install windows temporarly.

How can I do this?

---

### Post by taurus on 2006-06-30
There are many ways to accomplish that but you probably want to boot up with the LiveCD (desktop version).  Mount /dev/hda1 so you can edit your /etc/fstab.  In there, change /home from /dev/hda2 to /dev/hda1.  Then, copy /home everything in old /home to new /home.  You can also do the editing if you boot your system with the recovery mode...

---

### Post by aysiu on 2006-07-01
Full instructions are here:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by gudy1024 on 2007-04-20
this is the link : without .html :)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
 
Greetings from Thailand :)
[http://picasaweb.google.com/jazzcommunication](http://picasaweb.google.com/jazzcommunication)
Gudy

---

