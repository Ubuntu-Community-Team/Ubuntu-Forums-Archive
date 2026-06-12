---
title: "K42JC and Ubuntu 11.04 - No sound at all"
date: 2011-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bangrobe on 2011-06-07
Hi everybody
I'm using Asus K42JC and Ubuntu 11.04 ( just installed Linux Mint 11 replace for Ubuntu). I updated to latest Kernel, and now I can't hear any sound in Ubuntu. No system sound, no music. I already checked all sound preference, Alsa Mixer and they aren't mute. I followed instruction on this link : [http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966) but the problem still exist. 
So anyone could give me a help? Thanks so much.:)

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by megamendung on 2011-07-12
i have same problem (on same laptop series), please help. here is link alsa-info.
> [http://www.alsa-project.org/db/?f=d764877a9d4cf0502f95f5fe8118656eb9ed8cf9](http://www.alsa-project.org/db/?f=d764877a9d4cf0502f95f5fe8118656eb9ed8cf9)

thanks in advance...

---

### Post by lidex on 2011-07-15
> **megamendung said:**
> i have same problem (on same laptop series), please help. here is link alsa-info.


thanks in advance...

The edit you made to alsa-base.conf is not for your codec chip so remove it  and run the alsa-info script again.
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line;
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Save. Close. Reboot.

---

### Post by plasticinedean on 2011-07-22
I had the same issue. I fixed it by updating the kernel to the latest rc. The kernel im using is v3.0-rc7, with full working sound, system, music, movies etc. To update the kernel download from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc7-oneiric/) the files:

linux-headers-3.0.0-0300rc7_3.0.0-0300rc7.201107120911_all.deb

linux-headers-3.0.0-0300rc7-generic_3.0.0-0300rc7.201107120911_i386.deb

linux-image-3.0.0-0300rc7-generic_3.0.0-0300rc7.201107120911_i386.deb

Install them in the above order and reboot for working sound (in grub just choose to boot from the new kernel). Note that i have only tried this for 32bit. You can try the amd64 generic header and image if your on 64bit, but i have no idea whether it will work.

---

