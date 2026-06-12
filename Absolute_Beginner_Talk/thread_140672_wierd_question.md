---
title: "wierd question"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by obey43 on 2006-03-06
so i installed ubuntu on a partition (hda2).

windows was left on hda1.
i corrupted windows, and then was unable to boot into linux after that, so i install ubuntu on hda1

and now with grub i can get into hda2 which is the one i want 

is there anyway to remove hda1 linux without loving grub, as well as combining the soon to be empty hda1 into hda2 so i can use the entire harddrive with linux again?

sorry if that was really confusing

---

### Post by TrendyDark on 2006-03-06
Okay, simple fix to a confusing problem. lol

Leave the Ubuntu Installation you have on hda1 alone, boot into that one. Using synaptic or apt-get (apt-get is easier) get a program called Gparted.

```
sudo apt-get install gparted #This will work in the terminal
```

Now open up Gparted from the System Tools menu. View the hda2 drive and make sure it's unmounted. Then just delete the partitions on that drive, until it's a clean drive. Now make a new partition (FAT32 if you plan to reinstall windows or EXT3 if you're just going to use Linux).

Apply the changes and there you have it, you should be able to use that drive by mounting it somewhere like your home folder or such.

If you accidentally remove GRUB. Just insert the install CD, but when you get to the "press enter to start installation" screen, type "rescue", then hit enter.

Once you've followed all those screens, you should get a command line. just type:

```
grub-install /dev/hda1/
```

to reinstall GRUB on your first drive.

---

