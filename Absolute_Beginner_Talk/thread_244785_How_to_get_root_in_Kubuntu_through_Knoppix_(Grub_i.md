---
title: "How to get root in Kubuntu through Knoppix (Grub is broken)"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by voltronguy on 2006-08-26
OK, I moved my Linux partitions around and when I boot Grub immediately gets an error.  I'm hoping that changing menu.lst to point to the new partition will take care of it.

The problem is that I am in Knoppix right now.  I can't figure out how to get root in my Kubuntu installation so I can get write access on the menu.lst file.

Any other suggestions?

---

### Post by Schalken on 2006-08-26
try:
```
sudo mkdir /media/kubuntu
sudo mount /dev/hda1 /media/kubuntu
```

Where /dev/hda1 is your Kubuntu partition. If you don't know which is your Kubuntu partition AFAIK you can find out by typing ```
parted
``` into the Knoppix terminal.

After the partition is mounted your menu.lst should be at /media/kubuntu/boot/grub/menu.lst

---

### Post by voltronguy on 2006-08-26
OK, I'll give this a try, but I'm confused about where exactly it is making the /media/kubuntu directory? (ie in some sort of virtual directory in Knoppix or is it actually on my hardrive?)

---

### Post by Schalken on 2006-08-26
it is in some sort of virtual directory, yes.

---

