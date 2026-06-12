---
title: "swap file"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by algree on 2006-01-14
newbeeee two questions
  1 - how do yiu make the swap file bigger 
  2 - would it make the progs run faster

---

### Post by por on 2006-01-14
To begin with the last question, no, a larger amount of swap space does not make the system faster, but allows it to provide more virtual memory to the applications running at the cost of swapping memory pages to and from the swap area on disk, which is a relatively slow process.

In answer to the first question: Linux does not use a swap file, but swap partitions. Normally one is set up during installation. 
If you really need more swap space and aren't afraid to dug into a bit of commandline stuff then the following hints may be helpfull.
One can make other partitions usable as swap space with the mkswap command. (mkswap replaces any existing filesystem on a partition, so beware!) Normally the swap partitions are added to the kernel at boot time: all partitions marked as swap in the file /etc/fstab are added. With the commands swapon and swapoff swap partitions can be added and removed from the kernel at runtime. Best consult the manpages for these commands before using them, e.g. by running 'man mkswap' from a shell prompt.
Good luck.

---

### Post by algree on 2006-01-14
Thanks it sound hard i'll be better off thinking it over hard befor tring

Thanks again

---

### Post by Sef on 2006-01-17
In general, a swap partition should be double the amount of memory.  However, if you have 1 gigabyte or more of memory, you do not need to double your swap, unless you are doing heavy duty movie editing or other things that would use a lot of RAM.

---

