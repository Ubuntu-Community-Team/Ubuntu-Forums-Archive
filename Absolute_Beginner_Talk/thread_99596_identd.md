---
title: "identd"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by twaern on 2005-12-05
how do i go about installing identd for connecting to dalnet, etc..

---

### Post by gruepig on 2005-12-06
Use aptitude (or whatever you are using for package management), find the package called pidentd, and install it.  That should be all that is needed.

In a bit more detail, if you are interested ....

There are a number of identd packages to choose from.

dpkg -l '*ident*' 

from a terminal/command line will show you a bunch of options.  Say you pick pidentd (I don't know enough about identd to know if there are any differences between the packages; I suspect it doesn't much matter).

sudo apt-get install pidentd

That's it.

This installs /usr/sbin/identd which is started out of /etc/identd.conf.  You won't see a separate daemon process running, but you can verify that it's running with 'nmap -p 113 localhost' or 'telnet localhost 113'.  Should you need to make any configuration change (doubtful), edit /etc/identd.conf.

---

