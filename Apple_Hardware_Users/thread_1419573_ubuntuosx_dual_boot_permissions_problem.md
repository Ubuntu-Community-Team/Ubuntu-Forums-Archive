---
title: "ubuntu/osx dual boot permissions problem"
date: 2010-03-02
forum: Apple Hardware Users
---

### Post by mikeryker on 2010-03-02
Hey guys,
I'm currently dual booting ubuntu 9.10 and osx 10.6. I have 3 partitions set up in my hard drive. One for osx one for ubuntu, and one larger partition for shared data between the two. I set my ubuntu uid/gid to match my osx uid/gid (uid=501 gid=501), however I am still having problems with the permissions in my data partition. From osx I have full acess, but from ubuntu its read only...any ideas?

---

### Post by linuxopjemac on 2010-03-02
from what I understand is that journaling should be off in OSX to have a access to data. It is still not clear if you then can access or not. It is very difficult.

---

### Post by mikeryker on 2010-03-02
My data volume is formated hfs+ no journaling...the weird thing about this is that at first changing the uid/gid in ubuntu worked fine but for some reason now its read only...

---

### Post by handy on 2010-03-03
I only read write from OS X, to/from Ext3, via [http://www.paragon-software.com/home/extfs-mac/](http://www.paragon-software.com/home/extfs-mac/)

Though it doesn't work (at this stage) beyond 10.5. unfortunately.

---

