---
title: "Can only boot into mac after installing Linux - over High Sierra, Win 7, and Lion"
date: 2020-02-11
forum: Apple Hardware Users
---

### Post by kernel-boy01 on 2020-02-11
It appears my bootloaders are all out of wack.

 I installed win 7 from High Sierra (on a Mac mini 2011 with Radeon graphics chip) using boot camp, then created a mac partition and installed lion onto that third partition for my old apps. I then created a fourth partition, MS-DOS for installing Kubuntu. 

Created a USD installation for Linux by using etcher, rebooted while holding down the option key and selected the EFI "drive" on the right. (There were two... for some reason. I installed into the partition I created and left the location of the bootloader at the suggested, the first partition, High Sierra, same area refind was installed in after.

Then I installed refind using the script included in the folder. Now, I get an error message when trying to boot from holding command, and refind menu has extra icons and looks messed up.

The first icon is Ubuntu, then there is a fallback icon, then a windows icon that says "boot macos from legacy", then FOUR mac icons that say "boot macos from preboot" then one mac icon saying "boot macos from (my high Sierra drive label), then a windows icon saying "boot legacy is from FAT volume" which makes a screen saying "Missing operating system". After that, there is ANOTHER windows icon which says "boot legacy OS from NTFS volume".  -This one works.

Should I remove refind and install supergrub 2? Am so confused. 

[IMG]https://www.facebook.com/photo.php?fbid=2495333990576591&set=pcb.2495335583909765[/IMG]

[IMG]facebook.com/photo.php?fbid=2495333990576591&set=pcb.2495335583909765[/IMG]

[IMG]facebook.com/photo.php?fbid=2495335213909802&set=pcb.2495335583909765[/IMG]

---

### Post by howefield on 2020-02-11
Moved to "*Apple Hardware Users*".

---

### Post by kernel-boy01 on 2020-02-11
I can boot into all OSes, just the refind menu is messed up and the Kubuntu grub menu only shows linux, mac 32 bit and mac 64 bit.

---

