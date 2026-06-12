---
title: "Grub not working"
date: 2009-04-10
forum: Apple Hardware Users
---

### Post by sighk on 2009-04-10
OK, I mac a macbook from early 2006. inetl core duo 2, I had ubuntu 8.04t installed on it, it worked just fine. Grub loaded. I should mention I completely removed OSX. I erased everything and updated to 9.04. Everything was working nice for a few days. Then I turned it on and it shows a missing folder Icon. So I booted the cd

mount --bind /proc /media/sda1/proc
mount --bind /dev /media/sda1/dev
chroot /media/sda1/
update-grub sda

It says it is worked, I looked over all the files in /boot/grub and they seem to be correct

I reboot

Missing folder Icon.

Next In anger I put in a windows installation disk and it says Press any key to boot from CD....... I let this expire because I really don't want to do that. After that it boots ubuntu with grub.

So I thought mabey when i ran update-grub, it was putting info into an already corrupt grub.

So I fired up the windows instalation disk into repair mode, wiped the mbr and rebooted.

It now shows the hard drive when I hold option on boot, of course it won't work because it's a win boot loader.

Now I put the ubuntu cd in, run update-grub again

reboot

no bootable drives found, just a flashing "?" inside a folder, again I stick the winxp cd in and wait for time to expire, it boots from grub. Can anybody explain this or help me to fix it? Why would the bios be unable to find a boot loader on the hdd, but winxp after not pressing anything from cd will boot it? Did they change grub, Do I need some sort of patch for macbook now, when I haven't in the past?

---

### Post by cyberdork33 on 2009-04-10
> **sighk said:**
> OK, I mac a macbook from early 2006. inetl core duo 2, I had ubuntu 8.04t installed on it, it worked just fine. Grub loaded. I should mention I completely removed OSX. I erased everything and updated to 9.04. Everything was working nice for a few days. Then I turned it on and it shows a missing folder Icon. So I booted the cd

mount --bind /proc /media/sda1/proc
mount --bind /dev /media/sda1/dev
chroot /media/sda1/
update-grub sda

It says it is worked, I looked over all the files in /boot/grub and they seem to be correct

I reboot

Missing folder Icon.

Next In anger I put in a windows installation disk and it says Press any key to boot from CD....... I let this expire because I really don't want to do that. After that it boots ubuntu with grub.

So I thought mabey when i ran update-grub, it was putting info into an already corrupt grub.

So I fired up the windows instalation disk into repair mode, wiped the mbr and rebooted.

It now shows the hard drive when I hold option on boot, of course it won't work because it's a win boot loader.

Now I put the ubuntu cd in, run update-grub again

reboot

no bootable drives found, just a flashing "?" inside a folder, again I stick the winxp cd in and wait for time to expire, it boots from grub. Can anybody explain this or help me to fix it? Why would the bios be unable to find a boot loader on the hdd, but winxp after not pressing anything from cd will boot it? Did they change grub, Do I need some sort of patch for macbook now, when I haven't in the past?

use gptsync to sync your partition tables.

---

