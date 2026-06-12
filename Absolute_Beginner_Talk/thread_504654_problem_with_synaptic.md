---
title: "problem with synaptic"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by ghiocel on 2007-07-19
Hi there!
I'm completely new at UBUNTU and the applications that came installed with this OS, and I'm not a computer expert neither!
I have tried to install LIMEWIRE on my computer, but the installation of Java wasn't progressing at all for a long time, so I tried to stop it, but as the installation manager wouldn't stop, I turned of my computer. When I turned it on again and tried to install Limewire again (or install anything else), synaptic gave me the following message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.
```

In this situation I can't install any new application, and I don't know what to do.

Please help!

Thanks a lot!

Lavinia, Romania

---

### Post by w4ett on 2007-07-19
From the terminal type:

sudo dpkg --configure -a

and press enter, then type your password, and press enter again

This SHOULD repair the error

---

### Post by Kobalt on 2007-07-19
You should open up a Terminal (Applications > Accessories > Terminal) and run ```
sudo dpkg --configure -a
```
After this your Synaptic should be OK.

---

### Post by ghiocel on 2007-07-20
Thank you a lot!!!
The problem is solved!

Best wishes! :KS

---

