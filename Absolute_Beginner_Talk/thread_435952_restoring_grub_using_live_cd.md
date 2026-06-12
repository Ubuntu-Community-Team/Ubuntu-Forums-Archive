---
title: "restoring grub using live cd"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2007-05-07
i have installed windows which removes grub from MBR.now i want to store grub. is there any way of doing so by running live from ubuntu/kubuntu cd?
i am too much tired of this thing. every time i install windows ,i need to reinstall ubuntu.plz tell me a healthy way of getting out of this problem. don't suggest that install windows first then linux because i do.because of viruses , windows corrupts and i need to reinstall it.

---

### Post by Bachstelze on 2007-05-07
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

Written by myself :p

---

### Post by Wiebelhaus on 2007-05-07
> **HymnToLife said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

Written by myself :p

that's nice bud , thanks for working that up.

---

### Post by u04f061 on 2007-05-07
> **HymnToLife said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

Written by myself :p

thanks for this but i did every thing and got the message that it is installed.still i cant see grub menu

---

### Post by Bachstelze on 2007-05-07
Do you have multiple hard drives ?

---

### Post by u04f061 on 2007-05-07
> **HymnToLife said:**
> Do you have multiple hard drives ?

i have only one drive and one linux partion which is ext3.after installation ,i got one warning which was due to a bug in xfs ............ i don't remember what was it.
then i got message installation complete.

---

### Post by Bachstelze on 2007-05-07
And still, no GRUB menu ? That's very weird... Culd you please paste the output of *sudo fdisk -l* as well as the commands you typed ?

---

### Post by u04f061 on 2007-05-07
> **HymnToLife said:**
> And still, no GRUB menu ? That's very weird... Culd you please paste the output of *sudo fdisk -l* as well as the commands you typed ?

let me give another try with first method.

---

### Post by u04f061 on 2007-05-07
here is result
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         667     5349645    5  Extended
/dev/sda2             668        1461     6377805   83  Linux
/dev/sda3   *        1462        2397     7518420    c  W95 FAT32 (LBA)
/dev/sda4            2398        2429      257040   82  Linux swap / Solaris
/dev/sda5               2         667     5349613+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /mnt/root
root@ubuntu:~# mount -t ext3 /dev/sda2 /mnt/root
root@ubuntu:~# ls /mnt/root
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz

root@ubuntu:~# grub-install --root-directory=mnt/root /dev/sda2
mkdir: cannot create directory `mnt/root/boot': No such file or directory
root@ubuntu:~# grub-install --root-directory=/mnt/root /dev/sda2
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda

---

### Post by Bachstelze on 2007-05-07
You need to put /dev/sda in the last command, not /dev/sda2. If you put the name of a partition, GRUB will be installed on the boot sector of that partition, not on the MBR of the drive.

---

### Post by u04f061 on 2007-05-07
thanks once again. i have done and now rebooting my pc. let us see the result

---

### Post by u04f061 on 2007-05-07
> **HymnToLife said:**
> You need to put /dev/sda in the last command, not /dev/sda2. If you put the name of a partition, GRUB will be installed on the boot sector of that partition, not on the MBR of the drive.
yes it worked. now i can see grub menu.
thank you very much

---

### Post by Bachstelze on 2007-05-07
I guess I'll have to add something about that in the wiki page ;)

---

### Post by u04f061 on 2007-05-07
> I guess I'll have to add something about that in the wiki page
then certainly it would be the best for idiots like me

---

