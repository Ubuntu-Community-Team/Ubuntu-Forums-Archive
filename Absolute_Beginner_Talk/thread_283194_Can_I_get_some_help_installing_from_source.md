---
title: "Can I get some help installing from source?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by BdON003 on 2006-10-23
Hello all, I am trying to install gtkpod with video transfer support for my video iPod.  this is the how to: [https://help.ubuntu.com/community/iPodVideoTransferring]("https://help.ubuntu.com/community/iPodVideoTransferring")
Im at the part where I need to install mpeg4ip.  After "sed -i "s/SUBDIRS = \. test util/SUBDIRS = \./" lib/mp4v2/Makefile", the next thing is the command "make" returns "bash: make: command not found".  This is my first time doing something like this so any help is appreciated.

---

### Post by po0f on 2006-10-23
BdON003,

```
$ sudo aptitude install build-essential
```

Building gtkpod from source, you will find you require more than that package.

---

### Post by GameboyHippo on 2006-10-23
It may be easier to simply enable the multiverse repository and install the package via synaptic.  First, let's get the multiverse repository enabled.  Go to System->Administration->Software Sources.  In the first tab, check the box that says "Software Restricted by copyright or legal issues (multiverse)" Then hit close.  Now go to System->Administration->Synaptic.  Press CTRL+F and type gtkpod.  It should show up.  Just check the box next to it, hit apply and Kablam! You've got gtkpod on your system!  No need to compile nothin!

---

### Post by BdON003 on 2006-10-24
Thanks, will that have video support too?

---

### Post by Sef on 2006-10-24
>  ... enable the multiverse repository .... 

Here is how to enable the [repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

