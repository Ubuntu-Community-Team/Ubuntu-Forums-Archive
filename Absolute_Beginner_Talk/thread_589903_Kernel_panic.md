---
title: "Kernel panic ?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-10-24
I just installed updates yesterday, and i have put in this fix for the slow boot: [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

But now when i boot it says:

9.187715 Kernel panic - Not syncing: Attempted to kill init..

:mad: How can i fix this ?

---

### Post by jfinkels on 2007-10-24
> **mech7 said:**
> I just installed updates yesterday, and i have put in this fix for the slow boot: [http://ubuntuforums.org/showpost.php?p=3569987&postcount=4](http://ubuntuforums.org/showpost.php?p=3569987&postcount=4)

But now when i boot it says:

9.187715 Kernel panic - Not syncing: Attempted to kill init..

:mad: How can i fix this ?
Have you tried booting from a liveCD and reversing the changes you made to /etc/usplash.cong and /boot/grub/menu.lst?

The problem most likely stems from when you ran:```
sudo update-initramfs -u -k `uname -r`
```

I don't know how, but look for a way to recreate the initramfs image for the kernel you need (maybe just make a new partition, reinstall Ubuntu, and copy it from the new installation to the old one), then replace it? I'm not sure...

---

### Post by mech7 on 2007-10-25
hmm does anybody know anymore > how i could fix this :(

---

### Post by mech7 on 2007-10-27
Is there a way i can fix the file in windows ? cause that still works.

---

### Post by musik.maniac on 2007-10-28
I get the exact error message while trying to install. System just hangs. Booted from the CD and straight away install option. Tried with 800 X 600 too, no luck. :(

AMD 1800+ processor with 384 MB of RAM. Mboard has built in nvidia graphics. Anybody who can help me?

---

