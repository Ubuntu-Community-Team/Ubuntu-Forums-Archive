---
title: "How to find out what the hard drive association is"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by dhongyt on 2007-09-07
Recently I installed Window's Vista and that whipped out the previous grub install, so now I'm trying to reinstall Linux to boot with Window's Vista, but it doesn't seem like it is working. I think its because I recently installed 2 ide drives in the computer with my sata drive, so the hd0 isn't my sata drive anymore. How do I find out what my sata drive is being associated with? My sata drive is where I want to put it, it has 5 partitions in there, 1st Window's Vista and probably were the grub install is supposed to be. 2nd is the linux os. 3rd is the swap. 4th and 5th is storage.

How do I make it so it installs the grub install to my sata drive in the vista partition?

---

### Post by parvinder on 2007-09-07
Remove the new drives that you added to ensure that the hda0 will be the same where linux was installed and then run the installation disk. Hopefully, it should detect the previous installation and will repair it.

---

