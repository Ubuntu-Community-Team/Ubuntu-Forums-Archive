---
title: "How to put the /boot partition on a flash drive"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2008-04-12
I have my whole disk encrypted in ubuntu,well the weakest link is the /boot partition cause it is not encrypted is there a way I could put the /boot partition on a flash drive so that way unless you have the flash drive you can't boot the computer?

---

### Post by R6V2 on 2008-04-12
As far as I know, No. (Correct me if im wrong anyone) Because, when the computer loads, it doesn't load off the flash drive, it reads from the HDD. Having a USB drive when the computer boots means nothing, and if you use the 'BOOT FROM USB' then, it will just try to boot, but what's their to boot when it's not connected?

---

### Post by Gulyan on 2008-04-12
you can try to install the whole ubuntu (not just the /boot)  on an usb stick

---

### Post by duncan.hawthorne on 2008-04-12
to R6V2
you can have the MBR on the harddrive, and have then look where you want for the linux kernel


to jonward690
you just need to know how to mount your flash drive into /boot
i did this with an internal partition with the line in /etc/fstab of
# /dev/sda4
UUID=a66cb15d-f3aa-467b-80bd-d73b9bb3a9ad /boot           ext3    defaults        0       0

perhaps something similar would be useful. sorry i cant help more

you can also doing mounting generally using the mount command, something like
mount /dev/sda4 /boot
but i think this would happen too late to be useful, you need fstab entry

---

### Post by jonward690 on 2008-04-12
hmm well then is there a way to make a usb key to boot my computer so I wouldn't have to enter a huge password everytime I wanted to turn the computer on.

---

