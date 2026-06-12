---
title: "Odd problem with Grub"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2006-06-22
After following the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper") to change the boot order of Grub to default into Windows i've had an odd problem. When I boot into Ubuntu, shutdown and boot-up there are an extra two options in the boot menu, which are just duplicates of the Ubuntu and memory test options. I've revomed them from /boot/grub/menu.lst but they keep coming back.

---

### Post by aysiu on 2006-06-22
Go to System > Administration > Synaptic Package Manager (or Adept if you're using Kubuntu) and search for *linux-image*. Remove the old ones.

---

### Post by FireFusion on 2006-06-22
Thanks

---

