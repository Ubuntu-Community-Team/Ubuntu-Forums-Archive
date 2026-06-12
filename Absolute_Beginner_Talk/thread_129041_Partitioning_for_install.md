---
title: "Partitioning for install"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by tweetybird on 2006-02-12
Ok, a real noob question here.  Am about to install Ubuntu.  Have not tried any Linux flavor in about 6 years now.  Have XP on sda.  Intend to change boot order in bios to sdb as first boot device and then install Ubuntu to sdb to leave my XP disk totally unaffected.  Will this work?


Also, am planning to set up a 10GB /, 2 GB swap, and a 20 GB /home.  Assume this is plenty - will the partition utility allow me to set up in this way and will it know what each of the partitions is for?

Thanks

---

### Post by aysiu on 2006-02-12
You don't need to set a boot order in the BIOS (unless you're setting it to boot from CD, but that doesn't sound like what you're talking about). Just install Grub to the MBR.

See the fifth link of my signature for details... lots of details.

---

### Post by tweetybird on 2006-02-12
Thanks for the response, and the link, was afraid I was about to mess up, becuase I hadn't seen anything that told me where it was I needed to go the set the swap file.

---

### Post by kont.raen on 2006-02-13
[QUOTE=tweetybird]
Also, am planning to set up a 10GB /, 2 GB swap, and a 20 GB /home.  Assume this is plenty - will the partition utility allow me to set up in this way and will it know what each of the partitions is for?

Thanks[/QUOTE]

Hi tweetybird,

The size of the partitions - as you have mentioned them - will surely do, but maybe you should downsize the swap to 1 GB, unless you are planning to set up a server :)

Honestly, in all my time using different flavours of Linux for my home and office desktop environments, I never endend up using more than 100 MB of swap (on machines with 512 MB or more of RAM) - and even that has been on really rare occasions.

---

### Post by lha on 2006-02-13
[QUOTE=kont.raen]Hi tweetybird,

The size of the partitions - as you have mentioned them - will surely do, but maybe you should downsize the swap to 1 GB, unless you are planning to set up a server :)

Honestly, in all my time using different flavours of Linux for my home and office desktop environments, I never endend up using more than 100 MB of swap (on machines with 512 MB or more of RAM) - and even that has been on really rare occasions.[/QUOTE]

Second to that. 2 GB is a lot of swap, even a quarter of it is usually sufficient. 1GB is a more rational choice. If you want, you can make big swap partition but 2 GB is still quite a lot... (And a word on root partition; Mine is 5 GB and it is more than enough for me.)

Your plan sounds good. As long as you remember to tell the installer to install grub to Ubuntu's drive, your XP drive should stay intact. Sometimes grub guesses hard drives' mappings incorrectly and is therefore unable to boot your computer. It isn't dangerous or hard to fix if it happens, but it does require you to reinstall grub and tell it how to correctly map drives.

Your installation can be easier if you make Windows drive hdb and the drive you are planning to install Ubuntu into hda. No need to fool around with bios and grub will be set up correctly from the beginning.

---

### Post by tweetybird on 2006-02-13
Had system setup with XP installed on sda and written to MBR on sda with this drive booting in first position in the bios.

On initial boot after installing Ubunto to sdb, system booted right up into XP like nothing had happened.

If not for noticing one screen that flashed by during the partitioning process, seemed to remember it saying something about hdb.  So back into the bios and moved hdb to first boot position and sure enough there was the bootloader.  

So as it stands now, I have what I was looking for, a totally unaffected drive for XP.  All I have to do is change the boot order back to sda and my system won't even ackowledge that Linux has been installed.

---

