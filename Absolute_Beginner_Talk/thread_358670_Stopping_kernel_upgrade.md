---
title: "Stopping kernel upgrade"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Nevermore on 2007-02-11
i saw there is a new version of kernel, since i've many things compiled with the old one, i do not want to upgrade to the new kernel, how can i stop the upgrade? i tried to put on hold the files but seems i can't put on hold kernel on synaptic..
what can i do?
Thanks

---

### Post by bulldog on 2007-02-11
You can just update the kernel without any problem.
You only have to boot your current kernel to use your creations.

Otherwise you can use synaptic and lock your current version to avoid updates.

---

### Post by Nevermore on 2007-02-11
bulldog i tried to lock it, but seems synaptic doesnt let me do.when i click on lock the package list disappear and i've to look for the packages again, then when update manager wakes up, it still tried to upgrade the kernel..
what am i doing wrong?

---

### Post by kilou on 2007-02-11
What happens if you compile and use a Vanilla kernel instead of the Ubuntu one?? Will synaptics also try to update the Vanilla kernel and create a mess? If not, using a Vanilla kernel could be a nice solution, and you'll also have a newer kernel version than the Edgy ones.

---

### Post by Nevermore on 2007-02-11
actually i want to avoid using a new kernel because i have many module and drivers compiled by me and i don't want to recompile them all, also because i forgot the configurations..
so i dont want a new kernel, i want to keep my old one..
is a pity if i cant block the kernel upgrades, i wont be able to upgrade anymore.

---

### Post by bulldog on 2007-02-11
> **Nevermore said:**
> bulldog i tried to lock it, but seems synaptic doesnt let me do.when i click on lock the package list disappear and i've to look for the packages again, then when update manager wakes up, it still tried to upgrade the kernel..
what am i doing wrong?

Did synaptic ask you for the root password?
I tried it and it works without any error,so you probably did something wrong,there should be a little lock in the package you have locked.
The update manager isn't aware of this change you made,try to log out and in again,and if this isn't sufficient,well try a reboot.
Now the update manager should know and if not [and your version is locked with the little lock-figure] try to update and see what happens.

FYI you don't have to use the new kernel,you can just stick by the one you use now.
Just boot the kernel you have now and don't use the new one,it doesn't harm anyone if you do so.

---

### Post by Nevermore on 2007-02-11
yes synaptic asked for my password, but i don't see any lock on the files
i removed the metapackages and tried this way..

---

### Post by bulldog on 2007-02-11
> **Nevermore said:**
> yes synaptic asked for my password, but i don't see any lock on the files
i removed the metapackages and tried this way..

The little lock appears in the green box in front of the installed package.

---

### Post by Nevermore on 2007-02-11
unfortunately i can't lock any linux headers or kernel files
i can lock others, but not those ones
btw i started synaptic even via shell by gksudo synaptic
but is the same
the only metapackage i can't remove is linux-restricted-modules-common
so i have to upgrade them anyway..
since i cant lock

---

### Post by bulldog on 2007-02-11
Just upgrade then and don't use it.
The upgrade doesn't change your current config,so it can't harm it in anyway.

---

### Post by mikewhatever on 2007-02-11
> **bulldog said:**
> Just upgrade then and don't use it.
The upgrade doesn't change your current config,so it can't harm it in anyway.

If the kernel is updated and not used as you suggest, would there be security updates for both kernels, or is it unrelated? If yes, is there a way to prevent the security updates for the newer kernel?

---

