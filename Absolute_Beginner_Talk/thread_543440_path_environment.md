---
title: "path environment"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by bobetko on 2007-09-05
Can somebody direct me to nice, user friendly information where I can read about setting path environment. I am interested in details about sintax, and about possible places where path should be set.

I am growing a little frustrated by this. I had several attempts to clear this out, but every time I get tired of trying, and get confused by all different advisors....

I've looked other threads and couldn't find what I am looking for. Basically, everybody trying different things and getting mixed results.  For example, I've just installed application, and updated etc/environment file and after reboot, I still have to go to app's folder to run it.

Thanks,

---

### Post by vanadium on 2007-09-05
That is because Linux is quite more complex in that respect. One place where PATHS can be set is in .bashrc in your home directory. I added the following line to it:

export PATH=$PATH:$HOME/bin

This would add my custom directory ~/bin to the already existing path settings (that have already been set in diffferent places during startup.)

In fact, probably there will already be the line "export PATH=$PATH" in your .bashrc.

All these internals can be learne from a good book on Linux in general (I remember reading DOS books also, long time ago). The Linux Documantation project has literature: "Introduction to Linux - A Hands on Guide" by Machtelt Garrels not ony makes for an interesting, but also nice read.

---

