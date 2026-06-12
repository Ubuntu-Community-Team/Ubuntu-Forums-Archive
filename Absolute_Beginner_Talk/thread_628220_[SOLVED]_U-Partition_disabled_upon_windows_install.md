---
title: "[SOLVED] U-Partition disabled upon windows install"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by itix on 2007-12-01
I have problems again. I formatted  and reinstalled my windows partition today, and of course it was as windows-ish as it always is, and disabled my Ubuntu partition. Anyone knows any commands i can run from the live-CD terminal, or any graphical interface which enables it on the live-CD (prefer the last)??

---

### Post by bumanie on 2007-12-01
If you install windows after ubutnu (which includes a reinstall of windows) windows overwrites the mbr and hence also overwrites grub. It is possible to restore grub. You can do it via a live cd or via super grub disc.
If using live cd, once it has loaded off the cd, open terminal and type
sudo grub --> enter - this gets you into the grub shell. Next type
grub> find /boot/grub/stage1 --> - enter - this will give you an output (hd?,?) First ? being the hard drive number as seen by grub. The second ? is the partition number again as seen by grub. (There should also be a reference to the file system type). Next type
grub> root (hd?,?) --> enter - replacing the ?'s with the output numbers. Next type 
grub> setup (hd?) --> enter - only using the first number, ie drive number. next type
grub> quit --> enter
Get out of terminal shutdown and remove live cd. All going well, your computer should boot.

---

### Post by itix on 2007-12-01
Thanx, I know how to edit the grub ;)
It's just getting into gedit and grub that is the problem right now which you solved for me :p
Gotta write this up. No way that I'll keep this in memory. I'll try, and feedback the reults. Thanx ;)

---

### Post by itix on 2007-12-01
didn't work :/

---

