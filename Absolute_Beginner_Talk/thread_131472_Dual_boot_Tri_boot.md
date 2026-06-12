---
title: "Dual boot Tri boot"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-16
You know I have always herd About people doing Dualboots and so on. How would you set up a 3rd or even a 4th operating system into Grub? 

See I want to Keep Ubuntu and Windows because I know how to use both but still want to play with other distrobutions... Should I try this or not?

---

### Post by RaptorRaider on 2006-02-16
Sure.
Just add other distributions to /boot/grub/menu.lst in the same way Ubuntu was once added.

---

### Post by aysiu on 2006-02-16
1. Back up all your important data (in case you screw up accidentally)
2. Create a new partition somewhere.
3. Install the new distro to that partition.
4. Since this new distro is something you're just playing with (and could, presumably, be replaced by yet another distro to play with), keep Ubuntu's Grub on the MBR and install the new distro's Grub to that new partition.
5. In Ubuntu, mount the new distro's partition and copy the Grub entry from that new distro's /boot/grub/menu.lst file to Ubuntu's /boot/grub/menu.lst file.

---

