---
title: "Help with partitioins"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by cava11aro on 2007-04-22
I'm pretty good with Windows, but im new to Ubuntu. I have an Ubunto partition and a Windows partition. How come on Ubuntu i can see both partitions but on Windows i can only see the Windows partition but not the Ubunto partition. And is there anything i can do to be able to see both?

Thanks

---

### Post by oilchangeguy on 2007-04-22
read this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by RobsterUK on 2007-04-22
The reason is that Ubuntu can read Windows partitions, but Windows has no built in support for Linux file systems like ext3 which Ubuntu uses.

I think there is a driver you can get for windows so it can read Ext3 partitions

EDIT: Have a look at [this page]("http://www.fs-driver.org/")

---

### Post by Acglaphotis on 2007-04-22
WIndows cant read/write the Ext3 filesystem that linux uses. 
More info about read/writing from windows to linux:

[http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)[http://ext2fsd.sourceforge.net/]("http://ext2fsd.sourceforge.net/")

-Acgla

---

### Post by cava11aro on 2007-04-25
thanks, i'll give these a try

---

