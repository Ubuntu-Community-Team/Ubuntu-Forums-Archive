---
title: "How to install 9.10 on a macbook 5.1"
date: 2009-09-30
forum: Apple Hardware Users
---

### Post by amortvigil on 2009-09-30
i installed ubuntu karmic on aluminim macbook (pro) 5.1
its dualboot with windows and works wit refit and grub-pc.
installs without problem but wouldnt boot. I found a fix,
But i am not a guru so the steps i toke may be double or not realy needed.
I just tell what i did. 

In short copied my /boot into my efi partition an created a grub.efi.

Got it from :
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=538730](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=538730)

I used super grub to boot when i wasnt able
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
-> burn iso on cd-rom, startup while pressing c until i hear your cdplayer roar.



- install osx and refit. if this is done
- boot your karmic live cd/dvd and create your partions in gparted.
	* i left 150mb between all partitions *
- install ubuntu and boot with super grub disk.
- install all updates and make wifi an videocard working.
- reboot with supergrub disk and then the tricky part.

1) mount EFI partition 
 
 # mount /dev/sda1 /efi

2) copy all kernels and such
 
 # cp -a /boot /mnt/boot-fresh
 
3) create a grub dir
 
 # mkdir /mnt/efi/grub

4) head to /mnt/boot-fresh

 # cd /mnt/boot-fresh

5) make grub image

 # ./grub-mkimage -d . -o grub.efi part_gpt hfsplus fat ext2 normal sh chain boot configfile

6) copy all data to /mnt/efi/grub

 # cp grub.efi *.mod *.lst *.cfg /mnt/efi/grub
OR
 # cp -A /mnt/boot/grub /mnt/efi/

7) make realy sure you have the needed files

 # cd /usr/lib/grub/x86_64-efi ; cp *.mod fs.lst command.lst /mnt/efi/grub

8 ) Copy the grub.efi in the root folder of your efi partition

 # cp /mnt/efi/grub/grub.efi /mnt/grub.efi

9) and then  finaly update-grub2

 # update-grub2

10)

 # sudo reboot

it worked now


Blessings from Evan sorry for my english. if you encounter better ways to do it ill edit.

---

