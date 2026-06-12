---
title: "Almost all my browsers are dead"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by sirgazil on 2008-02-14
I have a big problem.

I made a fresh install of **Ubuntu 7.10** and install about 50MB of security Updates. The problem is, **after the security updates**, Firefox stopped working; now every time I click the Firefox icon to start it, it doesn't even appear. I downloaded Epiphany, Opera, Kazehakase, and Iceape, and only the latest is working.

I'd like to understand what's happening.

Thanks in advance.

---

### Post by LaRoza on 2008-02-14
Try running them from the command line.

Type "firefox" in the terminal to see what happens. If it gives errors, post the output, if it starts, the launcher is probably broken.

(Type "opera" also, if it is still installed.)

---

### Post by nudnik on 2008-02-14
> **sirgazil said:**
> I have a big problem.

I made a fresh install of **Ubuntu 7.10** and install about 50MB of security Updates. The problem is, **after the security updates**, Firefox stopped working; now every time I click the Firefox icon to start it, it doesn't even appear. I downloaded Epiphany, Opera, Kazehakase, and Iceape, and only the latest is working.

I'd like to understand what's happening.

Thanks in advance.

Its very difficult to say exactly whats gone wrong without volumes of information, however, it needn't be that complicated. It might be as simple as re-installing firefox. Open a terminal, become root and:

apt-get remove firefox
(wait for the removal to complete)
apt-get install firefox

Restart the machine for giggles and see what happens. 

If things continue to go awry, give us your hardware specs, and the output of any logfiles that might be relevant. Remember the mascot....see below.

---

### Post by sirgazil on 2008-02-14
> **LaRoza said:**
> Try running them from the command line.

Type "firefox" in the terminal to see what happens. If it gives errors, post the output, if it starts, the launcher is probably broken.

(Type "opera" also, if it is still installed.)

```
fla@nutabe:~$ firefox
Segmentation fault (core dumped)
fla@nutabe:~$ epiphany
Fallo de segmentación (core dumped)
fla@nutabe:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Fallo de segmentación (core dumped)
```

Hardware specs:

**Processor:** AMD Athlon XP 2200 +
**RAM:** 512 MB
**Hard drive:** 40GB
**OS:** Ubuntu 7.10
**Kernel:** Linux 2.6.22-14-generic

---

### Post by sirgazil on 2008-02-14
Can someone explain to me what does the above output mean? 

I'll keep this as an alternative:

> apt-get remove firefox
(wait for the removal to complete)
apt-get install firefox

Restart the machine for giggles and see what happens.

---

### Post by rkd on 2008-02-14
You said firefox stopped working after the updates, so I assume firefox did work before the updates.

So, clearly, something went wrong during those updates. Maybe the updates were interrupted by some kind of error and didn't complete properly.

One thing you could try is to update again. In a Terminal enter```
sudo apt-get update
sudo apt-get upgrade
```That probably will get more than just security updates. If you must limit it to security updates, I don't know how to do that.

If getting the updates again doesn't fix the problem, I think the next thing I would do is copy any files you want to keep to someplace off of the computer and do a fresh install of Ubuntu. Make sure things seem to be working, then get the security updates again. Then see whether the updates caused trouble again or went okay this time.

If the security updates didn't cause trouble this time, you are done, except for restoring the files you saved before reinstalling. If the security updates cause the same problem again, we'll have to think of something else to try.

---

### Post by rkd on 2008-02-14
Oh, I forgot to answer your question about what the output you posted means.  In simple terms, it means that something is seriously wrong in your system. Segmentation fault means the program tried to use memory it wasn't supposed to use.

---

### Post by jan quark on 2008-02-14
just a wild guess

try this commands perhaps they will help

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by mtgrocks04 on 2008-02-14
I had this problem once...it was after I installed some add-ons. I went into the firefox directory and removed the add-ons and everything worked fine after that...just a thought...

---

### Post by sirgazil on 2008-02-14
Thank you all for taking the time to answer but I decided to switch to Ubuntu 6.06 LTS, Gutsy is not working as I expected :(

See you around!

---

