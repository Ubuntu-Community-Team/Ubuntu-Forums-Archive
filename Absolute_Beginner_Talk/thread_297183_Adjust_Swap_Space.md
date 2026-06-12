---
title: "Adjust Swap Space"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-11-10
How do I adjust the swap space I have for my computer? Thanks!

---

### Post by Imsati on 2006-11-10
Was holding off on a reply since I'm not 100% sure you can adjust the Swap, but after an hour of no responses, I thought I'd at least point you (maybe) in the right direction.

Install gparted (partition program--look in Repo's) and follow the instructions. Very easy to change normal partition sizes, but as I said, not sure of a Swap.

~Jay

---

### Post by bulldog on 2006-11-10
I recommend the gparted live cd which you can get here,
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

It's about 25MB and you should burn it on a cd-rom and boot from it.

Your swap file is a small partition and can be changed.
The question is,what are you going to do,make it bigger or smaller.

When you want more swap space you have to free up space from another partition.

---

### Post by bruenig on 2006-11-10
If you are just going to resize the swap, you can do that in ubuntu, sudo apt-get install gparted and then unmount it with gparted and resize it, but you will more than likely want to incorporate some of that space into your other partitions. If that is the case you will need to use a live cd. If you aren't sure, just go with the live cd, it will work definitely.

The gparted live cd will work or the ubuntu live cd.

Just boot into one of those, if you choose the gparted, the partition editor will open automatically, ubuntu you will have to go to system>administration>Gnome Partition Editor.

Use the nice graphical editor to resize and such how you want.

When you apply changes and boot back into ubuntu, you may have to change your /etc/fstab as I did when I resized my swap.

---

### Post by CatKiller on 2006-11-10
If you are **just** changing the swap, you can do so in your normal environment with the GParted you can install from the repositories. You'll need to do a ```
sudo swapoff -a
``` to unmount the swap partition. You'll also need to unmount any other partitions you intend to modify. However, you can't unmount your **/** partition, for reasons that should be obvious. If you intend to change that, then you'll need to use the [GParted live cd]("http://gparted.sourceforge.net/livecd.php").

---

