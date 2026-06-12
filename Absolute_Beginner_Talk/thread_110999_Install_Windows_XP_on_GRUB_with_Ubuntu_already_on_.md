---
title: "Install Windows XP on GRUB with Ubuntu already on it"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Koobi on 2006-01-01
hi,
i've decided to install windows on a 5GB partition for three reasons:
1. so that i can play games...havent played a single one in over a year and emulators are too much for my P3 733 MHz PC to handle
2. lack of USB support. i need to use my USB port sometimes and this is just not possible with ubuntu.
3. i miss Adobe Photoshop. The Gimp and The GimpShop are great but Photoshop is amazing.


i've got breezy on GRUB and i already have allocated one partition for windows and i'd like to know how i can install XP without messing anything up in GRUB while keeping Ubuntu.

i'm not really a beginner...been using Ubuntu on Gnome for just over a year now but i didn't know where else to post this thread.

---

### Post by Nomearod on 2006-01-01
I think that if you install Windows now, it will uninstall Grub, but I don't know how could you install Grub again...

---

### Post by pbb on 2006-01-01
Not really an answer to your question, but I recently REinstalled Windows XP on a GRUB-multiboot system, and it left GRUB untouched.

Back in the old days, Windows 98 did used to remove any multiboot functionality, but XP seems to respect it?

---

### Post by steve.horsley on 2006-01-01
Before you install Windoze, take a copy of your partition table. Then you can put it back if necessary. To copy the partition table to a file:
```
sudo dd if=/dev/hda of=/CopyOfBootSector bs=512 count=1
```
To put it back again:
```
sudo dd if=/CopyOfBootSector of=/dev/hda bs=512 count=1
```

If you need to configur GRUB by hand to boot Windoze, the file to edit is /boot/grub/menu.lst. Here is a copy if the lines that add Windoze to my boot options. I use ME, but I assume the same would work for XP. You may need to change the partition number to suit your setup - my Windoze is on hda3:
```
title windows
root (hd0,2)
chainloader +1

```

I am not aware of any problems with USB in Ububntu. I succesfully use all of these through USB: Scanner, Printer, Camera, Pen-Drive, MP3-player, external hard disk, mouse. Three of those use USB-2.0.

I believe you can run Photoshop under wine in Ubuntu.

---

### Post by Koobi on 2006-01-03
i just wanted to show you an output of what my HDD looks like. i plan to install Windows XP on /dev/hda8

i'm confused about /dev/hda10
i know it's ext3 because i formatted it with qtparted but it shows up as HPFS/NTFS. any idea why that is?

> 
koobi@koobi:~ $ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         653     5245191    b  W95 FAT32
/dev/hda2             654        6451    46572435    f  W95 Ext'd (LBA)
/dev/hda3   *        6452        7476     8233312+  83  Linux
/dev/hda5             654        1928    10241406    b  W95 FAT32
/dev/hda6            1929        3330    11261533+   7  HPFS/NTFS
/dev/hda7            3331        3840     4096543+   7  HPFS/NTFS
/dev/hda8            3841        5115    10241406    7  HPFS/NTFS
/dev/hda9            5116        5383     2152678+   7  HPFS/NTFS
/dev/hda10           5384        6403     8193118+   7  HPFS/NTFS
/dev/hda11           6404        6451      385528+  82  Linux swap / Solaris
koobi@koobi:~ $ df -T -h
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3    7.8G  6.4G  1.1G  86% /
tmpfs        tmpfs    125M   16K  125M   1% /dev/shm
tmpfs        tmpfs    125M   13M  113M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hda5     vfat    9.8G  5.8G  4.1G  59% /media/windows
/dev/hda1     vfat    5.0G  3.5G  1.6G  69% /media/windows1
/dev/hda6     ext3     11G  9.7G  412M  96% /mnt
/dev/hda7     ext3    3.9G  2.8G  900M  76% /media/linux7
/dev/hda8     ntfs    9.8G  8.3G  1.6G  85% /media/windows8
/dev/hda9     ext3    2.1G  1.3G  721M  64% /media/linux9
/dev/hda10    ext3    7.7G  6.1G  1.3G  84% /media/linux10







[QUOTE=steve.horsley]
I am not aware of any problems with USB in Ububntu. I succesfully use all of these through USB: Scanner, Printer, Camera, Pen-Drive, MP3-player, external hard disk, mouse. Three of those use USB-2.0.

I believe you can run Photoshop under wine in Ubuntu.[/QUOTE]

that's funny...my USB devices don't seem to work on 5.10...maybe i should give it another try. i've been trying to hook up my webcam but it doesn't respond.

regarding Wine/x, i can't use any emulators because the PC is so slow. i tried Wine and some other emulators to try using Trillian once and i could barely use the system since it was so choppy.


steve.horsley, i will give your suggestion a try...but how would i edit my /boot/grub/menu.lst from the output i have quoted?

thanks for your time.

---

### Post by Sef on 2006-01-03
The problem with your webcam would be a lack of drivers for it.  Start a new thread for it, and you should be able to get some help for it.

---

### Post by Koobi on 2006-01-04
[QUOTE=Sef]The problem with your webcam would be a lack of drivers for it.  Start a new thread for it, and you should be able to get some help for it.[/QUOTE]
thanks, i'll have a look at that :)

but does anyone know how i would edit my /boot/grub/menu.lst from the output i have quoted?

---

### Post by Koobi on 2006-01-26
i looked around a bit and thought i had it figured out. i installed windows and edited my GRUB's menu.lst but it didn't work so i had to use the rescue disk to install GRUB and wipe the MBR again.

i hope someone can guide me this time. this is what my HDD partitions look like:
```

koobi@koobi:~ $ sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    b  W95 FAT32
/dev/hda2             654        6451    46572435    f  W95 Ext'd (LBA)
/dev/hda3            6452        7476     8233312+  83  Linux
/dev/hda5             654        1928    10241406    b  W95 FAT32
/dev/hda6            1929        3330    11261533+   7  HPFS/NTFS
/dev/hda7            3331        3840     4096543+   7  HPFS/NTFS
/dev/hda8            3841        5115    10241406    7  HPFS/NTFS
/dev/hda9            5116        5383     2152678+   7  HPFS/NTFS
/dev/hda10           5384        6403     8193118+   7  HPFS/NTFS
/dev/hda11           6404        6451      385528+  82  Linux swap / Solaris

```



i've got XP installed on /dev/hda8

is this what a part of my /boot/grub/menu.lst should look like?

```

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Microsoft Windows XP
root            (hd0,6)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

```

because if i understand correctly, GRUB reads the disks beginning with 0 and not 1...that what i read while searching for GRUB on google...so please let me know if i've got it right...it's really a problem to have to use the windows rescue disk when i need windows and then use the ubuntu rescue disks to get back to ubuntu.

thanks for your time.







:edit:
i tried both, (hd0,6) and (hd0,7) but they both gave me this error when i selected them via GRUB on boot:
> 
Error 11: Unrecognized device string


---

### Post by Sutekh on 2006-01-26
[QUOTE=Koobi]

title           Microsoft Windows XP
root            (hd0,6)
savedefault
makeactive
chainloader     +1
[/QUOTE]
Windows doesn't like not being on the first partition on the drive, so you'll need to trick it into thinking this using the **map** command.

[QUOTE=GRUB Manual]
If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see map), like this:

     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)

This performs a virtual swap between your first and second hard drive. 
[/QUOTE]
You can do the same for partitions too.
So try this
```

title           Microsoft Windows XP
root            (hd0,6)
savedefault
makeactive
[b]map (hd0,0) (hd0,6)
map (hd0,6) (hd0,0)[/b]
chainloader     +1

```
This should make Windows believe its loading from (hd0,0) instead of (hd0,6)

---

### Post by Koobi on 2006-01-27
hi Sutekh, thanks for your time.

i reedited menu.lst to use this:
```

title           Microsoft Windows XP
root            (hd0, 6)
savedefault
makeactive
map             (hd0,0) (hd0,6)
map             (hd0,6) (hd0,0)
chainloader     +1

```


but i still recieve the error:
```

Error 11: Unrecognized device string

```

---

### Post by Sutekh on 2006-01-27
Ok then.  Perhaps its best to re-install GRUB, because its very good at detecting settings for itself.

Try having a look at these links to re-install GRUB

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") (re-installs GRUB again)

[HOWO: Restore GRUB if you MBR is messed up]("http://ubuntuforums.org/showthread.php?t=24113")

---

### Post by Koobi on 2006-01-27
Sutekh, do you suppose i'd be better off if i just installed XP on hda1 instead?
it's not much of a hassle for me anyway because i haven't fully set up my XP install anyway. i don't mind reinstalling on hda1

---

### Post by StratosL on 2006-01-27
Hi there. I followed the first link, 
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

When trying to download the super grub disk, I got a message about a VBS:Davinia malware. Is this supposed to happen?

Thanks,

Stratos

---

### Post by Sutekh on 2006-01-28
[QUOTE=Koobi]Sutekh, do you suppose i'd be better off if i just installed XP on hda1 instead?
it's not much of a hassle for me anyway because i haven't fully set up my XP install anyway. i don't mind reinstalling on hda1[/QUOTE]

You could if you wish.  However you'll still need to fix GRUB.  Whenever Windows is installed after Ubuntu, it will remove GRUB from the MBR and replace it with its own bootloader.  

GRUB is very good at detecting other operating systems, so if you re-install GRUB it should detect Windows XP where it is.  Installing it on hda1 probably won't make things easier.

---

### Post by Sutekh on 2006-01-28
[QUOTE=StratosL]Hi there. I followed the first link, 
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

When trying to download the super grub disk, I got a message about a VBS:Davinia malware. Is this supposed to happen?

Thanks,

Stratos[/QUOTE]

I have not had any experience witht he Super GRUB Disc.  I'm sure its fine, if it was a problem that section would probably have been removed from the wiki page.  

I'd suggest using the Ubuntu installation CD to put GRUB back.  I've used it once and it wasn't hard to do.

---

### Post by Koobi on 2006-01-29
i did try re-installing GRUB and trued update-grub as well but nothing worked.

i installed windows on hda1 and then re-installed GRUB with root set to (hd0, 0) and that seemed to do the trick.


thanks :)

---

