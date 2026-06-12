---
title: "What is the diffrence in kernels ?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by bbmw on 2006-02-04
When installing "breezy" I was offered a choice of installing several kernels
somthing like this:

      Which kernel do you want to install ?
          linux-386
          linux-386-image
          linux-386-2.6.12-9-image

my questions are:

1) is there any diffrence in them ?

2) what is the diffrence between them ?

3) how do I decide which one is best for me ?

4) shouldn't the installer provide some information to help begginers ?

I could not find this by searching so I hope it has not been asked before.

---

### Post by JShadow on 2006-02-04
These are actually all the same kernel that you are installing. The first two are what are known as meta packages, which aren't actually the software you want, but allow your kernel to be automatically updated due to the dependencies.

So...

This is the class of kernel in Ubuntu that you are using:
> linux-386
386 is the most compatible. There are others you may want to use depending on what kind of processor you have. This package depends on the linux image package, and the restricted modules, which includes some additional drivers.


This is the package which depends on the actual image package:
> linux-386-image


This is the actual kernel:
> linux-386-2.6.12-9-image
2.6.12-9 is the version number of the kernel. linux-386-image will always depend on the highest version number so your kernel will automatically upgrade so long as it's installed.


I hope this clears things up a little!

---

### Post by bbmw on 2006-02-04
[QUOTE=JShadow]These are actually all the same kernel that you are installing. The first two are what are known as meta packages, which aren't actually the software you want, but allow your kernel to be automatically updated due to the dependencies.

So...

This is the class of kernel in Ubuntu that you are using:

386 is the most compatible. There are others you may want to use depending on what kind of processor you have. This package depends on the linux image package, and the restricted modules, which includes some additional drivers.


This is the package which depends on the actual image package:



This is the actual kernel:

2.6.12-9 is the version number of the kernel. linux-386-image will always depend on the highest version number so your kernel will automatically upgrade so long as it's installed.


I hope this clears things up a little![/QUOTE]

Thanks for helping.

Let me see if I have this right...
The main diffrence is when (or maby what causes) it upgrades and that the 
linux-386 includes the additional drivers from the restricted package and will
be upgraded whenever the image package or restricted package changes?

linux-386-image will be upgraded only when the image package changes
(major upgrades only?)

linux-386-2.6.12-9-image will be upgraded for minor changes to the image package

(I understand about 386 vs 686 etc.)

---

### Post by JShadow on 2006-02-07
Essentially, the  linux-386-2.6.12-9-image is the package that will be actually upgraded. The rest are just there for dependency's sake.

Having  linux-386 installed causes the "restricted" drivers to be upgraded at the same time.

---

### Post by Razorback on 2006-02-07
One question I have is:  Is it bad to have files from both 386 and 686 on your pc?  I am trying to get a video card configured and used a howto that had me remove the restricted module.  It was 386.  When reinstalling I picked 686 because I was running a Celeron processor and read that 686 was for it.  Will this cause problems?  When booting in recovery with Grub, I now see 686 and 386 as a selection.

---

