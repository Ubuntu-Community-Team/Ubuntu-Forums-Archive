---
title: "Kernel upgrade question"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Martango on 2006-07-29
Hi folks!

After installing my brand new Ubuntu Dapper Drake 6.06 the Update Manager asked me to download updates. That affected the kernel that somehow was upgraded from 2.6.15-23-386 to 2.6.15-26-386 together with the approx. 130 updates. So now i have 4 lines in the Grub loader instead of 2. Everything is working fine with the new kernel version. But my question is - what is the normal thing to do after a kernel upgrade and I have made sure that everything is working? What do most Linux people do? Uninstall the previous kernel or just keep it? And what do you do with the Grub loader? Delete old kernel versions lines in the config file or not? I can imagine that after many kernel upgrades the old kernel's will take a lot of harddisk space and the grub loader menu will be very long...

Happy Ubuntu owner :mrgreen: 
~Martango~

---

### Post by ovimunt on 2006-07-29
Hi,

Just leave it as it is, you might need the old kernel in the future, you never know. Plus, the kernels don't get updated all that often. 

Yet, if you really wanted you could remove the old kernel.

---

### Post by T700 on 2006-07-29
You can tell alot about people by how they handle this issue.  Personally, I keep the last three, successful, kernels.  So, if I have three listed in the bootloader and I install another, once I am convinced that it is fine (one to two weeks of use), I will uninstall the oldest, and am again left with three.

Some people like to install one, test it for an hour, and then uninstall all the rest.  All depends on your tolerance for risk.

Paul

---

### Post by Martango on 2006-07-29
Thanks!

Some good points there. I guess I will leave the Kernel's on my system for the time being. I would not know what files to remove to uninstall a kernel anyway :confused:

---

### Post by mscman on 2006-07-29
This is a question I had for a long time, mostly the part about uninstalling old versions. I try to keep the two latest kernels installed and remove the rest (i.e. the current kernel and the previous one). To remove old kernels you don't want, you need to remove the files in /boot that pertain to the kernel version you want to remove. For example, if I wanted to remove the kernel version 2.6.15-386, I would run the following command:
```
sudo rm /boot/*-2.6.15-23-386
```
Now assuming all of my kernels installed were of the 2.6.15 family, I could simply run the command:
```
sudo rm /boot/*23-386
```
and the same results would occur.

AFAIK, these kernel revisions are also removed from the GRUB menu.

Someone correct me if I'm wrong...

---

### Post by Martango on 2006-07-29
Is that all - that's almost to easy to be true ;) If it will remove the revisions in the GRUB menu as well I'm impressed! I like that strategy - to keep the two last kernels.

Thanks for your input!

---

### Post by mscman on 2006-07-29
> **Martango said:**
> Is that all - that's almost to easy to be true ;) If it will remove the revisions in the GRUB menu as well I'm impressed! I like that strategy - to keep the two last kernels.

Thanks for your input!

No problem. :D

---

### Post by infoseeker on 2006-07-29
I would prefer to use Synaptic Package Manager and do a search for> linux-image-2.6 and remove (mark for removal) the older kernels from there.

---

