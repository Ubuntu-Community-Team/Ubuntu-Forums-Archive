---
title: "Built new kernel and failed in reboot."
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Hxsrmeng on 2007-07-30
My computer is on Ubuntu Linux System 7.04 (Kernel version 2.6.20-15 generic).
I have done followings:

1.  downloaded the kernel source code 2.6.22.1 from kernel.org and unzipped it to: /home/linux/linux-2.6.22.1
2.  configured and built it with "make defconfig" and "make".
3.  I did use "make menuconfig" before "make", but actually I just took a look of the menus and didn't change anything.
4.  My linux system doesn't show me any mkinitrd package in synaptic package manager. But I heard now initramfs-tools had already been using instead of mkinitrd. I have this one installed. I don't know whether it matters.
5.  Installed modules with "sudo make modules_install" and got message:

    "
     INSTALL drivers/scsi/scsi_wait_scan.ko
     if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map  2.6.22.1; fi
     "

5.  use "sudo make install" and got message:
"
sh /home/dongrm/linux/linux-2.6.22.1/arch/i386/boot/install.sh 2.6.22.1 arch/i386/boot/bzImage System.map "/boot"
In order to use the new kernel image you have just installed, you
will need to reboot the machine.  First, however, you will need to
either make a bootable floppy diskette, re-run LILO, or have GRUB
installed.
Checking for ELILO...No
GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.22.1
"
6. Now I have these files in the folder /boot/
config-2.6.20-15-generic, config-2.6.22.1;                
System.map-2.6.20-15-generic, System.map-2.6.22.1;
vmlinuz-2.6.20-15-generic, vmlinuz-2.6.22.1;
initrd.img-2.6.20-15-generic

but I don't have initrd.img-2.6.22.1

7. Then I checked the bootloader file: /boot/grub/menu.lst, which had two relative items:
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e9d2d832-9b9b-4d26-b829-d5a379b3b838 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e9d2d832-9b9b-4d26-b829-d5a379b3b838 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

8.  According to the second one, i added one:
title           Ubuntu, kernel 2.6.22.1 (on July 29, 2007)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.22.1 root=UUID=e9d2d832-9b9b-4d26-b829-d5a379b3b838 ro single

since I don't have img file, I delete that line with img.

9. I rebooted my computer and chose this kernel, the boot process stops at the message:

"
VFS: Unable to mount root fs via NFS. Trying floopy.
VFS: Insert root floppy and press Enter.
"

I can not figure out what the wrong is. Can you help me with this?

---

### Post by deadgobby on 2007-07-30
sh /home/dongrm/linux/linux-2.6.22.1/arch/i386/boot/install.sh 2.6.22.1 arch/i386/boot/bzImage System.map "/boot"
In order to use the new kernel image you have just installed, you
will need to reboot the machine. First, however, you will need to
either make a bootable floppy diskette, re-run LILO, or have GRUB
installed.
Checking for ELILO...No
GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.22.1

I would of stop right after that. 
[http://www.hrlug.org/rescuedisk.html](http://www.hrlug.org/rescuedisk.html)
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by Hxsrmeng on 2007-07-30
> **deadgobby said:**
> sh /
.....
GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.22.1

I would of stop right after that. e[/url]

Thanks. Actually I don't understand you. Do you mean I needn't to touch menu.lst and reboot immediately?
 
Actually I didn't understand "point your default entry in menu.lst to /boot/vmlinuz-2.6.22.1" either.

---

### Post by xhizors on 2007-07-30
> **Hxsrmeng said:**
> Thanks. Actually I don't understand you. Do you mean I needn't to touch menu.lst and reboot immediately?
 
Actually I didn't understand "point your default entry in menu.lst to /boot/vmlinuz-2.6.22.1" either.

**_inside GRUB's menu.lst:_**


 instead of your old default kernel, you want to replace it with this:

        kernel  **/boot/vmlinuz-2.6.22.1** .... [etc]

You want to point your default boot entry to your new kernel, instead of the previous one.

---

### Post by walkerk on 2007-07-30
I wrote a howto on a simple way to install 2.6.22-8-generic but i don't think the moderators wanted to let it slide through..

using feisty fawn:

i added the gutsy repositories to sources.list.

sudo apt-get update

use synaptic to install the necessary linux-headers-2.6.22.-8-generic, linux-image-2.6.22-8-generic.. the modules etc.

once done. remove the repositories and reboot. voila! you booted into 2.6.22-8. 

too bad they didn't post my thread up.. i have it step by step all in command line. copy and paste would have done the trick..

oh well.. with teh above i think you can accomplish this.. unless of course your set on compiling the kernel yourself. in that case, i say enjoy :) don't get too frustrated.

---

### Post by Hxsrmeng on 2007-07-30
> **xhizors said:**
> **_inside GRUB's menu.lst:_**


 instead of your old default kernel, you want to replace it with this:

        kernel  **/boot/vmlinuz-2.6.22.1** .... [etc]

You want to point your default boot entry to your new kernel, instead of the previous one.

Thanks.
So, if I still want to keep the old one as my default boot entry, I don't need to do anything with the menu.lst?

---

### Post by Hxsrmeng on 2007-07-30
> **walkerk said:**
> I wrote a howto on a simple way to install 2.6.22-8-generic but i don't think the moderators wanted to let it slide through..

using feisty fawn:

i added the gutsy repositories to sources.list.

sudo apt-get update

use synaptic to install the necessary linux-headers-2.6.22.-8-generic, linux-image-2.6.22-8-generic.. the modules etc.

once done. remove the repositories and reboot. voila! you booted into 2.6.22-8. 

too bad they didn't post my thread up.. i have it step by step all in command line. copy and paste would have done the trick..

oh well.. with teh above i think you can accomplish this.. unless of course your set on compiling the kernel yourself. in that case, i say enjoy :) don't get too frustrated.

Thanks.

Yes, I want my own.

---

### Post by Lakefall on 2007-07-30
You either need to create an initrd for your kernel or to reconfigure it. As you are compiling your own kernel presumably to be used on single system only, you don't really need an initrd. You just need to make sure the essential code for mounting your root (/) partition is compiled into the kernel itself instead of being compiled as a module. (Without an initrd, the kernel cannot access the modules before the root is mounted.) The essential code includes the driver for the file system (most likely ext3) and the drivers needed to access the disk itself (probably [SATA](http://en.wikipedia.org/wiki/Serial_ATA) or [PATA](http://en.wikipedia.org/wiki/AT_Attachment)).

Also, after installing the kernel you may need to manually rename the symbolic link /boot/initrd.img to /boot/initrd.img.old or something like that (AFAIR) and to run update-grub (to automatically update the menu.lst).

Hmm.. and you may need to edit /usr/sbin/update-grub to add "#" at ```
# Update the root device to mount-by-UUID
kopt=$(convert_kopt_to_uuid "$kopt")
``` making it ```
# Update the root device to mount-by-UUID
#kopt=$(convert_kopt_to_uuid "$kopt")
``` and to stop using them damn UUIDs in the menu.lst. Something like this:```
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro
```
Note that the last quoted line (the only one that does stuff) is confusingly supposed to be commented out for the update-grub script.

---

### Post by Hxsrmeng on 2007-07-30
> **Lakefall said:**
> You either need to create an initrd for your kernel or to reconfigure it. As you are compiling your own kernel presumably to be used on single system only, you don't really need an initrd. You just need to make sure the essential code for mounting your root (/) partition is compiled into the kernel itself instead of being compiled as a module. (Without an initrd, the kernel cannot access the modules before the root is mounted.) The essential code includes the driver for the file system (most likely ext3) and the drivers needed to access the disk itself (probably [SATA](http://en.wikipedia.org/wiki/Serial_ATA) or [PATA](http://en.wikipedia.org/wiki/AT_Attachment)).

Forgot to say this is my laptop, with Windows XP and Ubuntu 7.04 mixed.

Do I still need a initrd? Where can I get it or which command will generate it?

Sorry, I don't understand "You just need to make sure the essential code for mounting your root (/) partition is compiled into the kernel itself instead of being compiled as a module."
Does it cause the boot message: 
"
Root-NFS: No NFS server available, giving up?
"

Does the file bzImage work? 

Thanks

---

### Post by Lakefall on 2007-07-30
> **Hxsrmeng said:**
> Forgot to say this is my laptop, with Windows XP and Ubuntu 7.04 mixed.
That shouldn't make any difference.

> Do I still need a initrd?
Actually I said you don't really need one.

> Where can I get it or which command will generate it?
I don't remember, because I never do it.

> Sorry, I don't understand "You just need to make sure the essential code for mounting your root (/) partition is compiled into the kernel itself instead of being compiled as a module."
Does it cause the boot message: 
"
Root-NFS: No NFS server available, giving up?
"
I think I wasn't paying attention. Your root partition is mounted over [NFS](http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29)? What I said should still apply, but it's the NFS support (and ext3) you need to have in the kernel (instead of a module), I suppose.

I don't know much about configuring NFS, but if you're not supposed to be doing anything with NFS (or know what it is) then things are definitely not working right. I don't remember if that error might be related to the whole UUID thing, which seems like a dirty Ubuntu-specific hack, which messes things up for kernel compilers. :-(

make menuconfig lets you choose if something is compiled as a built-in or a module. You need to have the stuff required to mount the root as built-in unless you have an initrd. Press Y instead of M. Also I don't know if make defconfig was even a good idea. make oldconfig might have been better.

> Does the file bzImage work?
What do you mean?

---

### Post by Hxsrmeng on 2007-07-30
> **Lakefall said:**
> 
I think I wasn't paying attention. Your root partition is mounted over NFS? What I said should still apply, but it's the NFS support (and ext3) you need to have in the kernel (instead of a module), I suppose.
make menuconfig lets you choose if something is compiled as a built-in or a module. You need to have the stuff required to mount the root as built-in unless you have an initrd. Press Y instead of M. Also I don't know if make defconfig was even a good idea. make oldconfig might have been better.


I will try what you said. Based on what I can understand.:)

I just copy ~USER/linux/linux/2.6.22.1/arch/i386/boot/bzImage to /boot
Since I don't have .img file there.  But it turned out not work. :(

Thank you!

---

### Post by Lakefall on 2007-07-30
I think you have to do this before it will work:> **Lakefall said:**
> Hmm.. and you may need to edit /usr/sbin/update-grub to add "#" at ```
# Update the root device to mount-by-UUID
kopt=$(convert_kopt_to_uuid "$kopt")
``` making it ```
# Update the root device to mount-by-UUID
#kopt=$(convert_kopt_to_uuid "$kopt")
``` and to stop using them damn UUIDs in the menu.lst. Something like this:```
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro
```
Note that the last quoted line (the only one that does stuff) is confusingly supposed to be commented out for the update-grub script.
And run update-grub.

 The kernel.org kernels do not support UUIDs as far as I've seen. Perhaps having an initrd would change that, but otherwise you need to use the /dev/?d?? syntax.

edit: Make sure if you are actually doing anything with NFS. I guess the odds are you aren't. If you don't know what it is, you definitely aren't.

---

