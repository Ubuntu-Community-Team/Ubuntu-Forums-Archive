---
title: "multiple kernel version shown at GRUB?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by cyclingwilly on 2006-12-14
Hi,
My name is Willy.
 
I am a happy beginner of Ubuntu.  Amazed by how the new OS gave my 6 year old P3 PC a rebirth.
 
Yesterday I installed version 6.06 for the first time on my machine and the process was smooth and fantastic with the fact that I was able to run firefox and IM at the same time when the OS was being installed!  (everyone remember the 45 min wait you have to go through when installing XP?) after reboot, GRUB presented me with 2 kernel versions to start the OS with along with my old XP pro.  I kind of just ignored that and picked the latest kernel in non-safe mode and carry on.
 
With the impulse of always having to have the most updated version of softwares, I proceeded to upgrade version 6.06 to 6.10.  Again, the process was really simple and problem free and my XP using buddies were shocked through IM that I was doing an major version upgrade when I was chatting with them.  After reboot, now i was presented with THREE versions of kernels under GRUB plus XP!!!
 
Sorry I don't have the exact version numbers here as I am at work but I am just curious to know if this is something everyone experiences as Ubuntu is constantly under development and testing and all the users are given the options to try different kernel versions or this happens because something I chose during installation?  Beside editing my GRUB to have one version shown, can i uninstall the kernels i don't need?  How do I do that?:confused:
 
thanks in advance! 
 
Wlly

---

### Post by Bachstelze on 2006-12-14
Hi and welcome to Ubuntu :)

Just uninstall the kernel image packages you don't want with your favourite package management app (Synaptic for ex.), they will be automagically removed from the list. The packages are called *linux-image-foo.bar.baz-bop-arch* (for example *linux-image-2.6.18-3-686*).

---

### Post by xnij on 2006-12-14
You have to remove them manually; Ubuntu doesn't remove the previous version of the kernel when upgrading. 

Use synaptic to remove the previous unneeded versions _after_ you're certain the new kernel is working. :) It will also remove it from the Grub config.

---

### Post by oracle5 on 2006-12-14
You can uninstall them but I like to have a fall back kernel in case something goes wrong with the new one. Its really just a personal preference though.

oracle5

---

### Post by sailor2001 on 2006-12-14
> **xnij said:**
> You have to remove them manually; Ubuntu doesn't remove the previous version of the kernel when upgrading. 

Use synaptic to remove the previous unneeded versions _after_ you're certain the new kernel is working. :) It will also remove it from the Grub config.

I believe most ubuntu users leave 2 kernels in place. the newest one and the one you just up-graded from....that way you have one to fall back on if the newest has a problem

---

### Post by bodhi.zazen on 2006-12-14
If the new kernel works I remove all the old ones.

I also keep a backup in the event of total failure.

---

