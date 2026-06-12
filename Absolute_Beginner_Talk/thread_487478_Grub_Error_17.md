---
title: "Grub Error 17"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by guyarye on 2007-06-29
I have two hard disks:
One is a SATA disk which windows XP Pro is installed on it.
And one a regular ATA drive which I'm using for linux.
I installed SuSE 10.2 and a month ago and now I installed Ubuntu 7.04 64 bit editon on the same partition I used for SuSE. I installed Ubuntu through the live cd and after the restart I get Grub error    17. What can I do??

I have Intel Pentium D, 1024 DDR2 memory and GeForce 7300GT.

---

### Post by alienexplorers on 2007-06-29
Try reloading grub.  Install your live cd and boot it.  Go into terminal and enter
> sudo grub
then enter
> find /boot/grub/stage1
root (hd#,#)
setup (hd#)
quit grub
reboot

---

### Post by guyarye on 2007-06-29
I followed your steps through the live cd and when I restarted my computer I had Grub Error 17 again.
Help?

---

