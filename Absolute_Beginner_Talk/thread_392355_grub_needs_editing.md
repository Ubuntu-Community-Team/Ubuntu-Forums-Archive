---
title: "grub needs editing"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-03-24
Hi there,
              I've done a lot of install and uninstall in my pc(unprofessional i know) with vista and ubuntu and now i cant boot ubuntu up!!!. 

Basically my pc partitions are now--->

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1275 10240000 7 HPFS/NTFS
/dev/hda2 1275 4335 24579072 7 HPFS/NTFS
/dev/hda3 4336 10011 45592470 f W95 Ext'd (LBA)
/dev/hda5 4336 5675 10763264 b W95 FAT32
/dev/hda6 5676 8501 22699813+ 83 Linux
/dev/hda7 8502 9818 10578771 83 Linux
/dev/hda8 9819 10011 1550241 82 Linux swap / Solaris

the ubuntu root partition's on /dev/hda7 as i have mounted and seen all the system files there now. the problem is that i made some partitions with vista and  that i think is the reason i now cant get ubuntu??!!   do i have to edit the grub settings....how do i do that.....i tried using super grub but being a novice got no luck.

can someone please help??:(

---

### Post by bulldog on 2007-03-24
If you see GRUB choose your ubuntu and hit 'e' to edit the line.
Make it point to your hd0,6 partition and try to boot [just read what's displayed]

If the booting is successful you have to modify the menu.lst,but we'll discuss that after you boot into ubuntu.

---

### Post by wannabuntu on 2007-03-24
hi,
    did what you said and at least it now it trys to startup:) !!!! But it then gives me an

/bin/sh:can't access tty; job control turned off(initramfs):( 

what can i do now???

---

### Post by bulldog on 2007-03-24
Mmm.I'm afraid you'll have to edit the fstab as well.

Boot the live cd and mount the partition manually to edit the files.
```
sudo mkdir /mnt/rescue
sudo mount /dev/hda7 /mnt/rescue
gksudo gedit /mnt/rescue/etc/fstab
```

Now modify the fstab to match the linux partitions you have,the numbers listed in fstab are wrong now.
Be careful and only change the numbers,don't forget to save the file.

Now we gonna edit menu.lst
```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
If possible copy it to the forum so I can explain what to change,you can do with fstab too,if you're having trouble with it.

---

### Post by wannabuntu on 2007-03-24
No i think i'll need help on both (to be safe) the fstab is


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=40c2efd5-aec2-406e-817b-4f43881723e7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=ffe96dc8-6950-4c9d-b6b2-c978ee272289 /home           ext3    defaults        0       2
# /dev/hda1
UUID=7C845BE5845BA086 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=1835EE352A02D93D /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=94C6-94A8  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=e5630003-5f8a-4d4c-85c8-9c0d7bf182fb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[/INDENT][/INDENT][/INDENT][/INDENT]


[SIZE="5"]the menu.lst is....[/SIZE]

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet
boot

Thanks for all your time and consideration...

---

### Post by wannabuntu on 2007-03-24
Bulldog....have to go offline till tomorrow.....thanks for all your help will check it out tomorrow......:)

---

### Post by bulldog on 2007-03-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda7
UUID=40c2efd5-aec2-406e-817b-4f43881723e7 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda7
UUID=ffe96dc8-6950-4c9d-b6b2-c978ee272289 /home ext3 defaults 0 2
# /dev/hda1
UUID=7C845BE5845BA086 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2
UUID=1835EE352A02D93D /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=94C6-94A8 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda8
UUID=e5630003-5f8a-4d4c-85c8-9c0d7bf182fb none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

```

This is what the fstab should look,I'm not sure about the UUID,but if you only created partitions and not copied the data to another one,it should be alright.

```
title Ubuntu, kernel 2.6.17-11-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda7 ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet
boot
```

There is a part of the menu.lst you'll have to alter as well,because you didn't copy it here.
Look for this part in the menu.lst```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1e44b9d0-9dff-405d-9fbc-58398539106e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)  <----Change this into (hd0,6)
```

To find the UUID's for your partitions```
ls /dev/disk/by-uuid -lh 
``` so you can check if they are correct in fstab and menu.lst.

---

### Post by wannabuntu on 2007-03-25
Man....cant begin to tell you how much your help is appreciated!!!:) 

will try it out now...

---

### Post by wannabuntu on 2007-03-25
_worked like a dream!!!!_\\:D/ 
                                    Thanks a lot pal...........owe you 1. With people like you around no wonder linux is gaining popularity.=D>

---

