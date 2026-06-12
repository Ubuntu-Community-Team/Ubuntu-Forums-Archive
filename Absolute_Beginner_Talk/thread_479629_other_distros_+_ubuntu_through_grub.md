---
title: "other distros + ubuntu through grub"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-20
On my pc atm i have windoze and ubuntu on it. I'm thinking of installing another distro, opensuse. Would i have to make any configuration changes to grub? 

Also, i'm thinking of using half of my linux hdd for it. Do i have to repartition everything? Or can i just repartition the ext2 parts. i have a 60gb hdd. intending to share 30gb for ubuntu and 30gb for opensuse.

A side question, does grub support bsd as well?

thanks.

---

### Post by dstew on 2007-06-20
You can add another distribution, and grub should be able to boot it. You might have to create an entry for your new distribution by editing your /boot/grub/menu.lst file though. You will need to make a new partition for your new distribution by shrinking the partitions you already have. You can use gparted for that, from an Ubuntu LiveCD boot, or use the [gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Grub can handle bsd. Look at [these recommendations]("http://www.gnu.org/software/grub/manual/grub.html#FreeBSD") for how to boot it. The recommendations are for booting  from the grub command line, but you can enter these same commands into the grub menu.lst file also.

---

