---
title: "user out of disk"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by sagittsun on 2007-05-08
when i try to login by using gdm, it told me the user is out of disk. Then, i login as root in command line,and type the command "df",it shows the disk in which i installed ubuntu is 99% used. What's more, it showed that 73334Mb used while actually that partition is only 9543 Mb.I feel quite confused.
By the way,once i modified the file".config" when try to compile the kernel,and after that the weirdie came out.

---

### Post by jiminycricket on 2007-05-08
Maybe you can re-install the Ubuntu kernel. (linux-generic) Can you choose which kernel to boot into at boot?

Also try apt-get clean and sudo apt-get autoclean .  There's an option in Synaptic to remove unused packages as well.

---

### Post by sagittsun on 2007-05-08
> **jiminycricket said:**
> Maybe you can re-install the Ubuntu kernel. (linux-generic) Can you choose which kernel to boot into at boot?

Also try apt-get clean and sudo apt-get autoclean .  There's an option in Synaptic to remove unused packages as well.

but,why it showed me more than the partition space had been used? that's weird

---

