---
title: "360 controller on Ubuntu"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Ajguy on 2006-09-10
Hello. I just installed Ubuntu yesterday and I'm loving it so far. I was very proud of myself when I managed to install ATI drivers successfully. Now I've hit my first brick wall. The Xbox 360 Controller. I have followed the isntructions in this thread: [http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller](http://ubuntuforums.org/showthread.php?t=164040&highlight=xbox+controller)
So far, I managed to get the make package and install that, but the kernel directory isn't there. This is what I get after running the make file:
aj@aj-desktop:~/xpad360$ make
make modules -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/aj/xpad360
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
aj@aj-desktop:~/xpad360$

I look in that directory and there is no build. I was just going to make it, but it won't let me make a directory there. Anyone know how to work this out?

---

