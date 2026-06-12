---
title: "[SOLVED] Question About Grub"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by czechman86 on 2008-06-08
For my laptop, I have a macbook, generation 2 and I have always had one hell of a time trying to get linux to work on it. I would have frequent crashes and thought that it was due to memory. However, osx and windows both run without a hitch, and I read recently that memtest is flawed on the macbook anyway. I didn't do much thinking about this problem til recently when I for fun read over the new wiki for 8.04. I noticed that it wants you to place grub in /dev/sda. I have been placing mine in the partition which I mark with '/'. Is it possible that a misplaced grub could wreak havoc on a macbook system? Thank you!

PS - also, I have had my memory and hardware tested out by Apple and they show that everything is in tip top condition.

---

### Post by jpkotta on 2008-06-08
You want Grub installed to whichever partition is the boot partition, which is usually the first one.  It doesn't really matter what you mount the partition as, if you mount it at all.  

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by czechman86 on 2008-06-09
thank you and that clears up that. i guess ill leave this case rest for a while and continue with my search.

---

### Post by cyberdork33 on 2008-06-09
you can install to the MBR (hda) or the the root partition. It doesn't matter. It is better to use the Ubuntu partition since Windows usually wants the MBR.

---

