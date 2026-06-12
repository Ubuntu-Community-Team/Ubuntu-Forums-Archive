---
title: "Cannot Configure Keyboard!!"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by xe1ufo on 2007-04-17
HELP!! I cannot get my Spanish from Spain keyboard recognized!! Can somebody PLEASE help me?

here is my original posts--

[http://ubuntuforums.org/showthread.php?p=2466581#post2466581](http://ubuntuforums.org/showthread.php?p=2466581#post2466581)

Thanks in advance!!

Steve, central old Mexico:confused:

---

### Post by deadgobby on 2007-04-17
Did you install with the english or spanish pack? That may make a difference.
Gobby

---

### Post by xe1ufo on 2007-04-17
Thanks for your reply!

I installed both. I can select either English or Spanish in the startup menu.

---

### Post by zvacet on 2007-04-17
If you want to use spanish let it be above english and cheked.You can unchek english too.

---

### Post by TURNER on 2007-04-17
Hi, 

Perhaps you can look into your Xorg.conf file.

First back up your Xorg, just in case!

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then reconfigure the Xorg by running the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

I am pretty sure that you can set up special key boards within the Xorg config

---

### Post by xe1ufo on 2007-04-25
Dear Friends:

After trying everything suggested by everybody, and not having success, I got a wild idea.  I did an online upgrade from Ubuntu 6.10 to Ubuntu 7.04 Feisty.  ALL PROBLEMS RESOLVED!!

Thanks to everybody for their kind input!

Dr. Steve, central old Mexico.:)

---

