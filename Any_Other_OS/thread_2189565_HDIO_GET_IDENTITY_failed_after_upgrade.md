---
title: "HDIO_GET_IDENTITY failed after upgrade"
date: 2013-11-23
forum: Any Other OS
---

### Post by hlyh1230 on 2013-11-23
hi,i'm using BodhiLinux which is based on Ubuntu 10.04,recently i wanted to install software that requires updated version, but i couldnt do so in terminal using dist-upgrade.
So i tried risky way by tweaking the source.list ...

now inside the source.list the ubuntu version is  Quantal ,yet when i check using "lsb_release -a"  command it still shows i'm at ubuntu 12.04 LTS

throughout this long way, i got problems with apt-get update,upgrade,-f install ,bla bla bla  ....

when i finally settled those problems and reboot, i just couldnt get past the login page.

when i look at the boot progress in terminal one of the line reads "HDIO_GET_IDENTITY failed" error.
And it just went on this loop like forever...

*My Bodhi is installed on external HDD,which I have made 4 partitions:
ext4 for "/" , ext4 for "/boot" , swap & ntfs for the remaining free space.

and now i have another new problem: GRUB menu doesnt show up when boot..
since my "/boot" & "/" location are at different partition, how do i chroot ?
then regarding HDIO problem,till now i didnt see any workable solution....can anyone here share yr opinion?

i just want to save the clean reinstall option as my last resort..
thx..

---

### Post by coffeecat on 2013-11-23
*Thread moved to **Other OS/Distro Support**.*

---

