---
title: "XP/Vista Dual Boot Machine turning into a Triple w/ Ubuntu problems"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by djxstream on 2007-06-14
my scenario.

ive been dual booting vista/xp (installed on separate drives) using EasyBCD for a while now, and using ubuntu either live CD or virtual machine.  EasyBCD is installed in XP and the XP drive is set to boot in bios, it loads up the option to pick vista or xp and both work as expected.

So i installed Ubuntu on a 3rd HD, and now set that to boot so i load into grub.  added an entry to grub to get to the XP drive (which has the easy bcd) andi  would be able to pick XP or Vista in the EasyBCD menu. And that works to an extent.

1) i pick ubuntu in grub, ubuntu loads
2) i pick windows in grub, easybcd loads
2.1) after getting to easybcd, i pick vista it loads
2.2) after getting to easybcd, i pick xp.....it reboots

ifi  changed my bios back to boot my XP drive and both XP/Vista work, but I can't get Ubuntu to boot thru easybcd.

So any ideas to get this triple boot working w/o the need to change bios boot order?

---

### Post by rickycodie on 2007-06-14
add an entry into the grub boot menu. using this thread

[http://ubuntuforums.org/showthread.php?t=460068](http://ubuntuforums.org/showthread.php?t=460068)

then from grub you can boot into all.

---

### Post by djxstream on 2007-06-14
if i add an entry to the xp drive, i get the easy bcd menu which doesnt let me boot xp

i could add an entry for the vista drive...but that wont help the issue and i already can get into vista.

---

### Post by rickycodie on 2007-06-15
add the entry to the ubuntu drive/partition, and go from there

---

