---
title: "Kernel source and no sound"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-30
Still have not got my sound going. Went to alsa website and found some new source codes. But ./configure complains about a kernel that supposed to sit in "/usr/src/linux" folder. The problem is the "src" folder is empty. It should contain a version.h file, but there is none.

If ound some other version.h file and copied it there, but it is not the correct version. So how do I go about changing a kernel? It sound like I could loose all my settings if I update/change a kernel, how can I prevent it from happening? I only want the specific app pointing to the correct kernel.

Another hitch is that when I compile new app from source, synaptic do not have the new versions. I tried with alsa-lib 1.0.9 but it still show 1.0.8? Any reason why and will I be able to correct it?

---

### Post by jerrykenny on 2005-07-30
It looks like you need to unpack the actual kernel source ( for your running kernel) somewhere,   and then make a symbolic link   (called linux)


eg   ln -s /home/kernel-2.6.??  /usr/src/linux

---

### Post by GrootBrak on 2005-07-31
[QUOTE=jerrykenny]It looks like you need to unpack the actual kernel source ( for your running kernel) somewhere,   and then make a symbolic link   (called linux)


eg   ln -s /home/kernel-2.6.??  /usr/src/linux[/QUOTE]
 And where will i find the kernel source?

---

### Post by az on 2005-07-31
If you need the full source, install the linux-tree package.  You will need to compile the kernel to be able to use the sources.  Just try installing the linux-headers package for your kernel.  Use that instead of the full source.

And if you compile something from source and install it, synaptic does not know about it.  So, you will not see a change in the package versions since you did not install any newer packages.  This is a great way to break your system.

---

### Post by GrootBrak on 2005-08-01
[QUOTE=azz]If you need the full source, install the linux-tree package.  You will need to compile the kernel to be able to use the sources.  Just try installing the linux-headers package for your kernel.  Use that instead of the full source.

And if you compile something from source and install it, synaptic does not know about it.  So, you will not see a change in the package versions since you did not install any newer packages.  This is a great way to break your system.[/QUOTE]
 uname -a gives me this.

> Linux HomePC 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

Synaptic don't have it. I have 2.6.10.5-386 as well from Synaptic. For some reason I am adviced to install the headers with the same number in order to compile source codes. Now how on earth will I get the two numbers to correspond?

---

