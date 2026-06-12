---
title: "GRUB boots to incorrect partition"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by HokkaidoHillbilly on 2007-04-15
Trying to help a buddy set up Edgy in a dual-boot config w/ WinXP on a Qosmio E10/2KCDTW, we've run into a GRUB problem.

On boot, the computer gives a "GRUB Hard Disk Error", so I booted to the Live CD, ran sudo fdisk -l and figured out that GRUB is booting to /dev/hda2, which is some sorta hidden Win 95 FAT32 partition.

I want it to boot to /dev/hda1, which is the main WinXP/NTFS partition, but what would be the best way to do this?  I've tried running sudo grub from the Live CD terminal, but haven't quite yet been able to figure it out.

For a little more info, this is what I get from sudo fdisk -l:

Device          Boot   ................   Id                      System
/dev/hda1                                   7                      HPFS/NTFS
/dev/hda2       *                          1c                     Hidden W95 FAT32 (LBA)
/dev/hda3                                  83                     Linux
/dev/hda4                                   5                      Extended Partition
/dev/hda5                                  82                     Linux swap / Solaris

Any ideas?

Thanks!

---

### Post by rsambuca on 2007-04-15
boot from the live CD and enter in a terminal```
sudo grub
```at the grub> prompt, enter```
find /boot/grub/stage1
```and see what it says.

---

### Post by HokkaidoHillbilly on 2007-04-16
Ok, booting via the Live CD, it get (hd0,2), but like I said, according to sudo fdisk -l, the only thing that was starred under "Boot" was the hidden 7MB partition.

Any ideas?

---

### Post by bwhite82 on 2007-04-16
Try this:

1) Boot into the LiveCD

2) Goto System>Administration>Gnome Partition Editor and find the HD you are trying to boot to in the list.

3) Make sure that under 'Mount point' you see a '/' 

4) Right click on it and goto 'Manage flags'

5) Check 'boot' and click close

6) Reboot

---

### Post by indytim on 2007-04-16
Assuming your Feisty is on say sda3:

1.  boot to your LiveCD

When you have booted up, go to the terminal

```

$ sudo mkdir /media/sda3
$ sudo mount /dev/sda3 /media/sda3
$ cd /media/sda3/boot/grub
$ sudo cp menu.lst menu.lst-bu
$ sudo gedit menu.lst 

```

Find the entry for your feisty kernel.  It'll look something like this

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```

The entry you want to change is the location of "root".  Change this to the partition containing Feisty (remember the numbering system in grub starts with " 0 ".  Save the file and re-boot.

Hopefully things will now be happy for you.

IndyTim

---

### Post by HokkaidoHillbilly on 2007-04-16
Will do, but will have to wait till tomorrow when I'm at work.  Thanks for all the help and I'll let ya know how it goes.

Cheers!

---

