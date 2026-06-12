---
title: "ubuntu 16.04.1 server on macpro2,1"
date: 2016-08-13
forum: Apple Hardware Users
---

### Post by djsmirk on 2016-08-13
Hello

I just want to post a success story.  I was able to install Server 16.04.1 onto a Macpro2,1 (eight core) last week.

For reference, these links were a huge help:

[https://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/]("https://blog.christophersmart.com/2009/07/23/linux-on-an-apple-xserve-efi-only-machine/")
[https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")
[http://blog.sergem.net/how-to-install-ubuntu-14-04-on-macpro-11-efi-boot-mode/]("http://blog.sergem.net/how-to-install-ubuntu-14-04-on-macpro-11-efi-boot-mode/")
[http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/]("http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/")

Tools Used:

- Macbook Pro with VMware Fusion.  Ubuntu 16 desktop as a guest
- 8Gb Lexar USB2 stick

I tried to document everything I did, so here we go:

1.  Build i386-efi bootloader using latest grub2 code (I pulled the source from git.  At the time, the version of grub2 was 2.02~beta3)

[LEFT]```
#./autogen.sh

#export EFI_ARCH=i386
#./configure --with-platform=efi --target=${EFI_ARCH} --program-prefix=&#8220;"
#make
#cd grub-core 
#../grub-mkimage -O ${EFI_ARCH}-efi -d . -o bootia32.efi -p "" part_gpt part_msdos ntfs ntfscomp hfsplus fat ext2 normal chain boot configfile linux multiboot loadbios reboot appleldr halt search gfxterm gfxmenu efi_uga efi_gop font
```[/LEFT]

2.  Prepare USB stick for booting (obviously my USB stick was at /dev/sdb, this may not be the same in your system.  use ```
dmesg
``` to verify)
[LEFT]```
#sudo parted -s /dev/sdb mklabel gpt mkpart EFI fat32 0% 100% toggle 1 boot
#mount /dev/sdb /media/usb

#mkdir -p /media/usb/efi/boot
#cp ~/grub/grub-core/bootia32.efi /media/usb/efi/boot
```[/LEFT]

3.  Create the grub.cfg (placed in /media/usb/efi/boot/grub.cfg)
[LEFT]```
insmod efi_gop
insmod efi_uga
insmod font

if loadfont ${prefix}/unicode.pf2
then
    insmod gfxterm
    set gfxmode=auto
    set gfxpayload=keep
    terminal_output gfxterm
fi
linux /efi/boot/linux **nomodeset**
initrd /efi/boot/initrd.gz
```
[/LEFT]

I add to add the kernel option "nomodeset" because the system would crash.  My macpro has an ATI Radeon based video card and I found this link:

[http://apple.stackexchange.com/questions/211260/grub-2-fb-swiutching-to-radeondrmfb-from-efi-vga]("http://apple.stackexchange.com/questions/211260/grub-2-fb-swiutching-to-radeondrmfb-from-efi-vga")

The linux and initrd.gz images were taken from the Ubuntu Server 16.04.1 netinstall image.  I just used wget to download them directly.

At this point the USB stick is ready to boot, so I can just umount it and put it into the macpro.  The guided partitioning automatically created a ESP "EFI System Partiion" for me, so I didn't have to worry about making it myself (previous howto articles discussed having to do this)

I installed base packages and completed the install.  So far so good...

4.  At this point, Ubuntu is installed but the macpro will not boot **into** Ubuntu.  This is because the ESP created during install is a VFAT partiion.  Apple's EFI architecture looks for a HFS partition.  Using the USB stick, I booted back into grub and booted Ubuntu manually:
[LEFT]```
linux /boot/vmlinuz-4.4.0-34-generic.efi.signed root=UUID=some_UUID nomodeset
initrd /boot/initrd.img-4.4.0-34-generic
boot
```[/LEFT]

Now, in order to complete this, I needed get the UUID of the &#8220;root&#8221; partition.  Within grub &#8220;ls -l&#8221; is supposed to show that, but it didn&#8217;t work for me.  I don't know if this is a bug, but &#8220;ls -l&#8221; seemed to be broken.

However, the command would boot Ubuntu but since it couldn't find the boot partition, it dropped me into a initramfs BusyBox shell.  Here I could use ```
blkid
``` to get the UUID of the root partition to properly boot.

Now I could complete the &#8220;fixing the EFI partition" steps from [http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/]("http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot/")

[LEFT]Some notes from changing the ESP partition:
Since the Mac Pro has a 32bit EFI, I installed these packages instead:

sudo apt-get install mactel-boot hfsprogs gdisk grub-efi-ia32

only to find out that grub-efi-ia32 is already installed

In order to update /etc/fstab, I had to modify the command to this:

```
sudo bash -c 'echo $(blkid -o export -s UUID /dev/sda1 | grep UUID -A 1) /boot/efi auto defaults 0 0 >> /etc/fstab'
```

This was because the &#8220;blkid -o export -s UUID /dev/sda1&#8221; command gave me both DEVNAME and UUID in the output, and we only need the UUID (probably due to changes in blkid since the article was first written)

When updating/installing grub, I had to refect a 32bit EFI and not a 64bit:

```
sudo grub-install &#8212;target i386-efi &#8212;boot-directory=/boot &#8212;efi-directory=/boot/efi &#8212;bootloader-id=&#8220;$(lsb_release -ds)&#8221;
```

After "blessing" the bootloader, the macpro would boot into Ubuntu but I had no video on my monitor.  I could ping the box from my LAN, so thats good.  But no SSH because I didnt install it.  OOPS!

I had to use the USB stick to manually boot so that I could then modify the grub.cfg for a text based boot:

GRUB_CMDLINE_LINUX_DEFAULT=&#8220;nomodeset&#8221;

Because the ESP partition is HFS based, the grub os_prober also added MAC OS boot options.  This is no good.  So I disabled the grub os_prober:

GRUB_DISABLE_OS_PROBER=&#8220;true&#8221;
[/LEFT]

5.  Fini!  The macpro would now boot into Ubuntu with a text based boot.  This machine is going to be a headless machine, so technically it didn't matter.  But I figured that I might eventually need to access the console, so having video at the console would probably be a good idea.

6.  The macpro is now running plexmediaserver, sonarr, sabnzbdplus and transmission and samba as my home media server/downloading box with a 1TB drive and 2TB drive for storage.  The boot drive is 500GB.  I just dropped in 16GB of RAM as well (I bought it with the default 2GB)


I hope this helps someone else in the future!

---

