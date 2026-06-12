---
title: "Uninstalling a duplicate Linux Mint OS"
date: 2013-02-15
forum: Any Other OS
---

### Post by Hodevah on 2013-02-15
Hi. I have a duplicate Linux Mint OS on my laptop. I think the way that the duplicate OS was inadvertantly installed was when I was having some initial trouble installing Mint and had inadvertanty installed it on /dev/sda10. The operating system that I am currently using (and have been using regularly) is on /dev/sda11. According to Boot-Repair the boot loader is installed on same. 

I have done a bit of research and found some information that pertains to Ubuntu. Currently, the OS I am using is Mint 14 (Nadia). 

(1)One of the links that I have gone to is here> askubuntu.com/questions/13052/how-to-remove-a-duplicate-ubuntu-installation-without-ruining-os-boot-menu. 

That gave me some information but I dont think all that I was looking for. 

(2) I was wondering that if I undertook the following procedure that I might be safe without ruining GRUB. 
 (a) remove the offending duplicate Mint via Terminal command (that is one of the sub-queries I have in needing to know how to do);

(b) remove offending kernals related to that duplicate install and update GRUB;

(c) boot into Windows to delete that offending partition and renew it with ext4 to eventually merge with the current Mint that I am using via  KDE Partition Mgr;

Please provide some feedback to the above  idea of mine if this would indeed resolve this issue. Otherwise if not, please keep reading for additional information.  ;)

Perhaps some useful information is posted below:


```
user@user-Aspire-5749 ~ $ sudo os-prober
[sudo] password for user: 
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda10:Linux Mint 14 Nadia (14):LinuxMint:linux
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda3:Windows 7 (loader):Windows2:chain
```In the above Terminal cmd, it shows what OS I am using; however, as you can see below there is an extra image/kernal installed as well. 

This is also evidenced by what GRUB displays during boot up. Sorry, but I dont know the procedure to attain to show you what GRUB shows me during boot up. Suffice it to say, that there are 2 Linux Mints (not including 2 Advanced Options for each one).

```
user@user-Aspire-5749 ~ $ dpkg -l | grep linux-image-
ii  linux-image-3.5.0-17-generic          3.5.0-17.28                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  ***linux-image-extra***-3.5.0-17-generic    3.5.0-17.28                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.5.0.17.19                               amd64        Generic Linux kernel image
 
```You can see that I have an extra image/kernal installed. I dont believe this is for the ADVANCED OPTIONS that are available via GRUB. Though I might be wrong. Please correct me if I am wrong.

I have GRUB CUSTOMIZER installed, though I dont know how to present a .txt file of its output here for viewing so that you can see the fact that there is an inadvertant and extra MINT install on my HDD. 


```
user@user-Aspire-5749 ~ $ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda11      59189412 6289352  49893392  12% /
udev             1937376      12   1937364   1% /dev
tmpfs             779956    1032    778924   1% /run
none                5120       0      5120   0% /run/lock
none             1949888      88   1949800   1% /run/shm
none              102400      12    102388   1% /run/user

```Again, it (the extra image and kernal) resides on /dev/sda10.

[IMG]http://i.imgur.com/64SpB5k.png[/IMG]

I can boot up into /dev/sda10 if you want to review/return information from there if you want to help ascertain anything needed to resolve this issue.  ;)

---

### Post by Hodevah on 2013-02-15
never mind. I found a program called os-unistaller made by a ubuntu user. What  a great program. 

issue solved.

---

