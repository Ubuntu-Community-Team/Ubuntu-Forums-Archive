---
title: "Booting Ubuntu on a Bios limited computer!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Idoc on 2008-02-17
I have a toshiba libretto 110 ct running windows xp, I installed ubuntu using netbootin utility after the install I can boot xp from grub but not ubuntu 7.10 .  Afer much reasearch I think I found the problem. At first I had the root beyond the 1024 cyl limit, that did not work!! repartitioned manually and put all prior to the 1024 limit.  I have to say I would have prefered to make a /boot partition to load then put everything else beyond 1024 cyl but there is no clear documentation to do that, maybe in the future an option can be added to have the installer do that if your bios can not boot large hds! anyhow after the install I got up to Please wait, I waited..... then was droped to the shell, the bootloader can not find the drive to contiue, I was able to boot with the following commands
modprobe ide-disk; modprobe ide-generic; cat /sys/block/hda/dev (to check major an minor numbers of hda whic was 3:0) then mknod /dev/hda1  b 3 1 followed by ctrl-d keypress. The system boots normally from there!  How do I fix this or automate this process??? It is a pain to type that every time I want to boot. 
** i think this has somthing to do with udev and the new sata driver now being used for ide, becase before I found the above code if i changed the boot options in grub from sda to hda it booted somewhat but never got to please wait. 
?? also is there a bootloader like nuni that doesnt use the bios to boot but works on partitons other than ext2??(not loadlin!)

---

