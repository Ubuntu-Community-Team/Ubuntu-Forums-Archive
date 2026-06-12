---
title: "Opening a CD"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by kntgsp on 2007-12-13
Completely new to Ubuntu, but why won't a CD open when I double click on the CD drive?  

It obviously reads fine as it installed Ubuntu.  I stick in a cd (blank or written) and nothing.  Spins every now and then, but that's it.  Can't seem to open a window to view the disc.

---

### Post by OffAxis on 2007-12-13
what kind of CD?
data or audio?

can you access it on the command line?
```
cd /cdrom
```
```
ls -a
```

---

### Post by kntgsp on 2007-12-13
typing cd /cdrom works fine. Takes me to the directory

I just popped in an audio CD to make it easy.  Didn't do anything, can't open a window when I double click the CD ROM icon under "Computer"

But anyway yea changing directory in command works.

---

### Post by zcal on 2007-12-13
> **kntgsp said:**
> typing cd /cdrom works fine. Takes me to the directory

I just popped in an audio CD to make it easy.  Didn't do anything, can't open a window when I double click the CD ROM icon under "Computer"

But anyway yea changing directory in command works.

But is there anything listed in the directory after you cd to it?  You can always get to the directory, even if a CD isn't mounted.

Try fiddling with the settings of External Media (something like that, can't remember what it's called in English) in your preferences menu.  You should be able to tell it to mount the CD automatically and play it with a specified program if it's an audio CD.

---

### Post by kntgsp on 2007-12-13
> **zcal said:**
> But is there anything listed in the directory after you cd to it?  You can always get to the directory, even if a CD isn't mounted.

Try fiddling with the settings of External Media (something like that, can't remember what it's called in English) in your preferences menu.  You should be able to tell it to mount the CD automatically and play it with a specified program if it's an audio CD.

Yea I try to do that and it gives me a Kernel 2.6 error:

> Volume Management Not Supported

The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.

---

### Post by kntgsp on 2007-12-13
anyone?

---

### Post by rsambuca on 2007-12-13
Strange.  Normally when running Ubuntu, if you insert an audio CD then a window will open.  What version of Ubuntu are you running?

And in the future, please wait a day or two before bumping your own threads.

---

### Post by kntgsp on 2007-12-13
Running 7.1, just installed today.

Everything else runs fine, internet works, etc.

---

### Post by rsambuca on 2007-12-13
The problem is with your volume management and the hald error.  

Try opening a terminal and re-installing the ubuntu-desktop.

---

