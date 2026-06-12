---
title: "Can someone explain restricted-modules to me?"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Starks on 2007-03-06
I don't get it. Is it a subset of "base" or something else?

---

### Post by [S|G] on 2007-03-06
They are device drivers that are not open source but are necessary to operate some hardware that you may have. They support things like wireless cards, video cards, winmodems, etc.

---

### Post by Starks on 2007-03-06
> **'[S|G] said:**
> They are device drivers that are not open source but are necessary to operate some hardware that you may have. They support things like wireless cards, video cards, winmodems, etc.
Would you recommend them for an EXTREME newbie who has some idea of how debian packaging works, but isn't ready for the hassle if there are too many compatibility issues?

---

### Post by old_geekster on 2007-03-06
Here is the explanation of "Restricted Modules": Resricted (supported software that is not available under a completely free license).

This is a very basic explanation of them, but it says it all.

It is a separate repostitory and has a complete set of available programs.  The software is supported, also.

---

### Post by [S|G] on 2007-03-06
So far I've only had one major problem concerning the restricted modules, but I think the issue has been fixed already (it was concerning using nvidia drivers for geforce 5500 + wireless drivers). What exactly do you need them for? If it is for video acceleration, there are some excellent tutorials on how to get them working (just do a quick search on the forums). There are some tutorials to get wireless working too, and they all involve installing restricted-drivers, I think.

But it's basically a matter of doing an "apt-get install linux-restricted-modules-`uname -r`" :)

---

### Post by old_geekster on 2007-03-06
> **Starks said:**
> Would you recommend them for an EXTREME newbie who has some idea of how debian packaging works, but isn't ready for the hassle if there are too many compatibility issues?
If you setup the repository in "Software Sources", you can find them in "Synaptic Package Manager".  You can either search the catalog or scroll through it if you don't know the name of the program.  I do both.

Are they recommended for complete newbie?  In my opinion, yes.  I am a newbie and I have used them since day one.

---

### Post by dstew on 2007-03-06
The word "Restricted" applies only to the license for using the software. It does not imply anything about how well it functions, if it is better or worse, or more difficult or easier to use than non-restricted ("free") software. In most operating systems, you remember the "I agree" button you click when installing software? That agreement you make restricts what you can do with the software, hence "Restricted". You can't give it away without permission, or copy it onto many computers without permission, or reverse-engineer it, or de-compile it, etc.

You don't see that button too often in the linux world, but sometimes you do. It is ok to use restricted software on linux systems.

---

