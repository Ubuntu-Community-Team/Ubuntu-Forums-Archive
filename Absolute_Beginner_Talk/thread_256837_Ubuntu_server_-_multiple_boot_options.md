---
title: "Ubuntu server - multiple boot options?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-13
I have installed Dappper Drake Server (at least that was what I thought?). 

When I boot I have a selection of seven different boot options such as:

Ubuntu Server
Ubuntu Bigiron
Ubuntu K7
...

Is this normal or have I installed Ubuntu 7 times?

Thanks

---

### Post by whizbaby on 2006-09-13
Don't know which CD you used to install or what options you took, but these are different hardware architectures you can choose from. (I guess 'Server' is for a 'normal' PC (i386))

---

### Post by steve.horsley on 2006-09-13
You have a choice of several different kernels. There is probably a rescue mode. Bigiron is probably optimised for something big (lotsa memory maybe). K7 is for Opteron CPUs (I think). They must be documented somewhere, but I don't know where.

---

### Post by Calculator on 2006-09-13
Thanks - I am installing off a server disk and a lot of the installation has taken place via the web.

I am using a server with xeon chips, therefore can I remove kernals that will not work on my machine?

Thanks for the help : )

---

### Post by steve.horsley on 2006-09-14
Theydon't take up that much disk space so they're not doing much harm. You may as well leave them unless you're really sure you don't want them.

You can always edit /boot/grub/menu.lst (with care and a backup) and comment out the stanzas that you don't want to be shown.

---

