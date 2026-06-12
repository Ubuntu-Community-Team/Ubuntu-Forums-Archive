---
title: "GRUB.... making Windows the default boot OS"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Jormanks on 2007-03-14
Hi guys. Well, since i don't have internet *yet* on ubuntu I want to make windows the default OS ... how can I edit the main boot menu so winxp is the default choice?
How can i modifiy the timer?
In Ubuntu can i Do this?
In the boot menu?

Thanks a lot guys, even for reading this.

---

### Post by divague on 2007-03-14
To make windows the dafault choice just edit the /boot/grub/menu.lst at the end of the file you'll see the operating systems, just put windows before the others.
In that same file you can modify the timer.

---

### Post by aidanr on 2007-03-14
open a terminal and use the following commands:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo gedit /boot/grub/menu.lst
```

and change the lines "default" and "timeout", or as divague said, move the windows entry above the others

---

### Post by Jormanks on 2007-03-14
Thanks man.... Divague....you're from Bolivia?
I'm colombian... well, this is no ubuntu stuff, but I being helped for someone geographically so close... man, it does good.

In that file there are a lot of ##... those  "##" mean something?

Also, how can i mount a partition i have in a HD? The thing is that this HD has two partitions, and one is already mounted.....

If i screw the boot file and save it, how can i restore the backup?

Thanks again

---

### Post by aidanr on 2007-03-14
the # means that line is commented out, ie. grub ignores that line, useful for adding in comments

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

you can restore the backup by booting the live cd, mounting the partition and renaming the backed up grub

---

### Post by Jormanks on 2007-03-14
> **aidanr said:**
> the # means that line is commented out, ie. grub ignores that line, useful for adding in comments

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

you can restore the backup by booting the live cd, mounting the partition and renaming the backed up grub

Thanks man, very helpful

Seriously!

Pd:... how i can rename the file?

(Yeah... sorry, I just have it since sunday and can't work it properly without internet)

---

### Post by aidanr on 2007-03-14
> **Jormanks said:**
> Pd:... how i can rename the file?

assuming ubuntu was installed to hda2 (you can see a list of partitions with "sudo fdisk -l")
the commands then to rename the backed up grub once you've booted the live cd would be:
```
sudo mkdir /tmp/temp
sudo mount /dev/hda2 /tmp/temp
sudo mv /tmp/temp/boot/grub/menu.lst.backup /tmp/temp/boot/grub/menu.lst
sudo reboot
```

of course you probably won't need any of this anyway;)

---

### Post by chuckyp on 2007-03-14
The single # in the menu.1st are NOT ignored due to popular belief.  Just change the default boot option counting from 0 down the list to the windows one.  Also count the entry for Other Operating systems as a number as well.  Hopefully this helps you out a little.

---

### Post by Jormanks on 2007-03-14
probably not.... but I've learnt something, and that's the real deal, isn't it?

---

### Post by divague on 2007-03-14
> Thanks man.... Divague....you're from Bolivia?
I'm colombian... well, this is no ubuntu stuff, but I being helped for someone geographically so close... man, it does good.

Yes, i'm from Bolivia

---

### Post by Jormanks on 2007-03-15
> **aidanr said:**
> assuming ubuntu was installed to hda2 (you can see a list of partitions with "sudo fdisk -l")
the commands then to rename the backed up grub once you've booted the live cd would be:
```
sudo mkdir /tmp/temp
sudo mount /dev/hda2 /tmp/temp
sudo mv /tmp/temp/boot/grub/menu.lst.backup /tmp/temp/boot/grub/menu.lst
sudo reboot
```

of course you probably won't need any of this anyway;)

Yeah but i type fdisk -l and this is what it shows

[PHP][B]Disco /dev/sda: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1       19929   160079661   42  SFS
[/B]
Disco /dev/hda: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        3085    24780231    c  W95 FAT32 (LBA)
/dev/hda2            3086        4742    13309852+  83  Linux
/dev/hda3            4743        4998     2056320   82  Linux swap / Solaris

Disco /dev/hdb: 20.0 GB, 20020396032 bytes
255 cabezas, 63 sectores/pista, 2434 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1   *           1        2434    19551073+   7  HPFS/NTFS
[/PHP]

The sda disk is recognized but just the first partition. As you can see, the other one is not in there (no sda2)... so... i tried to mount it anyway (sudo mount /dev/sda2: /FOLDER/ (ntfs), also tried (sfs))... am I typing this wrong or what?

---

### Post by Jormanks on 2007-03-15
arriba arriba!

---

