---
title: "make uninstall doesn't exist, what then!?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by mygind on 2007-07-18
Hi!

I've recently installed PHP, mySQL and Apache2 on my ubuntu feisty - compiling them using make, make install.

But I've figured I want to start from scratch again (I have to use the package manager!) and want to uninstall the files. How would I do this?

I successfully used make uninstall on mySQL, but, but the other sources doesn't seem to have a make uninstall... any other way I can easily remove PHP5 and Apache?

Thanks in advance.
Henrik Mygind

---

### Post by trskin on 2007-07-18
Perhaps this might be helpful
[http://ubuntuforums.org/showthread.php?t=98215]("http://ubuntuforums.org/showthread.php?t=98215")

---

### Post by mygind on 2007-07-18
the page you refer to doesnt tell me how to get rid of this newly installed (using make install) files, this just tells me how I should have installed it in the first place... :/

---

### Post by EndPerform on 2007-07-18
If there's no uninstall option in the make file, you're probably in for a lot of work.  You'd need to find out where the install script put the files (which can be spread among different directories) and then remove them manually.  I don't believe there is an automatic way to remove files from a manual install unless there's an uninstall option in the make file.

---

### Post by MattDTownsend on 2007-07-18
Try running sudo checkinstall in your installation directories.  Checkinstall observes what make install does and then bases a .deb file on it.  It then installs that .deb file into the database for you.  So, if it made the package "apache2" or whatever, you could then just do apt-get remove apache2 as soon as the checkinstall successfully completes.

There's a bug in the current release of checkinstall that might affect you -- it did affect my system.  If you get an error for no reason, downgrade to the edgy version from packages.ubuntu.com.  You download it, apt-get remove checkinstall, and then run sudo dpkg -i checkinstall*

---

