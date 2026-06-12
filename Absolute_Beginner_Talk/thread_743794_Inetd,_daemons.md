---
title: "Inetd, daemons?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by defmomo on 2008-04-03
Can anyone explain to me what exactly daemons and inetd are? It seems to me the only difference is that one is running continuously, and the other one (inetd) is only launched when inetd detects acces to a specific service. 
Also, it appears inetd isn't installed by default, but i can see and edit /etc/inetd, has it been added recently? (i am using Ubuntu 8.04)
I am trying to understand this because i am setting up an svn server, and if inetd is what i think it is, i would prefer to use it.

---

### Post by Hospadar on 2008-04-03
a daemon is any userspace (not a kernel module) process that runs in the background (it may not always be running, but it will at least run when called) that provides some OS service.  Basically, anything not covered by the kernel that requires more than just a library call will fall into the daemon category.  As for Inetd, I'm not personally too familiar with it, you might want to check the community docs in my sig, or [wikipedia]("http://en.wikipedia.org/wiki/Inetd").

---

### Post by defmomo on 2008-04-03
Would a script placed in /etc/init.d/ containing the svnserve daemon initialisation command make the svnserve daemon accessible as soon as the PC boots? This solution does seem... 'untidy'
Is there some other information about inetd in Ubuntu, since I have read the Wikipedia page for it, and it doesn't give any specifics of  how it interacts with the OS.

---

