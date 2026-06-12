---
title: "Questions about source code hacking and manpages"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by polarix on 2005-09-27
I am new to linux but for my studies i need to do some source code hacking(e.g. Tracing some device drivers). 

How can i read the source code in my Ubuntu?

Also, how can i read the manpages of the system calls in Ubuntu? e.g.
In my ubuntu, i can't get the "man 2 fork" to work as if in an unix system.

---

### Post by Wolki on 2005-09-27
To see the source code, you'll need to install the source packages. Make sure you have the relevant deb-src line in your /etc/apt/sources.list. Something like

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe

 Then you should be able to install source code with synaptic, it will also tell you where you can find it after installing.

---

