---
title: "Gnome: Hard drive Icons disapeared..."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by shidao on 2007-09-01
Hii peps!!!

I'm using ubuntu 7.04, and I don't know why, after a update (i think...) my hard drive icons and links in locations are disapeared!!

my "sudo fdisk -l" output are:
```

Disco /dev/hda: 81.9 GB, 81964302336 bytes
255 cabeças, 63 setores/trilha, 9964 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1   *           1        9964    80035798+   c  W95 FAT32 (LBA)

Disco /dev/hdb: 122.9 GB, 122942324736 bytes
255 cabeças, 63 setores/trilha, 14946 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hdb1   *           1       14945   120045681    c  W95 FAT32 (LBA)

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabeças, 63 setores/trilha, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1               1        3824    30716248+   b  W95 FAT32
/dev/sda2            3825        4462     5124735   83  Linux
/dev/sda3            4463        4589     1020127+   5  Estendida
/dev/sda4            4590       38913   275707530    b  W95 FAT32
/dev/sda5            4463        4589     1020096   82  Linux swap / Solaris

```

I have mounted one (the sda1) with "sudo mount /dev/sda1" and I can acess the data, but the icons or shortcuts are nothing being showed in desktop..

Can anyone help me?!!

thanks a lot to all

---

### Post by benfindlay on 2007-09-01
Try pressing alt+f2 and typing ```
gconf-editor
```

Press enter and go to />>apps>>nautilus>>desktop and look for "volumes_visible" this should be ticked to make your icons visible

Hope this helps!

---

### Post by MenZa on 2007-09-01
Could you paste the output of *cat /etc/mtab* and *mount*? Thanks!

---

### Post by shidao on 2007-09-01
> **benfindlay said:**
> Try pressing alt+f2 and typing ```
gconf-editor
```

Press enter and go to />>apps>>nautilus>>desktop and look for "volumes_visible" this should be ticked to make your icons visible

Hope this helps!

The "volumes_visible" was ticked....
but thanks anyway..

---

### Post by shidao on 2007-09-01
> **MenZa said:**
> Could you paste the output of *cat /etc/mtab* and *mount*? Thanks!
Sure...
Here it is..

For mtab:
> 
/dev/sda2 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hdc /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=andre 0 0


And the mount didn't work... "cat /etc/mount"....

Hope this help to find out what is going on...

thanks guys!

---

### Post by MenZa on 2007-09-01
Ah, just "mount". You don't need to cat anything :). And it appears your devices aren't mounted, which could explain for the lack of icons showing up.

---

### Post by shidao on 2007-09-01
> **MenZa said:**
> Ah, just "mount". You don't need to cat anything :). And it appears your devices aren't mounted, which could explain for the lack of icons showing up.

:) Ok, thanks, here it is..:

```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=andre)

```

---

