---
title: "IPod help please"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Hybrid_1014 on 2008-02-10
Before this happened, I used Amarok. I used it since i got Ubuntu on my computer, and it work fine until today. 
I plugged my IPod in and it won't mount at all. No icon on the desktop, not working in Amarok, nothing. All the other forums I've seen say it mounts,but won't play, or something to that nature. Anyone know a site/forum or know how to fix it?:confused:

---

### Post by spiderbatdad on 2008-02-10
[http://ubuntuforums.org/showthread.php?t=658523](http://ubuntuforums.org/showthread.php?t=658523)

---

### Post by Rocket2DMn on 2008-02-10
> **spiderbatdad said:**
> [http://ubuntuforums.org/showthread.php?t=658523](http://ubuntuforums.org/showthread.php?t=658523)

That method doesn't work.  I tried it myself, along with some other users, and it just ended up breaking the ipod until I restored it to factory settings using itunes in windows.

---

### Post by spiderbatdad on 2008-02-10
Thank you. I will not recommend it again.

---

### Post by Modified.Reality on 2008-02-10
I got this from another site

```
 

    #!/bin/sh

    modprobe sbp2
    mount /dev/sda2 /mnt/ipod/


```

unmount is

```
    #!/bin/sh

    umount /mnt/ipod
    rmmod sbp2


```

This site might help and has reference links  [http://people.csail.mit.edu/adonovan/hacks/ipod.html]("http://people.csail.mit.edu/adonovan/hacks/ipod.html")

---

