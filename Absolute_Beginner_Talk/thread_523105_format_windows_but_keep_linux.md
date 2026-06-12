---
title: "format windows but keep linux"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by JesterGr on 2007-08-11
Hey everyone!

I have 2 drives. On the first one (the primary/boot drive) i have my windows installation. On the second i have my Ubuntu distro. I want to format the boot drive and at the same time keep the second untouched. It doesn't seem to be a problem, but i have some thoughts that could lead to problems :

a) the grub is installed on the boot disk? if i format it, there will be no grub anymore, and the windows bootloader will take its place? so i will have no access to Ubuntu?

b) if the above doesn't pose a problem (suppose it solved or non-existent) ubuntu will find the new windows installation ? (i had read that it is recommended to install linux after windows. this means that there will be trouble otherwise?)

Any other problems that may pop ? 

Thnx in advance :)

---

### Post by gn2 on 2007-08-11
AFAIK you can format the Windows partitions without harming Grub which is written on the MBR which is outwith the partitions.

Grub can be re-installed from a terminal command from a booted Live CD.

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

Also see the Hermanzone link in my sig for lots of relevant info.

---

