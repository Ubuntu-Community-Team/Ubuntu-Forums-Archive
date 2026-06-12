---
title: "Linux Distros"
date: 2013-02-13
forum: Any Other OS
---

### Post by technologicme on 2013-02-13
Can i install 2 linux distribution on my pc runing xp with 768MB of ram  i all ready have zorin os 6 on C drive can i also install linux lite

---

### Post by JiuJitsu500 on 2013-02-13
Certainly. Just make sure you have one swap partition set that both distro's use.

XP should have two partitions, one for system reserved stuff, and one primary. Linux likes swap space, especially with low RAM. you should already have zorin using one swap partition.

Install the other one, but create a smaller sub-partition to install it to, but make sure it's using the same swap space as zorin. That way, no matter what you boot up, either one uses the same swap. Just kind of saves memory and space.

You can only have 4 primary partitions though, so create a primary sub-partition for the new OS and you should be fine. GRUB will recognize all three os's so long as you install GRUB to the DEVICE, not to any partition. Like, /dev/sda rather than /dev/sda2

---

### Post by oldos2er on 2013-02-13
Moved to Other OS/Distro Talk.

---

