---
title: "Ubuntu Eating UP RAM!"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-07-02
hello all,

i've just recently installed breezy on a pretty good machine... actually my work machine i've been putting it off cause i had a few bad experiences with using the default GRUB detection / installation onto the MBR... 

anyway... i noticed how fast it was on 1gig RAM, 3gig P4... the selected the auto install on my 20 gig partition so the installer selected approx 1 gig for swap... 

the first thing i did on my terminal after installation was
**$ free -m**

noticed how memory "used" was 983 mb and free was 28mb!!??? is this correct? please check on your machines too... note that i didnt have anything running when i tried this command... just the terminal

another thing... i tried
**$ top**

... and also noticed the same RAM usage! is this right? shouldnt it be around the 256 mark??? please try it on your machines too...

---

### Post by lime4x4 on 2006-07-02
john@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        875        134          0        168        436
-/+ buffers/cache:        270        740
Swap:         3012        148       2863

---

### Post by NeghVar on 2006-07-02
Free Ram does nothing for you so Ubuntu and Linux in general make the best use of it by caching files you are likely to use. Ram is fast enough that if you need something else it can push it out fast enough to get the new stuff in.

---

### Post by simonn on 2006-07-02
Not a problem.

Linux is a proper operating system. It makes use of the available resources i.e. if there is memory not being used it will use it for file caching etc...

[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

---

### Post by ProjectGod on 2006-07-02
thanks for the prompt responses!!!

i checked the GUI **system monitor** tool and noticed memory usage was actually 24 % and swap usage 1.5% :D 

so kudos to all! :D

---

### Post by Drakkor on 2006-07-02
I have just 512 Ram and use 26%

---

### Post by simonn on 2006-07-02
I suspect that the 26% = total memory - memory used for buffers/cache.

The memory used for buffering and caching is essentially free. If applications require more memory then memory currently used for buffering/caching will be used. If they do not need it then it is used for speeding up the system as a whole.

---

