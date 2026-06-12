---
title: "Changing the &quot;start up&quot; menu when pressing ESC"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by useResa on 2006-10-29
I am still quite new to the world of Linux/Ubuntu.
I have recently done an upgrade to Edgy and am faced with the following:

When my PC starts and I press ESC so I get the start up menu.
I have the possibilities of choosing:
the 2.6.17-10-386 kernel and this one in recovery mode,
the 2.6.17-10-generic kernel and this one in recovery mode
and a list of "old" kernels from the dapper installation.

The thing I would like is that I would like the generic kernel to be the default one, but since it is not located at the top of the list, I have to press ESC all the time to choose this one.

My question: How can I modify this list and move the generic kernel to the top and while I am at it, also remove the old dapper entries from this list.

Hope that my question is clear enough to understand.
Any help is really appreciated

---

### Post by catlett on 2006-10-29
```
sudo gedit /boot/grub/menu.lst
``` That is the list that appears when you press esc.
Copy/paste the generic entry to the top of the list. You can delete the other entries form the list but they will still be in the system. It is better to remove them through Synaptic Package Manager.
You should always keep an older kernel that you know works. Sometrimes a new kernel does not work as well as the old kernel (may be a bug or some other reason. it doesn't happen often) If you erase all the old kernels, you are stuck with a kernel that doesn't work well. If you keep one that works good, you can always boot to that until another new kernel comes along. You are basically keeping a "backup" kernel/

---

### Post by CatKiller on 2006-10-29
You can remove the old kernels from the list by uninstalling the old kernels with Synaptic. You could probably uninstall the -386 kernel as well, but don't do so if it would take your -generic kernel with it (for obvious reasons).

You can edit the boot-up menu list by editing /boot/grub/menu.lst - there are many posts about this file and the ways you can mess it up. So you'll probably want to make a backup first.

---

### Post by Chinkostu on 2006-10-29
would that involve making new partitions for each kernel version then? i suppose i could put 6.06 on one and 6.10 on the other, and continue to use Dapper until theres support for my (cruddy) hardware in Edgy.

---

### Post by useResa on 2006-10-29
> **catlett said:**
> ```
sudo gedit /boot/grub/menu.lst
``` That is the list that appears when you press esc.
Copy/paste the generic entry to the top of the list. You can delete the other entries form the list but they will still be in the system. It is better to remove them through Synaptic Package Manager.
You should always keep an older kernel that you know works. Sometrimes a new kernel does not work as well as the old kernel (may be a bug or some other reason. it doesn't happen often) If you erase all the old kernels, you are stuck with a kernel that doesn't work well. If you keep one that works good, you can always boot to that until another new kernel comes along. You are basically keeping a "backup" kernel/

Thank you for your quick reply. It did the trick.
Regarding removing old kernels, I am (still) a bit afraid that I may run into problems therefor left them in the list for now.
Very pleased with the fact that the generic kernel is now selected as a standard, since the 386 only used one of the two processors and now both are used again.

---

