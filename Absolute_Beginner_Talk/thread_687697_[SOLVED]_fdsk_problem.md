---
title: "[SOLVED] fdsk problem"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by nynoah on 2008-02-04
My computer went to do the usual file system check and came back with errors.  It said to run a manual Fdsk to correct that.  I am not sure how to do that.  I tried typing in fdsk into the bash commands but that did not work.  What are the correct commands that I need to run fdsk manually from bash?

Thanks
Noah

---

### Post by jan quark on 2008-02-04
try 
```

sudo fsck
```

also have a look at
```

man fsck
```

---

### Post by nynoah on 2008-02-04
why is is fsck?  instead of fdsk?  Just wanting to learn

---

### Post by jan quark on 2008-02-04
read this

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

---

### Post by Cannaregio on 2008-02-04
As Jan said just above, use man to learn what a command does.

However:
The following code for a command COULD (underlined: could) work:
from live-cd, use gparted in order to check if your main hard disk is sda1 or whatever
and then... 
(again: [COLOR="Blue"]sda1 [/COLOR] ONLY if your disk is really sda1, check in gparted through a live-cd first if you don't know)
..then use this code:

```
e2fsck -b 32768 /dev/[COLOR="Blue"]sda1[/COLOR]
```

good luck. The code above helped me many times, _especially when Linux was garbaged by some new virtual drive installation with reboot in my xp dual boot partition_.

---

### Post by jan quark on 2008-02-04
to check which disk  is which disk, and which partition which....

you can also run

```
sudo fdisk -l
```

---

### Post by FuturePilot on 2008-02-04
In addition to the above, do not run fsck on a mounted drive. It will most likely destroy data.
Also use the -C option with fsck to get a nice little progress bar :)

---

### Post by nynoah on 2008-02-04
I am back up and running now.  I just had to type fsck.........and wait a while.......lol

Then I just hit yes for all the questions.   Now I am back up and running.


Thanks everybody


Noah

---

### Post by jan quark on 2008-02-04
great to hear

please mark this thread as solved using the thread tools
thank you

---

### Post by nynoah on 2008-02-04
Ok done.............Thanks everyone for taking the time to help me.  This is why I stick with Ubuntu.  Because of the users that help each other.

---

