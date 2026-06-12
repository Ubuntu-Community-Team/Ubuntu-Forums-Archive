---
title: "Kernel swapped by mistake"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by getut on 2006-11-14
Like most here, I'm new to Ubuntu and I'm running Edgy.

In the last 2 days of trying to get my ATI drivers set up, I carelessly ran a command that I believe changed out my kernel to the wrong one.

My PC is a Pentium 4 dual core laptop and if I'm not mistaken it should be running the i686 version of the kernel, but after I ran the linux-restricted-modules command in one of the tutorials for getting the ATI drivers going, I rebooted and now Grub is showing boot options for 386 and generic but no 686.

I'm still functional but how do I get back to 686 kernel or am I imagining that it ever was on it.

---

### Post by Tomosaur on 2006-11-14
The 686 kernel has been replaced by 'generic' in Edgy. If you take a look at synaptic, you can see that the 686-kernel versions actually stated that they have been replaced by generic, so you shouldn't worry.

---

