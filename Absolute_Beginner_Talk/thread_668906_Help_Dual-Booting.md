---
title: "Help Dual-Booting"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by shoppy123 on 2008-01-15
Hello all. I recently completely switched over to linux and reformatted my entire drive and installed ubuntu onto it. I have been running it for about a week and have become comfortable with the environment. I wanted to try some other distros out there and I tried PCLinuxOS2007. I booted up into the live cd and after playing around with it I decided to install it.
                I resized my partition and installed PCLinux onto a newly formatted 6 gb partition and installed grub as my bootloader. When it came time to reboot I booted up my pc and it goes to grub fine but when I click on any of the entries it neither boots into Ubuntu or goes to PCLinux. It either goes to a black screen or a screen with a lot of text and error messages come up. I have a Ubuntu Live Cd available so if you can please help me it would be much appreciated.

---

### Post by mkoyle on 2008-01-15
Depending on whether you had anything you will miss on there, your best bet might be to just reinstall Ubuntu.  If you install PCLinux on the new partition you made for it and then install Ubuntu into the already-sized partition and allow them both to format you should be in great shape unless the PCLinux CD has an error (and caused this problem).  Why your new distribution will not work at this point is a bit of a mystery to me-- if it actually got to installing files after changing the partitions I do not see what the problem could be.

If you want to try salvaging the drive (to save data, learn -- or just because you want to tackle the challenge), you could start by booting with the live cd and then running the partition editor (I forget, but I think it is under System --> Admin --> Drives or something like that.    It might let you 'apply changes' and suddenly just work.

you might want to try running the filesystem repair program 'fsck'  First you need to know what your harddrive is called so run 

```
sudo fdisk -l
```

Here is my output from that command:

```
matthew@Judith:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60410   485235292+  83  Linux
/dev/sda2           60411       60801     3140707+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd398d398

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          30      240943+  83  Linux
/dev/sdb2              31        9729    77907217+   5  Extended
/dev/sdb5              31         279     2000061   82  Linux swap / Solaris
/dev/sdb6             280        9729    75907093+  83  Linux

```

For the devices that list 'Linux' in the system column (on my system they are /dev/sda1, /dev/sdb1, and /dev/sdb6 your drives might happen to appear as /dev/hd*, too) run 'sudo fsck (device)  as follows:

```
sudo fsck /dev/sd__
```

Anyway, if you still need help (if you decide to try to recover something and the above has not worked) I will need a bit of information to know what to do.  Post the output from the following:

```
sudo fdisk -l
```

---

### Post by shoppy123 on 2008-01-15
Well here is the result of the fdisk -l command.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fac9119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17854   143412223+  83  Linux
/dev/sda2           17855       19457    12876097+   5  Extended
/dev/sda5           17855       18704     6827593+  83  Linux
/dev/sda6           18705       19457     6048441   82  Linux swap / Solaris

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984     1983619+   6  FAT16
l
```
And here is my menu.lst file as well cause I figured I'm going to need to edit that as well.
```
timeout 10
color black/cyan yellow/cyan
default 4

title PcLinuxOS2007
kernel (hd0,0)/boot/vmlinuz-2.6.22-14-generic BOOT_IMAGE=PcLinuxOS2007 root=/dev/sda6  acpi=on resume=/dev/sda6 splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title linux-nonfb
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda1  acpi=on resume=/dev/sda6
initrd (hd0,0)/boot/initrd.img

title 2.6.18.8.tex5
kernel (hd0,0)/boot/vmlinuz-2.6.18.8.tex5 BOOT_IMAGE=2.6.18.8.tex5 root=/dev/sda1  acpi=on resume=/dev/sda6 splash=silent vga=788
initrd (hd0,0)/boot/initrd-2.6.18.8.tex5.img

title failsafe
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda1  failsafe acpi=on resume=/dev/sda6
initrd (hd0,0)/boot/initrd.img

title Ubuntu Gutsy Gibbon
kernel (hd0,0)/boot/vmlinuz-2.6.22-14-generic BOOT_IMAGE=Ubuntu_Gutsy_Gibbon root=/dev/sda1 
initrd (hd0,0)/boot/initrd.img
```
I don't really want to reinstall everything again because I've probably spent around ten hours configuring my computer and installing software. I think it is fixable I just don't know where to start.

---

### Post by shoppy123 on 2008-01-15
Oh and I have another question if I copy my entire filesystem exactly as is onto dvds and I reinstall ubuntu can I copy the files back over and overwrite everything will everything be exactly the same as it is now?

---

### Post by JoshuaRL on 2008-01-16
I would try SuperGrub first:

> **c0met said:**
> 
Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...
[LIST]
[*]making your win(dows) drive bootable
[*]making your linux drive bootable
[*]setting your system up for a dual boot
[/LIST]
If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. You can download the ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")


That was taken from [http://ubuntuforums.org/showthread.php?t=666838](http://ubuntuforums.org/showthread.php?t=666838)  And it worked for him.  Not exactly the same problem, but along the same lines and I believe it will work for you too.

---

### Post by shoppy123 on 2008-01-16
It didn't work. It just took me back to the grub loader that I began seeing after I installed PCLOS. Any other suggestions?

---

### Post by mkoyle on 2008-01-18
So right now you cannot boot with ANY of those boot options, right?

If you want to salvage all of the settings you have already configured on the ubuntu system, copying the contents of /etc and /home should save most things (and if you have created an apache web page or something that uses /var, include it, too).  What have you installed / modified?

Could you cull some of the error messages that you get and tell me which grub selection does what-- the black screens and the error messages.

Which drive did you get that menu.lst from?  Is that the one on /dev/sda1?

Post what is in your /dev/sda1, /dev/sda5.  I could also use the contents of /etc/fstab.  If you do not know how, use the following after booting a live cd:

```
cd ~/
mkdir sda1
mkdir sda5
mount /dev/sda1 ./sda1
mount /dev/sda5 ./sda5
```

If the mount commands give you trouble, run them as root by using 'sudo mount /dev/sda1 ./sda1'

What I want to see is the contents of boot, and of the fstab files on both drives:

```
ls -l ./sda1
ls -l ./sda1/boot
ls -l ./sda5
gedit ./sda1/etc/fstab
gedit ./sda1/boot/menu.lst
```

You may have already posted the menu.lst file from there; if so, just note that that is what you already posted (I'm just making sure we are looking at what is actually booting off your drive).

--Matthew

---

