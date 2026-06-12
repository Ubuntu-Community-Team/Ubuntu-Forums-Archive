---
title: "dependecies"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-06-01
how do u add dependecies to a program example mplayer

thanks for your help really aprecial it am just starting off in the world of linux

---

### Post by ash211 on 2006-06-01
I'm not sure what you mean by adding dependencies.  Those are programs that other programs require in order to work right.  If you just want to install a program and have it run correctly, install it from synaptic or on the command line (CLI) with ```
sudo apt-get install <program>
```  Those ways will resolve all dependencies (download and install the programs that are necessary to run others) for you.  That makes your life a whole lot easier:-D!

---

### Post by kvonb on 2006-06-01
Hi,

I assume you are trying to install mplayer, if so don't play around with depend problems, click here:
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)
and download Automatix, it will do it for you plus tons of other good stuff.

Regards,

Kev :mrgreen:

---

### Post by Jagot on 2006-06-01
If you really want to deal with dependencies properly then do not use apt-get - use aptitude instead:

```
sudo aptitude install <program>
```

apt-get will get all the dependencies for you, but if you want to remove the program and all it's dependencies then aptitude is the way to go.

---

