---
title: "[SOLVED] A little help with some loading issues"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by toolfreakuna on 2007-09-05
Hey all. I have recently been trying to set up a dual boot with Windows XP and Ubuntu 7.04. I got Windows XP completely installed, updated, and defragmented afterwards. (This is on a SATA 500 GB hard disk, by the way)

Anyhow. Windows was working perfectly (hah, funny). I installed Linux, and when installing, I selected to automatically partition the disk in half. It installed fine, or so it seemed. Then, when rebooting I got "Error loading operating system". So, after tinkering with GRUB as specified elsewhere on these forums, I got it to boot up to the GRUB menu. However, whenever selecting an OS to load, it gives Error 22: No such partition. 

So, I choose to edit from GRUB and the first line usually says something like

```
root (hd2,1)
```

which, according to find in the GRUB terminal, is where it is located. However, if I change it there to look like 

```
root (hd0,1)
```

then the OS boots as it should. I still cannot get Windows to load at all. And, I don't want to have to edit the boot listing each time I turn on my PC. Any help would be wonderful.

---

### Post by SOULRiDER on 2007-09-05
Edit the grub config:
```
gksu gedit /boot/grub/menu.lst
``` you canc hange all boot options there and the changes will be permanent.

---

### Post by NeuralEskimo on 2007-09-05
I have been  running 100% Kubuntu for quite a while, so my memory about dual booting is a little fuzzy but I believe you need to add an entry to your menu.lst file which goes something like this:

```

title         Crappy OS (AKA Windows)
root          (hd0,0)
makeactive
chainloader   +1

```

You can make the title say anything you want, but I like the one above. ;) Also, you may need to tweak the root, line, but given your description, I think (hd0,0) will work for you. 

Hope this helps...

---

### Post by toolfreakuna on 2007-09-05
Awesome, got it working. Thanks so much for the quick replies and advice!

---

