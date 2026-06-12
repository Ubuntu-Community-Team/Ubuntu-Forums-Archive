---
title: "[SOLVED] Updates have failed"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Sunny Jim on 2007-11-05
I installed Ubuntu 7.04 days ago and was told I had 130 odd updates to be installed.  I started but got an error message with Package Manager  'Error occured.  E:dpkg interrupted run  'dpkg --configure -a' to correct.   This I did but the message was that I needed 'superuser privileges'  What on earth is this?   I opened Update Manager and an error message said: Software Index broken - cannot remove or install.  Run 'sudo apt-get install -f'  When I did the next message was that I must run ' sudo apt-get install -a' to correct, but this comes up as an unrecognized command line.
Therefore completely stuck!  Help please!

---

### Post by jaybombalous on 2007-11-05
try this for the first command instead.

```
sudo dpkg --configure -a
```

sudo gives u root privileges (**superuser access**). If you want to change something in the internal file system of the OS, **U MUST** be root. Any error saying u don't have permission to access, means u probably need to be root to do what your are trying to do.

---

### Post by jaybombalous on 2007-11-05
```
dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.
```

straight out of the manual for dpkg. What happen was u needed to configure a unpacked package that was never configured before u can continue.

---

### Post by Sunny Jim on 2007-11-05
Thank you jaybombalous for your reply.
In reply to your first suggestion, I ended up with a screen of gobblydegook that I could not make sense of.
For the second suggestion, I just do not understand what it means!!

If downloading suggested updates results in a major disaster, then Ubuntu has to be CONSIDERABLY more user friendly than it is at present if it is ever to succeed Microsoft - just look at the trouble to configure a dialup modem!!

---

### Post by por100pre1 on 2007-11-05
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install -f
```

I just fixed a Windows issue some minutes ago, it took me a whole week to find a solution! Is that user friendly?

EDIT: BTW, I using Ubuntu since May, I've been a Windows user for many years.

---

### Post by Sunny Jim on 2007-11-06
Many thanks por1OOpre1 - I tried that and it came up with the reply run <sudo apt-get install -a>.   You may not believe it ( I still don't really) but the machine sorted itself out overnight.   But I have noticed that there are two kernels now installed (different nunbers) on the boot-up page.  I wonder if there was some conflict between then.
Whilst I have your attention, should I install Terminal with the SuperUser option as that was requested during my glitch and I had then no idea of what it meant?
Thanks again

---

