---
title: "Black screen after Ubuntu Splash (10.04) iMac 27&quot;"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by Gervs on 2010-05-02
Hi, guys.

When I run the CD in order to install Ubuntu 10.04 appears a splash screen and after that turn it on a black screen, CD sounds like still working but nothing's happend on my screen. I think it's 'cuz display resolution isn't supported (2560 x 1440). Well, I don't kwon. This just happen with 10.04, with 9.04 or 9.10 everything's cool.

Thanks.
Gervs.

---

### Post by Master Yami on 2010-05-03
I am having the same problem. I try to boot from the 10.04 disc, and see nothing. I know it has booted, since when I press the power button the system shuts down and ejects the disc. I tried using nomodeset option on pressing F6 but that didn't help.

I think it has to do with the ATI graphics, but I'm not sure.

---

### Post by jisaac on 2010-05-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

and [http://ubuntuforums.org/showthread.php?t=1456439](http://ubuntuforums.org/showthread.php?t=1456439)

should help.

---

### Post by linuxopjemac on 2010-05-03
crazy that Canonical dares to call it LTS and the final release has bugs like this...Many people out there using Radeon cards. I think they stick too much to the 6 month's release cycle

---

### Post by linuxopjemac on 2010-05-03
Here some info for you guys:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by binary10 on 2010-05-03
I too am surprised at the release given the number of ATI issues that bounced up within the last RC build, but that aside my old laptop with its GM965 feels a lot snappier with 10.04, I migrated/clean installed from 9.04 to 10.04.

For now though I daren't do too much on my iMac 27 i7 - because of the ATI issues.

I'm sure that things will get sorted.. 8.10 to 9.04 was all fun and games when that got released.

---

### Post by jaggomiken on 2010-11-17
Hi everybody,
I installed Ubuntu 10.04.1 LTS on my iMac 27'' Core i5.

1) I first installed REFIT from pre-installed Mac OS X.
1a) In MacOSX, resize the HFS+ partition with some of apple's disk utilities so that you make space for linux.

2) Then I used ubuntu-10.04.1-alternate-amd64.iso to make a text-only installation into an ext4 partition.
2a) I used "gnu parted" to delete the partitions created in 1a) for hosting linux and I re-created them with "gnu parted" to avoid messing up GPT with sfdisk or fdisk/cfdisk, that don't handle GPT tables.
2b) I told installer to install Ubuntu into the partition created with gparted (so I didn't use the partition editor builtin into the ubuntu installer). Wait some minutes for the installer to copy files and install packages.
3) Then I booted in and got the well known "blank screen" issue of Xorg after the "ubuntu" logo;
4) So a rebooted the system and selected the "failsafe/rescue" grub entry to boot ubuntu in rescue mode (text only);
5) I selected the failsafe X11 session and told the system to use "low graphic mode" only for this session;
6) The network was working, so I installed the fglrx driver for "proprietary hardware drivers"
7) I configured the /etc/default/grub file to append "readon.modeset=0 nomodeset" after each boot entry (but I'm not sure this setting is really mandatory for Xorg to work correctly)
 Then I rebooted and everything works good.

I'm sticking on make the keyboard and mouse work as expected (as in Mac OS X).
Hope this helps.

---

### Post by timblack on 2011-01-02
Just wanted to confirm another case of successfully working around this little bug by following the critically important steps of:

* install refit
* make room for linux using diskutil
* use a text installer
* install grub on linux root partition, not separate boot partition
* sync MBR/GPT using refit's partition tool
* booting the kernel with "radeon.modeset=0 nomodeset" into a recovery shell
* install proprietary ATI drivers, unload the open radeon drivers and update xorg.conf accordingly.

In my case, I have a late 2009 27" iMac with ATI Radeon 4850 (ser. no. ends in 5RU), and am actually running Debian Squeeze. To install the ATI drivers, I followed the instructions at [http://wiki.debian.org/ATIProprietary#Squeeze](http://wiki.debian.org/ATIProprietary#Squeeze).

---

### Post by pelle.k on 2011-01-04
What most other people said. Ubuntu works fine on my iMac27  11.1 (ci5, hd4850). The critical steps are;
[LIST]
[*]make room with diskutil
[*]optional - make sure windows is the last partition, adjust boot.ini if needed
[*]boot ISO with nomodeset and xforcevesa
[*]install grub too root partition (not mbr)
[*]run gptsync from OSX and set ubuntu root bootable
[*]boot with nomodeset and xforcevesa
[*]install propreitay drivers
[*]profit?
[/LIST]
Also, an additional step with kubuntu is to make the apple wireless keyboard paired, by connecting to the net, installing gnome-bluetooth, running bluetooth-applet, and pressing the pin before it (the keyboard pin requester) disappears (it make take quite a few tries...). For that, you may need a second (pc) USB keyboard.
Oh, you can find a osx binary for gptsync [here]("http://redirectingat.com/?id=292X457&xs=1&url=http%3A%2F%2Fwww.mediafire.com%2Ffile%2Fjizonwxymzr%2Fgptsync-0.2.pkg.zip&sref=http%3A%2F%2Fwww.insanelymac.com%2Fforum%2Findex.php%3Fshowtopic%3D177505")

---

### Post by texas.chef94 on 2011-03-18
> **pelle.k said:**
> What most other people said. Ubuntu works fine on my iMac27  11.1 (ci5, hd4850). The critical steps are;
[LIST]
[*]make room with diskutil
[*]optional - make sure windows is the last partition, adjust boot.ini if needed
[*]boot ISO with nomodeset and xforcevesa
[*]install grub too root partition (not mbr)
[*]run gptsync from OSX and set ubuntu root bootable
[*]boot with nomodeset and xforcevesa
[*]install propreitay drivers
[*]profit?
[/LIST]
Also, an additional step with kubuntu is to make the apple wireless keyboard paired, by connecting to the net, installing gnome-bluetooth, running bluetooth-applet, and pressing the pin before it (the keyboard pin requester) disappears (it make take quite a few tries...). For that, you may need a second (pc) USB keyboard.
Oh, you can find a osx binary for gptsync [here]("http://redirectingat.com/?id=292X457&xs=1&url=http%3A%2F%2Fwww.mediafire.com%2Ffile%2Fjizonwxymzr%2Fgptsync-0.2.pkg.zip&sref=http%3A%2F%2Fwww.insanelymac.com%2Fforum%2Findex.php%3Fshowtopic%3D177505")

Could you or someone write a basic step by step procedure for this nomodeset challenge. I am talking from a novice's perspective. Sure would
help.
Thanks

---

### Post by Untitled_No4 on 2011-03-18
> **texas.chef94 said:**
> Could you or someone write a basic step by step procedure for this nomodeset challenge. I am talking from a novice's perspective. Sure would
help.
Thanks

From [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)
> 1. Reboot and in GRUB menu highlight Recovery Mode
2. Edit kernel parameters and add radeon.modeset=0 nomodeset
3. Boot and choose 'Low Graphics Mode' when problems reported
4. Install the proprietary driver using System > Administration > Hardware Drivers

Mind you, 3 and 4 didn't work for me on Kubuntu 10.10 since it didn't start in Low Graphics Mode. I don't think it's related to the fact that I'm using Kubuntu (but I'm not sure).
What I did instead was to connect the machine to a wired internet, then chose command line with network, and once there I installed the ATI drivers manually. To do that you will have to run the following commands:
```
apt-get install fglrx fglrx-amdcccle fglrx-modaliases
```

Once installed run
```
aticonfig --initial
```

and then reboot normally
```
reboot
```

I could then log into the Kubuntu. If you have to change any settings (resolution, brightness) you can always run
```
gksudo amdcccle
```
for Ubuntu, or 
```
kdesudo amdcccle
```
for Kubuntu and change those settings.

---

