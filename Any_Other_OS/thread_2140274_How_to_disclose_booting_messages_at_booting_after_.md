---
title: "How to disclose booting messages at booting after installing Windows 8 with UEFI?"
date: 2013-04-29
forum: Any Other OS
---

### Post by grenis on 2013-04-29
Hello. I have two questions. I will expound the situation first and then ask that.

I set on AHCI, UEFI only, GPT partition and off secure boot in BIOS set up. I have installed Windows 8 at first and Linux Mint 14 mate on other partition on my new notebook, the boot loader was not installed at hda but hd7 that is mounted as /. (naturally /boot is in hd7.)

So, my partitions consist of the followings.

1,2,3 - UEFI booting partition produced by Windows 8.
4 - Winodws 8 ntfs
5 - Data fat32
6 - not allocated yet.
7 - /
8 - /home
9 - swap

After Mint was installed, Grub appeared on screen at reboot. I could boot into Mint. However, chosing Window 8 from the boot menu resulted in a blank screen. So I entered BIOS setup, I found a new start option - linuxmint in BIOS booting start option.

I booted into the Mint, executed boot-repair and rebooted again.

Grub appeared on screen again, yet another start option - grub has been added to BIOS booting option. I could boot into both Windows 8 and Mint in this time.


Question 1 : Is my install process for dual booting Windows 8 and Mint right? Is there any problem that is expected? 


I succeed in dual booting, but when it was installed only Mint on my notebook I could watch black screen for a moment at booting and met X-Windows. But now, I have watched a lot of booting message at booting.

And so I research grub configuration by grub customizer, the contents is the following.

-------------------------------------------------------------------------------------------------------------
recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_gpt
insmod ext2
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
search --no-floppy --fs-uuid --set=root --hint-BIOS=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7 b1e6a4f7-18c4-44ed-b06a-2e64b65fae11
else
search --no-floppy --fs-uuid --set=root b1e6a4f7-18c4-44ed-b06a-2e64b65fae11
fi
linux /boot/vmlinuz-3.5.0-17-generic root=UUID=b1e6a4f7-18c4-44ed-b06a-2e64b65fae11 ro
initrd /boot/initrd.img-3.5.0-17-generic     
--------------------------------------------------------------------------------------------------------------

The gfx_mode is active, so I think it is normal that booting message has to be unvisible. I don't know why booting messages appear on screen at booting.

I tried to delete 'recordfail' in upper configuration but the situation was same, change 'grub_gfxmode' in the file /etc/default/grub to 'saved' but it was same too.


Question 2 : How to disclose booting messages and enclose Mint logo at booting? Why it appears booting messages at booting?


For reference, my notebook spec is following.

cpu - intel i5-3210M 2.50Ghz
chipset - intel 7 series/C210 Series 
ram - samsung DDR3 1600mhz 4G
video - HD Graphics 4000 / Gforce GT635M
sound - HDA intel PCH
lan - Realtek RTL 8111/8168B PCI Express Gigabit
wlan/bluetooth 4.0 - Broadcom BCM43142 
hdd - HITACHI HTS54101 1TB
odd - LG HL-DT-ST DVDRAM GT50N
usb - Intel(R) USB3.0 eXtensible Host controller
card reader - Realtek_RTS5229

Thank you in advance for your kind answer..

---

