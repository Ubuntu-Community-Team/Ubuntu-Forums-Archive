---
title: "yaboot update error"
date: 2007-11-15
forum: Apple PPC Users
---

### Post by Gen2ly on 2007-11-15
Thanks for reading this.  Recently I've been working on my iBook and getting linux running good.  I've created a new kernel but am having trouble updating yaboot.

I've updated to the latest version of yaboot but I'm having trouble with ybin updating open firmware.

"ybin -v" returns:

ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/hda8...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/hda8...
ybin: Installing /etc/yaboot.conf onto /dev/hda8...
ybin: Setting attributes on ofboot...
hattrib: No volume is current; use `hmount' or `hvol'
ybin: Warning: error setting attributes on ofboot
ybin: This is probably bad but we'll ignore it.
ybin: Setting attributes on yaboot...
hattrib: No volume is current; use `hmount' or `hvol'
ybin: Warning: error setting attributes on yaboot
ybin: This is probably bad but we'll ignore it
ybin: Setting attributes on yaboot.conf...
hattrib: No volume is current; use `hmount' or `hvol'
ybin: Warning: error setting attributes on yaboot.conf
ybin: This is probably unimportant so we'll ignore it
ybin: Blessing /dev/hda8 with Holy Penguin Pee...
hattrib: No volume is current; use `hmount' or `hvol'
ybin: Warning: error blessing /dev/hda8
ybin: This is probably bad but we'll ignore it
ybin: Updating OpenFirmware boot-device variable in nvram...


When I reboot yaboot still chooses the previous kernel.  Any ideas what is going on and what I can do?

---

### Post by pxwpxw on 2007-11-16
**Dirk.R.Gently**

ybin needs run as root, as illustrated below, but might be some other problem with the bootstrap partition permissions, check it out manually with hfsutils hmount, parted and mac-fdisk.

```

$ sudo mac-fdisk -l /dev/hda | grep boot
/dev/hda2         Apple_Bootstrap uboot                262144 @ 64       (128.0M)  NewWorld bootblock
/dev/hda12        Apple_Bootstrap untitled               1954 @ 22857699 (977.0k)  NewWorld bootblock

###parted  showa that hda12 is not formatted
$ sudo parted /dev/hda p free | grep boot
 2      32.8kB  134MB   134MB   hfs          uboot     boot 
12      11.7GB  11.7GB  1000kB               untitled  boot 

$ hmount /dev/hda2
hmount: /dev/hda2: error opening medium (Permission denied)

$ hls
hls: No volume is current; use `hmount' or `hvol'

$ sudo hmount /dev/hda2
Volume name is "bootstrap"
Volume was created on Tue Jun 19 13:43:31 2007
Volume was last modified on Fri Nov 16 21:34:06 2007
Volume has 131952640 bytes free

$ sudo hls -l
f  tbxi/UNIX         0      3058 Nov  2 23:01 ofboot.b
f  boot/UNIX         0    153124 Nov  2 23:01 yaboot
f  conf/UNIX         0      1241 Nov  2 23:01 yaboot.conf

$ sudo hvol
Current volume is mounted from:
  /dev/hda2

Volume name is "bootstrap"
Volume was created on Tue Jun 19 13:43:31 2007
Volume was last modified on Fri Nov 16 21:34:06 2007
Volume has 131952640 bytes free

$ humount
$ sudo hvol
No known volumes; use `hmount' to introduce new volumes
$ 


```

---

### Post by Gen2ly on 2008-01-09
thanks for the help pxwpxw.  never did find out what the "issue was".  I ended up updating the system and installing the new yaboot  ( 1.3.14 ) and I was able to install new information to direct to the kernel.

I remember this being a problem back in Edgy that an old yaboot was being used and it's good to find out that yaboot now has a maintainer - [http://yaboot.ozlabs.org](http://yaboot.ozlabs.org).

---

### Post by VidiotGeek on 2008-01-11
Ok, this is attempt #3 at posting my question...so I'll skip all the crap & cut to the chase. I'm trying to re-install Feisty at the end of my internal drive after an attepted dist upgrade to 7.10 hosed my install. The first time I did it, it worked no problem. Now, I think I just successfully installed the OS, setting up the root & swap partitions & all. But when the installer exits, it tells me that it failed to install yaboot, "your system may not be bootable!" ...Well gee, thanks. So I guess I need a good resource for manually installing yaboot on the bootstrap partition of my drive. I'm still learning the Linux command line, despite having bash in OS X for 5+ years--I've managed to avoid using it too much.

---

