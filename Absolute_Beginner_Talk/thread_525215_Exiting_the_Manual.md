---
title: "Exiting the Manual"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by will71110 on 2007-08-14
How do you exit the man command?  I tried ctrl + c and that doesnt work.  One of my terminals is stuck in the man command and I have no idea how to exit it.

---

### Post by will71110 on 2007-08-14
DUH...ctrl + z worked.

---

### Post by kevinlyfellow on 2007-08-14
Thats the wrong way :-)

** Hit q**

ctrl-z is a very different thing.  For more info on ctrl-z visit this article [http://www.commandlinemac.com/article.php?story=20070723115723132](http://www.commandlinemac.com/article.php?story=20070723115723132)

To stop something from running in command line, use ctrl-c sometimes ctrl-d

---

### Post by will71110 on 2007-08-14
Ah ok....That works too.  Thanks.  

Seems ctrl + z is suppose to pause or run it in the background but I looked and it acctually closed it.  Donno? :confused:

---

### Post by kevinlyfellow on 2007-08-14
Well, ctrl-z puts the running app in the background and pauses it.  After you hit ctrl-z, use the command "jobs" to see it stopped in the background.  To bring it back up, use the command "fg"

All this isn't too important now, since the advent of graphical interfaces, but it is useful sometimes, and I wish I knew all of this sooner than I found out.

---

