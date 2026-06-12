---
title: "precise pangolin on a macbookair"
date: 2012-03-13
forum: Apple Hardware Users
---

### Post by hugow on 2012-03-13
i installed the precise pangolin beta1 amd64 on my macbookair3 and it's working fine except that blessing the boot loader doesn't seem to work any more. i can boot but it always takes 30seconds of waiting during the initial white screen. i tried blessing all 3 partitions in legacy and non-legacy mode (in non-legacy booting doesnt even work) but i still have to wait 30 seconds. the hdd is gpt formatted with:
- sda1 beeing the 1MB (no-fs?) bios_grub partition
- sda2 being ext2 /boot.
- sda3 crypt/lvm

as created by the installer when i choose "use entire disk with crypted lvm". what do i need to bless?

---

### Post by hugow on 2012-03-14
ok i figured it out. use at your own risk! here's what i did (dont do this if you dont have a backup/rescue image, seriously!):

1) install grub-efi
2) run parted /dev/sda, set boot flag for first partition (using set)
3) mkfs.msdos /dev/sda1
4) create an executable file named something like 69_apple in /etc/grub.d that mounts sda1 somewhere and copies /boot/grub/grub.efi to /<somehwere>/EFI/BOOT/BOOTX64.EFI, then unmounts it
5) run update-grub, now the BOOTX64.EFI should be on sda1
6) shutdown
7) insert apple boot stick
8) power on holding alt (i had to do this twice, first time it didnt even boot from the stick...)
9) boot into OSX installation, open a terminal and type "bless --device /dev/disk0s1 --setBoot" withouth the legacy option

done! booting is quite a bit faster than the old blessed installation using legacy booting since the EFI doesnt need to load the legacy drivers any more

---

