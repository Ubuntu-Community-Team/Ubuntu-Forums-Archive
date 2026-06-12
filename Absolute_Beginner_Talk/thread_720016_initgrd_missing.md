---
title: "initgrd missing"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by adam212 on 2008-03-09
Hello

well i recently installed kubuntu and after booting into it i was told there are 159 new updates available so i installed them but after doing that ubuntu wont load always saying "line 15 file not found" which is a grub error which cant find the initgrd.img file. I had a look at my menu.lst file which is listed below. kubuntu is installed on parition 5 so the menu.lst file is correct( i think so). i ran the live cd and had a look at /boot/grub and i think i am missing initrd.img file because all i see there is initrd.img-2.6.22-14-generic.bak (which of course is a back up) and the other one being initrd.img-2.6.22-14-generic.dpkg-bak ( which i dont know wth it is) and then i have my vmlinunz and memtest file there. I also tried to boot up live cd and mount the kubuntu partition which i successfully did (for the first time without help) but couldnt get the write permissions so at this point i am stuck here and need help. How do i get the write permissions to restore the backup file. btw all i have to do to restore the file is rename it and remove .bak, right.

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f6498daa-0b3d-734a-37e9-763c9bc57cbc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f6498daa-0b3d-734a-37e9-763c9bc57cbc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin



Sorry my english is terrible, i know.

thanks

---

### Post by adam212 on 2008-03-09
nvm i solved it. yes it was initgrd.img file missing

sudo dollphin and then replacing permission did the trick. i feel like a pro. hehe. kinda funny that update would mess it up instead of fixing errors. well happy to get it fixed. sorry to waste your time.

i couldnt edit the title so mods please be free to change the topic title to solved. TY

---

