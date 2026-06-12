---
title: "Viewing Ubuntu Partition on OSX Question"
date: 2008-06-26
forum: Apple Hardware Users
---

### Post by ninjapenguin on 2008-06-26
Hello,

How can I have the Ubuntu partition visible on OS X?
And if I can get it to be visible can I use parallels for both my bootcamp partition and my Ubuntu partition?

---

### Post by owlgorithm on 2008-06-26
You can use ext2fsx to solve this, and it even works with Leopard.

[http://sourceforge.net/project/showfiles.php?group_id=64713]("http://sourceforge.net/project/showfiles.php?group_id=64713")

You should get the universal binary of the developer version if you want to use it with Tiger or Leopard, but you can't use the universal build on earlier versions of OS X. There are earlier versions available there, too, however.

Also, you *should* be able to use the Linux partition with Parallels. I haven't done it personally, but it seems reasonable that once Mac can read the drive, Parallels should also be able to read the drive. I have done it with Vista, and I must confess that booting the partition in Parallels felt slower than booting the virtual disk.

There are directions that may be useful here, but they are about a year old:
[http://codeshepherd.blogspot.com/2007/05/running-fedora-core-on-macbook.html]("http://codeshepherd.blogspot.com/2007/05/running-fedora-core-on-macbook.html")

---

