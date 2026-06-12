---
title: "GRUB seemingly unfixable"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by opticyclic on 2006-10-15
I am using Dapper, but I have a SATA disk with several partitions on it (XP and Vista RC2).
Either after I installed Vista, or after I removed Linspire (and deleted the partition it was on) I can't get back into Ubuntu.
I am worried that it might not just be a GRUB issue, but a kernel issue as well.

I have tried several HowTos to no avail.

I hoped to be able to automagically update grub but I cant do it from the LiveCD```
sudo update-grub
```Even though I have mounted my installation it doesn't modify the menu.lst.```
ubuntu@ubuntu:/mnt/old/boot$ sudo grub-install /dev/sda3
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/mnt/old/boot$ sudo grub-install /dev/hda
/dev/hda: Not found or not a block device.
ubuntu@ubuntu:/mnt/old/boot$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/mnt/old/boot$
```

[This]("http://ubuntuforums.org/showpost.php?p=117829&postcount=2") doesn't help either ```
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.
```

The 6.06 LiveCD doesn't seem to be able to set the flags for root, boot as per ([Restore Grub]("http://doc.gwos.org/index.php/Restore_Grub")) , but I can get some way with my 5.10 LiveCD.
However, it doesn't fix the messed up grub options.  

I have posted the key part of my menu.lst at the bottom.
I get Kernel Panic messages when I try the last option in my list and the others don't work.

I am a bit concerned that my device.map is empty and that the kernel version on my main installation seems to be so different from the LiveCD.
```
**ubuntu@ubuntu:/boot$ ls**
abi-2.6.15-23-386     initrd.img-2.6.15-23-386  [SIZE="2"][COLOR="Red"]vmlinuz-2.6.15-23-386[/COLOR][/SIZE]
config-2.6.15-23-386  memtest86+.bin
grub                  System.map-2.6.15-23-386
ubuntu@ubuntu:/boot$ cd /mnt/old/boot
**ubuntu@ubuntu:/mnt/old/boot$ ls**
cboot.b        debian.bmp        initrd-2.6.10.gz.inf   sarge.bmp
coffee.bmp     debianlilo.bmp    linux-swap.swp         sid.bmp
config         grub              los-bootsplash.bmp     System.map-2.6.10
config-2.6.10  initrd-2.6.10.gz  los-bootsplash.xpm.gz  [SIZE="2"][COLOR="Red"]vmlinuz-2.6.10[/COLOR][/SIZE]
ubuntu@ubuntu:/mnt/old/boot$
 
```


See below output from fdisk and the attachment for a screenshot of GParted.
```
ubuntu@ubuntu:/mnt/old/etc$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   218130569    67119570    f  W95 Ext'd (LBA)
/dev/sda3   *   270630993   312576704    20972856   83  Linux
/dev/sda4       218130570   270630989    26250210    7  HPFS/NTFS
/dev/sda5        83891493    98590904     7349706    b  W95 FAT32
/dev/sda6        98590968   138432104    19920568+   7  HPFS/NTFS
/dev/sda7       138432168   176184854    18876343+   7  HPFS/NTFS
/dev/sda8       176184920   218130569    20972825    7  HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:/mnt/old/etc$
 
```


I have tried [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") and this works for restoring my MBR for Windows, but it doesn't seem to save the menu.lst for linux.

This is the end of my menu.lst
I made it from installing grub with the LiveCD to get the standard version, then tried to edit it.
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=unionfs ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

title		Ubuntu, kernel 2.6.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.2.6.10.gz
savedefault
boot

title		Linux
root		(hd0,2)
kernel	/vmlinuz root=/dev/sda3 ro
 
```

---

### Post by TrendyDark on 2006-10-15
Grub shows up, but Ubuntu is not on the list?

---

### Post by opticyclic on 2006-10-15
Thats correct.
My menu.lst is all messed up.
I think it is because I can't find the right kernel to boot.
I think I have the correct drive (/dev/sda3)

---

### Post by misha680 on 2006-10-16
Well if you mount the drive from the live cd (say in /tmp/a) and modify the menu.lst, you can use the grub-install command from the live CD as follows:

```
sudo grub-install --root-directory=/tmp/a /dev/sda
```

Also you might try changing your root directory on the autokernels too since it seems that it is wrong now (change from hd(0,0) to hd(0,2) and also find the line that starts with kopt=root=something and change that to kopt=root=/dev/sda3 (or whatever partition).

Hope that helps.

Misha

---

### Post by opticyclic on 2006-10-16
Unfortunately when I try that I get
install_device not specified

---

### Post by misha680 on 2006-10-16
Wow that was a fast reply. I just changed the command? What about the new one (I did not have the /dev/sda in there yet when I first posted it).

Misha

---

### Post by opticyclic on 2006-10-16
When I do 
sudo grub-install --root-directory=/mnt/root hd0

I get /dev/sda3 does not have any corresponding BIOS drive.

edit: same with sudo grub-install --root-directory=/mnt/root /dev/sda

---

### Post by misha680 on 2006-10-16
Hmm, that's weird. If it's sda3 shouldn't your boot device be /dev/sda? Otherwise maybe you need to change sda3 to hda3 if /dev/sda doesn't work for grub-install but /dev/hda does. But I'm honestly not sure, I never really figured out the hda vs sda thing.

But I know for sure that on a Dapper Live CD the grub-install --root-directory=somewhere /dev/somewhere will work, because when I got rid of Windows for good I switched around my partitions and then had to switch my root partitions this way. I had to change the kopt=root= line and also the hd(x,x) strings, did the grub-install and then it worked.

Misha

p.s. Hmm... that is weird, especially if your screenshots from gparted and fdisk are from the same live CD as you are running these commands. Otherwise, if you are using a different version  of the live CD now than you were then maybe you just need to use the same version (or change the root device name to whatever gparted says on the current live CD). If that doesn't fix it, and it doesn't work from the Dapper Live CD using the same device name as gparted says for the root device in the update-grub command, I am really not sure :( )

---

### Post by Herman on 2006-10-17
Hello opticyclic,
Repairing your menu.lst is not a function  of Super Grub disk, but  you should be able to boot your Ubuntu automatically with Super Grub Disk by going 'English Super Grub Disk'-->'Gnu-Linux'-->'Boot Gnu-Linux Directly'-->'SCSI', and then Super Grub should boot Ubuntu for you by finding the symlinks in '/' root, to whatever kernel and initrd.img you have installed.

Another (manual) approach would be to use either the installed Grub's or Super Grubs's Grub Command Line Interface, (press 'c' from any Grub menu), for investigating your computer and finding out how to boot it, here's the link, [COLOR=#33ff33][Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
[COLOR=Black]You should be able to do as described in this link following, and do a [Direct Kernel Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")
If you take notes while you are doing that, you can use the same commands in your menu.lst, to repair it after you boot Ubuntu.

Here's what I guess your menu.lst entry should look like for Ubuntu, and pretty near [/COLOR][/COLOR][COLOR=#33ff33][COLOR=Black]the same[/COLOR][/COLOR][COLOR=#33ff33][COLOR=Black] commands should work in [/COLOR][/COLOR][COLOR=#33ff33][COLOR=Black]your Command Line Interface  as well, if Ithese are correct. (Except you can omit the 'savedefault' if you want, especially when booting from the command line.
[/COLOR][/COLOR]```
title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda3 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot
```You can re-install Grub to MBR as illustrated here, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"), if that's another thing you need to do. Or use Super Grub Disk to do that instead.

I hope that will be helpful to you, 
Regards, Herman :D

---

### Post by opticyclic on 2006-10-20
hmm when I look in the  /usr/src/linux directory all I can find is my linspire kernels.
when I look in /var/cache/apt/archives all I can find if references to 2.6.10

I have a terrible feeling that somehow my Ubuntu kernels were stored on my Linspire partition - which is now my Vista partition :( 

Right now I am going to try forcing an installation of the kernel in the boot directory following this info
[http://ubuntuforums.org/showpost.php?p=1431609&postcount=50](http://ubuntuforums.org/showpost.php?p=1431609&postcount=50)

However, I am having to compile my own kernel following this info
[http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)

Unless there is a precompiled deb for Dapper somewhere that might save me time?

---

### Post by catlett on 2006-10-20
> **opticyclic said:**
> hmm when I look in the  /usr/src/linux directory all I can find is my linspire kernels.
when I look in /var/cache/apt/archives all I can find if references to 2.6.10

I have a terrible feeling that somehow my Ubuntu kernels were stored on my Linspire partition - which is now my Vista partition :( 

Right now I am going to try forcing an installation of the kernel in the boot directory following this info
[http://ubuntuforums.org/showpost.php?p=1431609&postcount=50](http://ubuntuforums.org/showpost.php?p=1431609&postcount=50)

However, I am having to compile my own kernel following this info
[http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)

Unless there is a precompiled deb for Dapper somewhere that might save me time?

Go here and scroll down to get the kernel debs for dapper [http://packages.ubuntu.com/dapper/base/](http://packages.ubuntu.com/dapper/base/)

---

