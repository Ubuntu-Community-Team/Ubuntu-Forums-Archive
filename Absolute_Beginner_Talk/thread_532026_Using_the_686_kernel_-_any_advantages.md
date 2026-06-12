---
title: "Using the 686 kernel - any advantages?"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by BJ Bignell on 2007-08-22
Hello,

I have Ubuntu Feisty installed on a PIII laptop, and would like to try running the 686 kernel.  There seems to be a big difference in opinion about whether or not it makes a difference.  Does the 686 kernel really do anything different?

I've tried to install the 686 package, but it doesn't work.  Probably because it's "obsoleted" by the generic image?  Why, and what does the generic image offer?  Is it a straight 386 package, or something else?

Thanks for the help!
BJ

---

### Post by asmoore82 on 2007-08-22
[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)
:KS

---

### Post by BJ Bignell on 2007-08-22
Thanks for the link; makes everything clear.  If I really really wanted to, I suppose I could always download the sources and do my own custom compilation, eh?  Maybe if I've got a rainy day to burn, sometime in the future...  :)

---

### Post by igknighted on 2007-08-22
> **BJ Bignell said:**
> Thanks for the link; makes everything clear.  If I really really wanted to, I suppose I could always download the sources and do my own custom compilation, eh?  Maybe if I've got a rainy day to burn, sometime in the future...  :)

For when you do get around to it: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

In reality, compiling a kernel is very easy.  It just can take a while (takes about 45 minutes on my PC, can take upwards of 2 or 3 hours on others).  During that time you can use your PC, it'll just be slow (like running winXP during a virus scan).

I think you would find a custom kernel would speed things up a bit.  I am running Gentoo on my pIII HP e-pc and while its only got like 1ghz, 256ram it runs amazingly quick (custom kernel, KDE 3.5.7).  If you really want to breathe speed into an older computer like that, give Gentoo a try.  Arch is also a good choice.  These are certainly harder distros to adapt to, but the documentation for both is excellent... so if you're up for a challenge, go for it!

---

