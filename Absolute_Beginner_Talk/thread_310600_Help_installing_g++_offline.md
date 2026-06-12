---
title: "Help installing g++ offline"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by Penguin_Reaper on 2006-12-01
Can someone please tell me how to install g++ offline?
I've been trying for about two weeks to figure this out.
*sigh* It would be exetremely easy if I had the internet.

---

### Post by daller on 2006-12-01
The easiest way, is to install it on another machine, and then copy the fetched packages to the other machine.

This is the directory:

/var/cache/apt/archives/

The packages you are interested in:

cpp, gcc, g++-4.1, gcc-4.1

...and of course:

g++

Good luck!!!

Download it here:

[http://www.dallerweb.dk/ubuntu/gcc.tar.bz2](http://www.dallerweb.dk/ubuntu/gcc.tar.bz2)

---

### Post by echo $USER on 2006-12-01
You have access to the net somewhere or you would not have been able to make this post.  So, go back to where you made this post and follow this link...

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=g%2B%2B&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=g%2B%2B&searchon=names&subword=1&version=edgy&release=all)

Pick hte version that supports your ubuntu version and download the latest build of g++.  then go to you ubuntu box, and install the .dpkg... then pray there are not any dependancy issues.

---

