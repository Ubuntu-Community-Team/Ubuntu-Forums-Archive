---
title: "grub error 22"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by draze on 2008-02-04
i didn;t really do uch.  i was using ubuntu like before. everything was perfect. i was charging my ipod.

then my mom need windwos so i restarted and booted to windows...worked perfect too. then i restarted again.

i get grub error 22

last time i solved it by booting into repair mode on WinXP cd repairing some file in c:/WINDOWS.  i forgot what file....so if you could tell me what file was it. or any oher way too bring everithng back to normal

---

### Post by draze on 2008-02-04
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bdb0bdb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ca20c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           59782       60801     8193150   83  Linux
/dev/sdb2           59591       59781     1534207+  82  Linux swap / Solaris
/dev/sdb3           55766       59590    30724312+   7  HPFS/NTFS
/dev/sdb4               1       55765   447932331    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 1023 MB, 1023933952 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
/dev/sdc2              11         124      915705    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by draze on 2008-02-05
ok i found the way to fix it....i fixed it through windows repair mode and typed in C:/Windows/fixmbr


then i restart...it doesn't give me the grub error, but it doesn't give me the window where i have to choose the operating system so it just boots me into WinXP. How to bring my Ubuntu back?

---

### Post by bumanie on 2008-02-05
> sudo grub--> enter
find /boot/grub/stage1
and post the output

---

### Post by dstew on 2008-02-05
You will need to reinstall grub. To do it properly, you need to boot a Live CD system since grub will not be able to deal with the mounted disk of the hard disk system. After you boot the live CD, open a terminal, and type grub. That should get you the grub> prompt. At the grub prompt enter```
find /boot/grub/stage1
```Based on your fdisk output, my guess is that it will return (hd1,0). Whatever it returns, use that as the argument for the root statement```
root (hd1,0)
setup (hd0)
quit
```Then reboot. You should get the grub menu now. If any grub menu items do not work, we can edit the grub menu file to fix those problems too.

---

### Post by bumanie on 2008-02-05
Sorry forgot to add to boot via live cd. Then put in codes.

---

### Post by draze on 2008-02-05
i am on the school network now. but i will post it as soon as i come home.

---

### Post by draze on 2008-02-05
grub> find /boot/grub/stage1
 (hd1,0)

grub>

---

### Post by bumanie on 2008-02-05
Boot with the live cd again. In terminal type
sudo grub --> enter
>grub root (hd1,0)
>grub setup (hd1)
>grub quit
Remove live cd and reboot. All going well, your system should be back to normal.

---

### Post by draze on 2008-02-05
well i did all you said. i've seen some stuff going on in my terminal. it seemed to have worked.

but it didn't

it stayed the same as it was before.

but i tried something else...i set my bios to boot up from my second hard drive wihc is 8GB linux 1.5swap 30just space in ntfs and everything else is just space too in ntfs.
it gave me the:

Error 17:Cannot mount seleceted partition

so i switched back to my win XP HDD...

i got the same problem...it keeps booting to windows.

---

### Post by Biggy on 2008-02-05
Download [Super Grub Disk]("http://supergrub.forjamari.linex.org/?section=download") and fix the errors. i got the same problem and i fixt

---

### Post by bumanie on 2008-02-05
That should have worked. Try super grub disc, it is a good tool and handy to have around anyway. If super grub disc doesn't work, post the output of 
> sudo gedit /boot/grub/menu.lst

---

