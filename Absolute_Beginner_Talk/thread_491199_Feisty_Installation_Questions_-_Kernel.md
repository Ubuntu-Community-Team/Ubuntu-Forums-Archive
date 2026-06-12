---
title: "Feisty Installation Questions - Kernel"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-07-03
I have been using Dapper Drake for about 9 months and I am very please with it.  I attempted to install Feisty Fawn (not upgrade) as a second Ubuntu bootable installation in order to start leaning the new feature of Ubuntu.  I have the multi-booting working well, but almost immediately experienced problems is setting up and configuring Feisty.  These problems were relative to the modem dialup internet connection and the nVidia driver installation.  In attempting to determine my problem, I noticed that my kernel (uname -r) is "generic" rather than "386" as I would expect on my Intel EC Core 2 Duo.  This concerned me so I did some further checking.
If I boot the LiveCD for Dapper, or the Hard Drive installation of Dapper and execute "uname -r" I get the "386" indication for my kernel.
However, if I boot the LiveCD for Feisty, or the Hard Drive installation of Feisty and execute "uname -r" I get the "generic" indication for my kernel.

Is this normal? Is the installation failing to properly probe my hardware?  

I would like to resolve this question before I continue trouble shooting my other modem and nvidia problems.

---

### Post by greg_g on 2007-07-03
That isn't a problem.  On my Core2 Duo I have the generic kernel.  And I am not experiencing any problems with it.

It might just be the way things are labeled now.

---

### Post by Bachstelze on 2007-07-03
The generic kerne became the default in Edgy, when it became obvious there was no point in keeping all the subarch-specific kernels.

---

