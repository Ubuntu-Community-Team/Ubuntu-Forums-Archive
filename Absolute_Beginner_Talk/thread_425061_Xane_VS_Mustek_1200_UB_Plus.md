---
title: "Xane VS Mustek 1200 UB Plus"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Orthodox_Celt on 2007-04-27
Hi to you all...

I own Mustek 1200 UB Plus scanner, and so far I have menaged to get it up and working in ubuntu from my root account...
What I need is to make it work on my user account as well.

I have already tryed this

[HTML]user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE[/HTML]

and yet it does not work...

Can enyone help me please ???

Kind regards

---

### Post by phidia on 2007-04-27
What does scanimage -l entered in a shell output?
Have you looked at the how tos at sane? [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html)

---

### Post by compiledkernel on 2007-04-27
[http://www.sane-project.org/sane-mfgs.html#Z-MUSTEK](http://www.sane-project.org/sane-mfgs.html#Z-MUSTEK)

From that list which 1200 is it?

---

