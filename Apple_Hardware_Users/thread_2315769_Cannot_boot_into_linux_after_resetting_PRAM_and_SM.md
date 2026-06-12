---
title: "Cannot boot into linux after resetting PRAM and SMC"
date: 2016-03-02
forum: Apple Hardware Users
---

### Post by vsanchez1961 on 2016-03-02
Hi,

A week ago my macbook pro began shutting down at random times while working, but only when running MacOSx and not when running Kubuntu. I suspected that maybe was a problem with the SMC and/or PRAM, so I reset those... (I still have random shutdown, though)... 

When I rebooted the machine it went directly to MacOSx, bypassing the GRUB prompt, I am using GRUB in the EFI mode so I do not user ReFIT (sp?). Ok, no problem I thought, I need to run the efibootmgr and make sure the booting order is right, I created an USB ubuntu installer, booted from it, apt-get installed efibootmgr and tried:

efibootmgr -d /dev/sda -o 0,80

However, this time that failed since there was no Boot0000 entry... only Boot0080 and BootFFFF, the normal Mac entries in the EFI partition. First that has happened to me. 

I checked the disk EFI partition and everything seemed to be right (grub directory, executable, etc) . I really do not understand how the booting process works with the modern EFI systems so looking in the network I found that maybe the problem was that some table explaining available systems got corrupted...

I found a post mentioned using a command like:

efibootmgr -c --disk /dev/sda --part 1

(my EFI partition is in /dev/sda1 so the command should look what is available there, btw  before that I tried grub-install --bootloader_id command and had not worked).

This seemed to work, I now had a Boot0000 entry which was named "Linux" and the boot order was 0000,0080 as required...

Still, no grub boot. It will go directly to MacOSx. 

So I tried reinstalling grub... (booted from the USB disk, mounted /dev/sda6 (my root partition) to /mnt and my EFI partition to /mnt/boot/efi and chrooted to /mnt and did a grub-install and a update-grub)
But still the machine boots directly to MacOSX.... 

Any ideas?? I do not understand the booting process, I am not always clear if I am messing with the USB boot or the main disk boot description.

---

### Post by vsanchez1961 on 2016-03-02
Sorry, but always posting here gives me ideas about what could have been wrong.. it turns out a had not done the grub-install, only the update-grub. After I did a grub-install another EFI system appeared Boot0001 called Ubuntu (the Boot0000 was already taken due to whaterver i did before). I had to readjust the boot order to 1,80 and finally was able to go back to Linux.

I still would like to know what happened, what resetting the PRAM and/or SMC had to do with the booting process, if that was really the cause...

---

### Post by drothlis on 2016-12-20
I successfully used [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") from a live ubuntu usb stick -- I just clicked "recommended repair" and it did the trick.

---

