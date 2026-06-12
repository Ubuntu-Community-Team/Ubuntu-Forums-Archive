---
title: "Where can I get sockets.h?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by ADT on 2007-01-18
I was looking around on the forums and google to see if I could find out where to get sockets.h header file. I couldn't find anything. Sorry if this has been asked before but what package do I need to download to get sockets.h.
I installed a command-line xubuntu 6.10 system which has icewm as it's window manager.
I installed libvanessa-sockets-dev, and I installed libc6-dev from the repositories.
When I compile some c code it gives the following error:
error: sys/sockets.h: No such file or directory
Where is sockets.h?

Any help would be much appreciated.

---

### Post by moma on 2007-01-18
Du you mean "socket.h" ?

$ dpkg -S socket.h
...
linux-libc-dev


Or search for it on [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Also:
$ sudo updatedb 
$ locate socket.h

---

### Post by ADT on 2007-01-18
Damn, I am an idiot. I had typed #include <sys/sockets.h> instead of 
#include <sys/socket.h>
I should really read through my code before I post for help. Sorry about that it won't happen again.
Thanks for the help any way. I now know a few new commands aswell, thanks.

---

