---
title: "PSDoom in Deb form"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Kat of Zion on 2008-04-10
Anyone figured a way to get this program to install via a deb?

[http://sourceforge.net/project/showfiles.php?group_id=3418](http://sourceforge.net/project/showfiles.php?group_id=3418)

Its the weirdest program I have seen on Linux but I cant imagine that some Ubuntu user hasnt run this on their machine.

---

### Post by caryb on 2008-04-10
It hasn't been updated since 2000 that was back in the 2.2 kernel days! I probably wouldn't load something of that vintage on my machine.


Cary

---

### Post by Hospadar on 2008-04-10
If you want to take some source package and install it as a deb, you've got a couple options:

Research how to build debs and build your own (it's actually pretty easy)

or,

If the program uses the standard "./configure" "make" "sudo make install" sequence to build and install, you can replace the "sudo make install" step with "sudo checkinstall"  This will build a deb and install it.  The deb won't have any dependancies or anything like that, but it makes it convenient to uninstall the package when you want.  You'll have to get checkinstall first "sudo apt-get install checkinstall"

---

