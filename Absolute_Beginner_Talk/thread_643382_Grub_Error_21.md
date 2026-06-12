---
title: "Grub Error 21"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by foxjps on 2007-12-17
Ok so I installed onto my external HDD and clicked reboot then on restart I had an error 21....I have absolutely no clue what to do.

(Please explain everything, I've never touched Linux before).


Thanks.

---

### Post by Lord_Dicranius on 2007-12-17
Well, I know the GRUB error 21 means that it could not find the disk.

Found these two results by Googling:
[http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)
[http://osdir.com/ml/boot-loaders.grub.bugs/2003-02/msg00080.html](http://osdir.com/ml/boot-loaders.grub.bugs/2003-02/msg00080.html)

---

### Post by logos34 on 2007-12-17
Did you let it install grub bootloader to the default location (hd0), i.e. internal drive?

---

### Post by Presto123 on 2007-12-17
Yup...If you want the simplest way to do it...download SuperGrub, burn it like you did for Ubuntu, have it in the drive when you want Linux, and it will pull up your drive when you click on "Linux" after it loads.

Also, if you are dual booting it, you will probably want that disk to fix your Windows MBR back to normal.

The alternative is to edit the grub file...

---

### Post by foxjps on 2007-12-17
Supergrub isn't an option because I ran out of Cd's (...) I tried [http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)

but I get:
```

root@ubuntu:/home/ubuntu# grub-install /dev/sda1/
/dev/sda1/: Not found or not a block device.
```


I'm trying to reinstall (again..) now.

---

### Post by discoade on 2007-12-17
im not 100% on this but how can an os boot from a usb assuming it is usb!
 drive until your usb port drivers are loaded is there an option in the bios to boot from usb?  im probably talking crap so if i am just ignore me!:)

---

### Post by Presto123 on 2007-12-17
OH...it does, I had an external running it for a while. 320 gig external was running 7.10 on my laptop before I found out how to get it to dual-boot onto my locked NTFS partition.

The problem he is having here is that the Grub file loaded onto his main hard drive. I have never found a way around this, either.

---

### Post by foxjps on 2007-12-17
Hmm I did a full reinstall and it completed successfully however I still receive error 21..at a bit of a loss now. 



Have no idea how to boot Supergrub from a USB drive (I do have one)

---

### Post by Presto123 on 2007-12-17
> **foxjps said:**
> Hmm I did a full reinstall and it completed successfully however I still receive error 21..at a bit of a loss now. 



Have no idea how to boot Supergrub from a USB drive (I do have one)

Another simple question for you...do you have the external plugged in when doing this? Also, try hitting CTRL+Alt+Del after it gives you the error. In my case it had to have time to load the external, so, using the power button or just shutting it down didn't work right. By hitting the CTRL+Alt+Del combo, the external doesn't shut down fully.

---

### Post by foxjps on 2007-12-17
Yes I had the external plugged in throughout, I'll try that now,...

---

### Post by foxjps on 2007-12-17
No luck :( Right now I only want something that will get me back to Windows.

---

### Post by Presto123 on 2007-12-17
K...this is past me.

---

### Post by foxjps on 2007-12-17
Thanks for your help

---

### Post by dstew on 2007-12-17
Did you get the grub error as the very first thing that happened? Did you get the grub menu, and then the error, or just the error? If you just get an error number, and no explanation, that is a stage 1.5 error. It usually means that when you installed grub, you instructed it to find its stage 2 in a disk that it can no longer find. Usually, this means that the BIOS enumeration of the disks has changed between the time you installed grub, and when you tried to boot it. Sometimes, this can be because you changed the boot order, or plugged/unplugged a USB device or IDE disk. Other mistakes can be made, such as installing grub to a partition instead of to a disk MBR.

To get Windows back, use the Recovery Console on your Windows CD, and issue the fixmbr command, followed by the Windows name of the disk that has the WIndows system on it:```
fixmbr c:
```Of course, this wiil overwrite the grub boot loader, but you can try to install grub again at your leisure.

---

### Post by foxjps on 2007-12-17
Grub error first thing.

---

### Post by dstew on 2007-12-17
OK, let me see if I understand. You booted an Ubuntu LiveCD, and chose to install Ubuntu to an external USB disk. When you got to the part about installing grub, did you choose (hd0)?

---

### Post by foxjps on 2007-12-17
Thanks, to bad I dont have a windows CD haha.

---

### Post by foxjps on 2007-12-17
> **dstew said:**
> OK, let me see if I understand. You booted an Ubuntu LiveCD, and chose to install Ubuntu to an external USB disk. When you got to the part about installing grub, did you choose (hd0)?


I cant say I remember, It's late and i've been trying to fix this for hours.

---

### Post by dstew on 2007-12-17
It can probably be fixed on of two ways. If your WIndows is 98 or XP, you can get a recovery CD from the Microsoft web site. The other way is to use the Ubuntu LiveCD and get your installation sorted. Or, you can sleep on it.

If you want to try to fix it using the LiveCD, the first step is to plug in your external drive, and boot the LiveCD. Open a terminal and issue the command```
sudo fdisk -l
```Post the result to the forum.

---

### Post by foxjps on 2007-12-17
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27c6edcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1277    10253312   27  Unknown
/dev/sda2   *        1277       24322   185105624    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ffde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    5  Extended
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris
ubuntu@ubuntu:~$
```


Dont like giving up :) thanks for your help


Edit: What if your Vista, can you get a recovery CD then? :P

---

### Post by dstew on 2007-12-17
About the recovery console for XP and 98, maybe I am wrong about getting it from Microsoft. I looked a bit, and didn't find it, but I seem to remember if you just want the recovery commands, you can get them somewhere. Vista has its own recovery system, but I doubt if you can get it on-line.

Anyway, from your fdisk output, it looks like sda is your internal IDE drive, and sdb is your external drive, correct? Your IDE drive has two partitions. sda1 is an unknown type, probably a recovery partition for your WIndows system. sda2 is your Windows system. That partition is bootable.

sdb contains your Linux system in the partition sdb1. From the behavior of your system, it seems you installed the grub boot loader into the MBR of sda, which was probably (hd0) during your installation. Because of this, Windows will no longer boot, because grub overwrote the Windows boot loader. This can be fixed by the fixmbr command as I mentioned above (if you can get a recovery console). The grub boot loader will load grub stage 1.5, which is probably on the first sector of the Windows partition sda1, which is reserved for booting. This can be fixed with the fixboot command (if you ever get to a recovery console).

When stage1.5 runs, for some reason it cannot find the sdb disk. I don't know why it cannot find it, but it might be due to an error during installation. We need to do some experiments to see if we can get grub to at least boot the Ubuntu system. If it can, we can probably get it to boot the Windows system too.

One way to see if grub is able to see the sdb disk is to use the grub command line. From a console on the LiveCD system, enter the command```
grub
```This should get you a grub command line that looks like this```
grub>
```On the grub command line, enter the command```
find /boot/grub/stage1
```If it can't find it, then try ```
find /boot.ini
```Post the results.

EDIT:Bedtime, see you tomorrow.

---

### Post by foxjps on 2007-12-18
Got a result on one of those commands..
```

grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)

```

Thanks very much for your help.

---

### Post by dstew on 2007-12-18
This is a good sign. It means that grub can detect its boot directory, and it is on the grub-named device (hd0,0). What is interesting is that the partition (hd0,0) is probably *not* on your IDE drive, since /boot/grub/stage1 is part of an Ubuntu installation, and from your fdisk output it seems that your Ubuntu installation is on sdb, the external drive. In other words, with your current configuration, (hd0) seems to be your external drive, and (hd1) is probably your internal drive. This is because in some systems, the BIOS changes the drive enumeration when the boot order changes, or when a drive is unplugged or plugged in again, and grub gets its drive names from the BIOS enumeration.

So, at least the grub program on your LiveCD can detect the external drive. There does not seem to be any basic incompatability between grub drive-detection-and-mounting routines and your external drive. It is only a matter of configuration.

Since you got a stage 1.5 error ("Error 21" and no further explanation) this strongly suggests that you will need to install grub again. You cannot fix this type of problem by editing the menu.lst file.

To install grub again, in your current configuration, go the the grub command line from a LiveCD boot and issue these commands:```
root (hd0,0)
setup (hd1)
```In your current configuration, this should install the grub boot loader to the MBR of the IDE drive (hd1) configured to point to the grub directory on (hd0,0).Type **quit** to exit grub, and reboot. Let me know what happens.

---

### Post by logos34 on 2007-12-18
..

---

