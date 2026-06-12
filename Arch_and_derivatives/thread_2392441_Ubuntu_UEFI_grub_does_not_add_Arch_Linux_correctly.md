---
title: "Ubuntu UEFI grub does not add Arch Linux correctly"
date: 2018-05-21
forum: Arch and derivatives
---

### Post by Cavsfan on 2018-05-21
If you have Arch Linux installed in UEFI/GPT mode on SSD, when you add any version of Ubuntu in UEFI/GPT mode, it does not create the correct **initrd** boot line correctly for Arch leaving just the ability to boot into the fallback kernel.
Ubuntu Grub adds this:
```
initrd    /intel-ucode.img
```

However with the Grub on Arch Linux, it creates the correct **initrd** boot line:
```
initrd    /intel-ucode.img /initramfs-linux.img
```

I create a bug on Ubuntu grub to hopefully get this fixed. If you have this problem add your name.

[https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314](https://bugs.launchpad.net/ubuntu/+source/vm-builder/+bug/1772314)

---

### Post by Cavsfan on 2018-06-08
Not many people using Ubuntu along with Arch?

---

### Post by Cavsfan on 2018-10-17
FWIW, this bug was fixed in openSUSE last week.

---

### Post by JonPaul on 2018-10-18
same problem with antergos..

---

### Post by Cavsfan on 2018-11-12
> **JonPaul said:**
> same problem with antergos..

Same problem in every Linux system there is, I'm pretty sure.
I've installed openSUSE Tumbleweed, Fedora 28, CentOS, Sabayon Linux and all Debian based systems, possibly a few others have this same problem.

They do not take into account the possibility that the *[COLOR=#666666]initrd[/COLOR]* could have 2 .img entries.

openSUSE is the only one I'm aware of that has fixed this.

---

### Post by 23dornot23d on 2018-11-12
Its almost every linux system that seems not to want to include arch or manjaro .......

In the past I have just kept manjaro as the first bootloader ..... but as you say ...... by now it should have been included.

Maybe we all just get used to our own workarounds ...... but it would be helpful to get it fixed properly if anyone can do that please.

---

### Post by Cavsfan on 2018-11-13
> **JonPaul said:**
> same problem with antergos..

I got to thinking later, Antergos is based on Arch so, that's crazy.

> **23dornot23d said:**
> Its almost every linux system that seems not to want to include arch or manjaro .......

In the past I have just kept manjaro as the first bootloader ..... but as you say ...... by now it should have been included.

Maybe we all just get used to our own workarounds ...... but it would be helpful to get it fixed properly if anyone can do that please.

I opened up the bug on Ubuntu and it isn't going any where. I opened the same bug on openSUSE and Michael Chang, the developer worked with me to fix it and so that is one down.

My workaround is to make a custom grub on every system I install because unlike the Legacy/MBR partitioning, with UEFI you cannot keep your grub on any one system.
If a system updates it's grub, it also installs it there and I hate typing in "/initramfs-linux.img" on the Arch menuentry. Also, surprisingly most of the other menuentries are wrong on other distros.

I've learned a lot like how to customize each grub on each system I have - Ubuntu, Arch Linux, openSUSE, Fedora and CentOS.
But, I dropped CentOS when I found that it isn't good for a desktop OS more for a server. The conky version was 1.9 I'm pretty sure.

I installed Xubuntu 18.04 this morning and my custom entries would be this (using UUIDs):
```
cavsfan@cavsfan-xubuntu:~$ sudo blkid | grep sdc
[sudo] password for cavsfan: 
/dev/sdc1: UUID="[COLOR=#ff0000]688D-126B[/COLOR]" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"
/dev/sdc3: LABEL="C:" UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="[COLOR=#008000]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR]" TYPE="swap" PARTLABEL="swap" PARTUUID="c39d976b-91cd-4d59-a270-91398b764d3f"
/dev/sdc5: LABEL="ArchLinux" UUID="[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc6: LABEL="Media" UUID="840ac879-510a-4b8d-be01-9d3a5f37dbb2" TYPE="ext4" PARTLABEL="Media" PARTUUID="61e2e7f9-1a98-44f7-881e-ae85fceaf994"
/dev/sdc7: LABEL="openSUSE" UUID="[COLOR=#0000ff]06d2aa5d-5c70-4916-9f8f-219f93668d52[/COLOR]" TYPE="ext4" PARTLABEL="openSUSE" PARTUUID="6c7b8cd9-4350-4600-8e9e-ff1eb2933c9f"
/dev/sdc8: LABEL="Fedora" UUID="[COLOR=#0000ff]56ffa54a-e3c5-4b5d-9a21-fc14f662f7bb[/COLOR]" TYPE="ext4" PARTLABEL="Fedora" PARTUUID="887a3d2f-73ed-4894-b566-3e37294757e7"
/dev/sdc9: UUID="[COLOR=#0000ff]27fb4082-7bd3-4974-9fa5-d2b43886513b[/COLOR]" TYPE="ext4" PARTUUID="2edba524-105d-40b4-9242-530ca362a32a"

```
/etc/grub.d/06_custom:
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Fedora 28 (Workstation), openSUSE Tumbleweed, Xubuntu 18.04 and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]' {
     load_video
     set gfxpayload=keep
     insmod gzio
     insmod part_gpt
     insmod fat
     set root='hd2,gpt1'
     search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
     linux  /vmlinuz-linux root=UUID=[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR] rw  quiet
     initrd /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-linux-fallback-[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR]' {
     load_video
     set gfxpayload=keep
     insmod gzio
     insmod part_gpt
     insmod fat
     set root='hd2,gpt1'
     search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
     linux  /vmlinuz-linux root=UUID=[COLOR=#0000ff]bbca28b2-503e-4dc8-9850-c54bd0492da8[/COLOR] rw  quiet
     initrd /initramfs-linux-fallback.img
}
menuentry 'Fedora (Workstation)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-simple-[COLOR=#0000ff]9084e0b8-b05b-41af-a4eb-902a0bebe70a[/COLOR]' {
     load_video
     set gfxpayload=keep
     insmod gzio
     insmod part_gpt
     insmod ext2
     set root='hd2,gpt8'
     search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]9084e0b8-b05b-41af-a4eb-902a0bebe70a[/COLOR]
     linux  /boot/vmlinuz root=UUID=[COLOR=#0000ff]9084e0b8-b05b-41af-a4eb-902a0bebe70a[/COLOR] ro rd.driver.blacklist=nouveau resume=UUID=[COLOR=#008000]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] rhgb quiet
     initrd /boot/initrd
}
menuentry 'openSUSE Tumbleweed' --class opensuse --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-[COLOR=#0000ff]06d2aa5d-5c70-4916-9f8f-219f93668d52[/COLOR]' {
     insmod part_gpt
     insmod ext2
     set root='hd2,gpt7'
     search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]06d2aa5d-5c70-4916-9f8f-219f93668d52[/COLOR]
     linux  /boot/vmlinuz root=/dev/sdc7 splash=silent resume=/dev/disk/by-uuid/[COLOR=#008000]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] quiet
     initrd /boot/initrd
}
menuentry 'Xubuntu 18.04' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-[COLOR=#0000ff]27fb4082-7bd3-4974-9fa5-d2b43886513b[/COLOR]' {
     recordfail
     load_video
     gfxmode $linux_gfx_mode
     insmod gzio
     insmod part_gpt
     insmod ext2
     set root='hd2,gpt9'
     search --no-floppy --fs-uuid --set=root [COLOR=#0000ff]27fb4082-7bd3-4974-9fa5-d2b43886513b[/COLOR]
     linux  /boot/vmlinuz root=UUID=[COLOR=#0000ff]27fb4082-7bd3-4974-9fa5-d2b43886513b[/COLOR] ro quiet splash $vt_handoff
     initrd /boot/initrd.img
}
menuentry 'Windows 10' --class windows --class os $menuentry_id_option 'osprober-efi-[COLOR=#ff0000]688D-126B[/COLOR]' {
     insmod part_gpt
     insmod fat
     set root='hd2,gpt1'
     search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]688D-126B[/COLOR]
     chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

The [COLOR=#008000]resume=UUID=bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] part from the openSUSE vmlinuz worked on 18.10 yesterday.
Also, the [COLOR=#008000]resume=/dev/disk/by-uuid//bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] part from the Fedora vmlinuz line would probably work too on the Ubuntu vmlinuz line.
It points to the swap file for resume after suspend.

---

### Post by oldfred on 2018-11-13
Why not use a Windows type entry that boots into the other install's UEFI entry.
       ```
menuentry "Fedora UEFI" {
  search --file --no-floppy --set=root F496-1330
  chainloader (${root})/efi/fedora/grub.cfg
}

``` 
    
Or a configfile entry to boot the other grub.cfg or whatever they use?

I only have Ubuntu and first thing I do is turn off os-prober and add my own 40_custom. Most are configfile as Ubuntu's grub only installs to /EFI/ubuntu.

I am in process of changing to use labels, but some are still like this:

       
```
 menuentry "Cosmic 18.10 on sdb12" { 

  configfile (hd2,gpt12)/boot/grub/grub.cfg 
  } 

```

Then you get the full grub from your other install.

label version:
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)

---

### Post by Dennis N on 2018-11-14
> Why not use a Windows type entry that boots into the other install's UEFI entry.
I agree. This is the only way I know to have a maintenance-free UEFI multiboot setup that includes Fedora. Works with other OS too. In particular, I also use it for Arch-based Manjaro. This was discussed extensively last year in this thread:
[https://ubuntuforums.org/showthread.php?t=2355551](https://ubuntuforums.org/showthread.php?t=2355551)
If you should have two Fedora installations, you can still make the custom menu totally maintenance-free by using two EFI system partitions!
My own working entry: 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'FEDORA 28            lvm - menu' {
insmod part_gpt 
insmod fat
search --no-floppy --fs-uuid --set=root DE47-135A
chainloader /EFI/fedora/shimx64.efi 
} 
```
This method was proposed for multi-booting by J.A. Watson in his ZDNet columns:
[https://www.zdnet.com/blog/jamies-mostly-linux-stuff/](https://www.zdnet.com/blog/jamies-mostly-linux-stuff/)
In particular, see the Mar. 24,26,30,  2015 columns.

---

### Post by Cavsfan on 2018-11-14
> **oldfred said:**
> Why not use a Windows type entry that boots into the other install's UEFI entry.
       ```
menuentry "Fedora UEFI" {
  search --file --no-floppy --set=root F496-1330
  chainloader (${root})/efi/fedora/grub.cfg
}

``` 
    
Or a configfile entry to boot the other grub.cfg or whatever they use?

I only have Ubuntu and first thing I do is turn off os-prober and add my own 40_custom. Most are configfile as Ubuntu's grub only installs to /EFI/ubuntu.

I am in process of changing to use labels, but some are still like this:

       
```
 menuentry "Cosmic 18.10 on sdb12" { 

  configfile (hd2,gpt12)/boot/grub/grub.cfg 
  } 

```

Then you get the full grub from your other install.

label version:
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive)

I know you are light years ahead of most of us, myself included. This is a great idea. I will definitely look into it more.

> **Dennis N said:**
> I agree. This is the only way I know to have a maintenance-free UEFI multiboot setup that includes Fedora. Works with other OS too. In particular, I also use it for Arch-based Manjaro. This was discussed extensively last year in this thread:
[https://ubuntuforums.org/showthread.php?t=2355551](https://ubuntuforums.org/showthread.php?t=2355551)
If you should have two Fedora installations, you can still make the custom menu totally maintenance-free by using two EFI system partitions!
My own working entry: 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'FEDORA 28            lvm - menu' {
insmod part_gpt 
insmod fat
search --no-floppy --fs-uuid --set=root DE47-135A
chainloader /EFI/fedora/shimx64.efi 
} 
```
This method was proposed for multi-booting by J.A. Watson in his ZDNet columns:
[https://www.zdnet.com/blog/jamies-mostly-linux-stuff/](https://www.zdnet.com/blog/jamies-mostly-linux-stuff/)
In particular, see the Mar. 24,26,30,  2015 columns.

Sweet. I guess there are more than one way to accomplish this. Arch already uses the EFI UUID, which is probably why it works so well.

I will definitely look into this. 

I was just happy to be able to create a custom grub period that did not need to be changed but, this looks like the best idea.

Thanks Fred and [COLOR=#000000]Dennis![/COLOR]

Last night, I put together a custom menu that boots into Xubuntu's new kernel, recovery and the backup kernel.
I booted into the backup kernel at present so it works.
FWIW:
```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Fedora 28 (Workstation), openSUSE Tumbleweed, Xubuntu 18.04 and Windows 10"
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-bbca28b2-503e-4dc8-9850-c54bd0492da8' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw  quiet
    initrd /intel-ucode.img /initramfs-linux.img
}
menuentry 'Arch Linux (fallback kernel)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-linux-fallback-bbca28b2-503e-4dc8-9850-c54bd0492da8' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root 688D-126B
    linux  /vmlinuz-linux root=UUID=bbca28b2-503e-4dc8-9850-c54bd0492da8 rw  quiet
    initrd /initramfs-linux-fallback.img
}
menuentry 'Fedora (Workstation)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-simple-9084e0b8-b05b-41af-a4eb-902a0bebe70a' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt8'
    search --no-floppy --fs-uuid --set=root 9084e0b8-b05b-41af-a4eb-902a0bebe70a
    linux  /boot/vmlinuz root=UUID=9084e0b8-b05b-41af-a4eb-902a0bebe70a ro rd.driver.blacklist=nouveau resume=UUID=bbc771f8-ba61-4e50-aeca-d2754b112aee rhgb quiet
    initrd /boot/initrd
}
menuentry 'openSUSE Tumbleweed' --class opensuse --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-06d2aa5d-5c70-4916-9f8f-219f93668d52' {
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt7'
    search --no-floppy --fs-uuid --set=root 06d2aa5d-5c70-4916-9f8f-219f93668d52
    linux  /boot/vmlinuz root=/dev/sdc7 splash=silent resume=/dev/disk/by-uuid/bbc771f8-ba61-4e50-aeca-d2754b112aee quiet
    initrd /boot/initrd
}
menuentry 'Xubuntu 18.04' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-27fb4082-7bd3-4974-9fa5-d2b43886513b' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt9'
    search --no-floppy --fs-uuid --set=root 27fb4082-7bd3-4974-9fa5-d2b43886513b
    linux  /vmlinuz root=UUID=27fb4082-7bd3-4974-9fa5-d2b43886513b ro quiet splash $vt_handoff
    initrd /initrd.img
}
menuentry 'Ubuntu (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-39-generic-recovery-27fb4082-7bd3-4974-9fa5-d2b43886513b' {
    recordfail
    load_video
        gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt9'
    search --no-floppy --fs-uuid --set=root 27fb4082-7bd3-4974-9fa5-d2b43886513b
        linux    /vmlinuz root=UUID=27fb4082-7bd3-4974-9fa5-d2b43886513b ro recovery nomodeset 
    initrd    /initrd.img
}
menuentry 'Xubuntu 18.04 (backup kernel)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-27fb4082-7bd3-4974-9fa5-d2b43886513b' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt9'
    search --no-floppy --fs-uuid --set=root 27fb4082-7bd3-4974-9fa5-d2b43886513b
    linux  /vmlinuz.old root=UUID=27fb4082-7bd3-4974-9fa5-d2b43886513b ro quiet splash $vt_handoff
    initrd /initrd.img.old
}
menuentry 'Windows 10' --class windows --class os $menuentry_id_option 'osprober-efi-688D-126B' {
    insmod part_gpt
    insmod fat
    set root='hd2,gpt1'
    search --no-floppy --fs-uuid --set=root 688D-126B
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

```

---

### Post by Cavsfan on 2018-11-14
> **Dennis N said:**
> I agree. This is the only way I know to have a maintenance-free UEFI multiboot setup that includes Fedora. Works with other OS too. In particular, I also use it for Arch-based Manjaro. This was discussed extensively last year in this thread:
[https://ubuntuforums.org/showthread.php?t=2355551](https://ubuntuforums.org/showthread.php?t=2355551)
If you should have two Fedora installations, you can still make the custom menu totally maintenance-free by using two EFI system partitions!
My own working entry: 
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'FEDORA 28            lvm - menu' {
insmod part_gpt 
insmod fat
search --no-floppy --fs-uuid --set=root DE47-135A
chainloader /EFI/fedora/shimx64.efi 
} 
```
This method was proposed for multi-booting by J.A. Watson in his ZDNet columns:
[https://www.zdnet.com/blog/jamies-mostly-linux-stuff/](https://www.zdnet.com/blog/jamies-mostly-linux-stuff/)
In particular, see the Mar. 24,26,30,  2015 columns.

Also Fedora does not generate a generic symlink for initrd and vmlinuz like every other Linux OS does just after a new kernel is installed.
So, I created a script to run when a new kernel is installed. I'm running it manually now but, I am very close to getting it right.

But, I've got some reading to do it looks like.

Thanks for all of the input.

---

### Post by Cavsfan on 2018-11-14
I also had Sabayon Linux installed for a while and had the grub customized with the UUIDs but, I did not like it much. It failed the 2 .img entries for Arch test just like the rest.

But, so much was missing it wasn't worth the effort to get it right. It's Gentoo-based as it uses Entropy (Equo, Rigo) / Emerge as package managers.

I didn't even save anything on that partition, I just put Xubuntu 18.04 in it's place.

---

### Post by Dennis N on 2018-12-09
> **Cavsfan said:**
> Also Fedora does not generate a generic symlink for initrd and vmlinuz like every other Linux OS does just after a new kernel is installed.
So, I created a script to run when a new kernel is installed. I'm running it manually now but, I am very close to getting it right...
Symbolic link needed in Fedora? The chain loading in the quoted text would always boot the latest kernel without any symbolic link in Fedora since the newest kernel is always placed first in the Fedora grub menu. That's the advantage of doing it this way, and makes it maintenance free.

---

### Post by Cavsfan on 2019-02-10
> **Cavsfan said:**
> Also Fedora does not generate a generic symlink for initrd and vmlinuz like every other Linux OS does just after a new kernel is installed.
So, I created a script to run when a new kernel is installed. I'm running it manually now but, I am very close to getting it right.


> **Dennis N said:**
> Symbolic link needed in Fedora? The chain loading in the quoted text would always boot the latest kernel without any symbolic link in Fedora since the newest kernel is always placed first in the Fedora grub menu. That's the advantage of doing it this way, and makes it maintenance free.

I got the script perfected a while ago, forgot to post it here. Adding this script to /etc/kernel/postinst.d/ also boots into the last installed kernel every time. 
```
#!/bin/bash
#

# We're passed the kernel version being installed
KERNEL_VERSION="$1"

ln -s -f "initramfs-"$1".img" /boot/initrd.img

ln -s -f "vmlinuz-"$1 /boot/vmlinuz

echo "   SUCCESS: symlink initrd.img created for "initramfs-"$1".img"" >&2
echo "   SUCCESS: symlink vmlinuz created for "vmlinuz-"$1" >&2

exit 0

```
I just called it **symlink-kernel** in my home directory.
You install the script with this command: 
```
sudo install symlink-kernel /etc/kernel/postinst.d/symlink-kernel
```

This is my Fedora grub menuentry in Xubuntu 18.04. I've got all of my systems customized because if grub is updated on another system, grub moves to that system.
Arch Linux, Fedora 29, openSUSE TW and Xubuntu 18.04 LTS all have a working **06_custom** file

```
menuentry 'Fedora 29 (Workstation)' --class fedora --class gnu-linux --class gnu --class os --unrestricted $menuentry_id_option 'gnulinux-advanced-[COLOR=#ff0000]1216e907-e6c7-4791-841d-a2d2d7a4dcfc[/COLOR]' {
    load_video
    set gfxpayload=keep
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd2,gpt8'
    search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]1216e907-e6c7-4791-841d-a2d2d7a4dcfc[/COLOR]
    linux  /boot/vmlinuz root=UUID=[COLOR=#ff0000]1216e907-e6c7-4791-841d-a2d2d7a4dcfc[/COLOR] ro resume=UUID=[COLOR=#0000ff]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR] rhgb quiet nouveau.modeset=0 LANG=en_US.UTF-8
    initrd /boot/initrd.img
}

```
```
[cavsfan@fedora ~]$ sudo blkid | grep -e "Fedora" -e "swap"
/dev/sdc4: UUID="[COLOR=#0000ff]bbc771f8-ba61-4e50-aeca-d2754b112aee[/COLOR]" TYPE="swap" PARTLABEL="swap" PARTUUID="c39d976b-91cd-4d59-a270-91398b764d3f"
/dev/sdc8: LABEL="Fedora" UUID="[COLOR=#ff0000]1216e907-e6c7-4791-841d-a2d2d7a4dcfc[/COLOR]" TYPE="ext4" PARTLABEL="Fedora" PARTUUID="887a3d2f-73ed-4894-b566-3e37294757e7"

```
I'm sure some of that is extraneous but, it works and I don't mind.

There are many ways to skin a cat and I have the UUID method working to my satisfaction.

If you did install the script, you would see something like this in the terminal output when a new kernel is installed:
  ```
Running scriptlet: kernel-core-4.20.6-200.fc29.x86_64                                                                                                                                                             169/169 
   SUCCESS: symlink initrd.img created for initramfs-4.20.6-200.fc29.x86_64.img
   SUCCESS: symlink vmlinuz created for vmlinuz-4.20.6-200.fc29.x86_64
```

---

### Post by &amp;wP*!) on 2019-08-02
> **Cavsfan said:**
> I also had Sabayon Linux installed for a while and had the grub customized with the UUIDs but, I did not like it much. It failed the 2 .img entries for Arch test just like the rest.

But, so much was missing it wasn't worth the effort to get it right. It's Gentoo-based as it uses Entropy (Equo, Rigo) / Emerge as package managers.

I didn't even save anything on that partition, I just put Xubuntu 18.04 in it's place.

**Question:** When you boot to Arch, do you mount your ESP? If yes, Is it /boot or /boot/efi? Since you are using Ubuntu Grub to boot Arch, I assume you mount ESP in Arch as mount point /boot/efi. Since you boot Arch kernel from Ubuntu GRUB, I think this mount is not needed.
**Question:** At Arch, when updating the kernel, are the kernel names changing or always the same name?

---

### Post by Cavsfan on 2019-11-12
> **Cavsfan said:**
> Also Fedora does not generate a generic symlink for initrd and vmlinuz like every other Linux OS does just after a new kernel is installed.
So, I created a script to run when a new kernel is installed. I'm running it manually now but, I am very close to getting it right...

> **Dennis N said:**
> Symbolic link needed in Fedora? The chain loading in the quoted text would always boot the latest kernel without any symbolic link in Fedora since the newest kernel is always placed first in the Fedora grub menu. That's the advantage of doing it this way, and makes it maintenance free.

BTW: The bug is still open on this. Still affected by 2 people. 

I currently have Windows 10 and 9 Linux systems installed. My grub jumps from one system to another when a new version is installed on that system. So, I learned to customize them all.

It's been a while since I've had time to look at this again. I've gotten the cruft out of my initial custom menuentries so, linking UUIDs doesn't sound so far fetched. 4 lines and the brackets make 6 lines for each system and _it works every single time_.

I needed a common way to boot every system and this works very well. Also I have Fedora 30 and recently installed Fedora 31.
In that situation what would you do? Your 30 **/EFI/fedora/shimx64.efi** file would have been written over by your 31 **/EFI/fedora/shimx64.efi** file. Getting grub back on Fedora is nearly [[color=blue]impossible[/COLOR]](https://fedoraproject.org/wiki/GRUB_2#Create_a_GRUB_2_configuration).
Most systems have a command to reinstall grub but, not Fedora. 
Ubuntu: **sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/EFI/ubuntu --bootloader-id=ubuntu**
Arch Linux: **sudo grub-install --target=x86_64-efi --efi-directory=/boot/efi/Arch_grub --bootloader-id=Arch_grub**

I installed a drive out of my old computer and grub finds the old legacy Linux installs and adds them. On Fedora 31 normal grub runs for 18-20 minutes on this 4th generation i7 and htop shows it's using 100% CPU during this time.
My custom grub takes < 10 seconds to execute because **10_linux** and **30_os-prober** are not executed. Here is my Fedora 30 and 31 menuentries:
```
menuentry 'Fedora 30 (Thirty)' {
	search --no-floppy --fs-uuid --set=root [COLOR="#0000FF"]43cd93b8-2442-42df-88a3-7bf069390d49[/COLOR]
	linux  /boot/vmlinuz root=UUID=[COLOR="#0000FF"]43cd93b8-2442-42df-88a3-7bf069390d49[/COLOR] ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=[COLOR="#FF0000"]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR] rhgb quiet LANG=en_US.UTF-8
	initrd /boot/initrd.img
}
menuentry 'Fedora 31 (Thirty One)' {
	search --no-floppy --fs-uuid --set=root [COLOR="#009933"]3ba4cef1-ee4e-47a9-acd4-52bccb07a237[/COLOR]
	linux  /boot/vmlinuz root=UUID=[COLOR="#009933"]3ba4cef1-ee4e-47a9-acd4-52bccb07a237[/COLOR] ro rd.driver.blacklist=nouveau modprobe.blacklist=nouveau nvidia-drm.modeset=1 resume=UUID=[COLOR="#FF0000"]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR] rhgb quiet
	initrd /boot/initrd.img
}
```

Bionic Beaver:
```
menuentry 'Xubuntu 18.04.3 Bionic Beaver LTS' {
	search --no-floppy --fs-uuid --set=root [COLOR="#FF8C00"]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]
	linux  /vmlinuz root=UUID=[COLOR="#FF8C00"]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR] ro quiet resume=/dev/disk/by-uuid/[COLOR="#FF0000"]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR] splash
	initrd /initrd.img
}
menuentry 'Xubuntu 18.04.3 Bionic Beaver LTS (recovery mode)' {
	search --no-floppy --fs-uuid --set=root [COLOR="#FF8C00"]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]
	linux  /vmlinuz root=UUID=[COLOR="#FF8C00"]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR] ro recovery nomodeset
	initrd /initrd.img
}
```
```
~$ sudo blkid | grep -e "sdc1:" -e "sdc5" -e "sdc9:" -e "sdc10:" -e "sdc12:"
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="15661847-bc65-401a-84b0-97a157f3949f"
/dev/sdc5: UUID="[COLOR="#FF0000"]b564ed75-b9ee-410f-9f87-04afc30a0ff4[/COLOR]" TYPE="[COLOR="#FF0000"]swap[/COLOR]" PARTLABEL="swap" PARTUUID="dc354366-1300-48d4-8a60-133aa2e2ca57"
/dev/sdc9: LABEL="Fedora" UUID="[COLOR="#0000FF"]43cd93b8-2442-42df-88a3-7bf069390d49[/COLOR]" TYPE="ext4" PARTLABEL="Fedora" PARTUUID="ee5e61eb-eab9-4794-aabe-a84a910fe9a0"
/dev/sdc10: LABEL="Bionic" UUID="[COLOR="#FF8C00"]338e6d3b-cbd4-496d-9cc2-b688a90c17c3[/COLOR]" TYPE="ext4" PARTLABEL="Bionic" PARTUUID="4f579967-b025-47dc-b080-64a0865d7165"
/dev/sdc12: LABEL="Fedora31" UUID="[COLOR="#009933"]3ba4cef1-ee4e-47a9-acd4-52bccb07a237[/COLOR]" TYPE="ext4" PARTLABEL="Fedora31" PARTUUID="c76d0607-d89b-49b5-82fd-f0460ec47cfe"

```
Grub currently is on Fedora 31 but, if grub moves to another installation a grub update on Fedora does not re-install grub there.

Nothing fancy, no background, no font colors, just a custom menu and timeout.

[[img]http://i.imgur.com/yerb7Icm.jpg[/img]](https://imgur.com/yerb7Ic)

---

