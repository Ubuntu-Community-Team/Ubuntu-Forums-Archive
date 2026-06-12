---
title: "Fix the macbook crackling sounds once and for all."
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by volanin on 2008-07-01
Some people using INTEL-BASED macbooks have already experienced the
annoying crackling sound in the macbook left speaker. There was already
one solution posted in this thread:

[http://ubuntuforums.org/showthread.php?t=611345](http://ubuntuforums.org/showthread.php?t=611345)

But even this solution solves the problem only sometimes. At least in my
experience, it seems that some programs somehow reset the sound system
and the crackling returns.


Now I have come with a new solution, but be warned, it's for advanced
users only since it involves patching and recompiling the kernel.


While I was playing with the vanilla kernel 2.6.25, I realized that the
Intel HDA driver in this version is already fixed and does not have the
crackling sound at all. Unfortunatelly, at least for me, this kernel has
a few shortcommings that make it quite unstable on my system...
and besides that, I really prefer to use the patched-and-tested
Ubuntu kernel.

So today, I was trying to backport the Intel HDA driver from 2.6.25 into
the Ubuntu kernel, and it was indeed surprisingly easy and pleasurable,
since now I am running a stable Ubuntu kernel with perfect sound.

I have already been using it for a couple hours and a couple reboots and
I have not yet heard any crackling at all. The sound is crisp and clean!

For those of you brave enough (or annoyed enough!) to try this, I have
attached a patch in this post. The steps I used are the following:
*(You must enter every command below as root)*


**1.** *apt-get install build-essential libncurses5-dev*

This command will install everything necessary to configure and compile
your new kernel.


**2.** *apt-get source linux-source-2.6.24*

This command will download the current hardy kernel and apply all necessary
Ubuntu patches. It will create a folder with a ready-to-compile kernel.


**3.** Patch your kernel with the attached file and compile it!


If you try this solution, please post your results and observations here.
Thank you a lot.
:)

---

### Post by infinitusagnitio on 2008-07-01
Can you attach the instructions for patching the kernel?  I tried searching it on the web, but all I got was [patch -p1 < 'patchname'] for gz files, and whenever I do that I get permission denied (including with sudo).  I looked one up for bzip, but that didn't work either.

---

### Post by volanin on 2008-07-01
Try this:

```
$ zcat PATCH.gz | sudo patch -p1
```

---

### Post by infinitusagnitio on 2008-07-01
Permission denied, same error.

---

### Post by aurorix on 2008-07-04
If I boot up with a crackly left speaker, I fix the problem by:

```
sudo /sbin/alsa force-reload
```

This will force an unload/load for all the ALSA modules; the crackles will usually disappear with it (if not, just keep trying until it does).

---

### Post by russo.mic on 2008-07-06
Don't know if this helps or not, but I had this problem until 2 weeks ago when I installed Ubuntu Studio.  It hasn't happened once since.  

Russo

---

