---
title: "Compiling kernel from source problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-04-06
I was playing around with this guide 

[http://www.linuxforums.org/desktop/the_newbies_guide_to_compiling_your_first_kernel.html](http://www.linuxforums.org/desktop/the_newbies_guide_to_compiling_your_first_kernel.html)

and i came across a problem

i followed all steps exactly as they are written

But i came across a problem 

in the step **Configuring Your Kernel**

when i type **make xconfig** in the terminal

i get an error like this

xxxx@xxxx-desktop:/usr/src/linux$ make xconfig
  CHECK   qt
*
* Unable to find the QT installation. Please make sure that
* the QT development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `s cripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2
giannis@giannis-desktop:/usr/src/linux$ make xconfig
\  CHECK   qt
*
* Unable to find the QT installation. Please make sure that
* the QT development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2

What is the problem and how can i fix it?

---

### Post by heimo on 2007-04-06
Well... This isn't solution to run xconfig, but it's a workaround. You can do the same configuration using "make menuconfig" or (with even more spartan) "make config". If "menuconfig" won't work, you may need to install libncurses5

```
sudo aptitude install libncurses5
```

There seems to be instructions for building custom kernel for Ubuntu over here:
[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

### Post by timv on 2007-12-26
It's somewhat sad that more than six month have passed and no one has bothered to post an answer to a pretty straightforward question. I just joined the board out of frustration because I keep running into this myself when I have a question: I can find lots of messages asking the same question, but there are never answers.

Perhaps the original poster already has his or her answer, but for the sake of those like myself: I just solved it by trial and error (for Ubuntu 6.10 Edgy Eft and kernel "2.6.17-12-generic") by installing the packages qt3-dev-tools and libqt3-mt-dev.

I first tried installing some qt4 dev packages and they didn't help. Perhaps I installed something there that was also needed. But adding "qt3-dev-tools" and "libqt3-mt-dev" was what finally made it work for me.

---

### Post by gravyflex on 2008-01-11
> It's somewhat sad that more than six month have passed and no one has bothered to post an answer to a pretty straightforward question.

Thanks alot Timv!!! I was just about to give up.

---

### Post by balak on 2008-01-21
> **timv said:**
> I just solved it by trial and error (for Ubuntu 6.10 Edgy Eft and kernel "2.6.17-12-generic") by installing the packages qt3-dev-tools and libqt3-mt-dev.


Thanks, timv! Exactly the answer I was looking for.. Good that you posted your results.

---

### Post by Iron_maiden_forever on 2008-02-12
Thanks! I was searching for help on this too!

---

