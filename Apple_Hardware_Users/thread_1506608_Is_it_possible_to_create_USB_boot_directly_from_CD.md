---
title: "Is it possible to create USB boot directly from CD image for iBook G4?"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by transmixer on 2010-06-10
My only computer, an HP notebook was broken and back to the factory for repair.
A friend kindly just let me use her old iBook G4 instead, as I really need a computer to work.
But the G4 is just so old that, most recent webpages don't work well in the old safari 1.3.2, it doesn't even support some e-mail websites! Also the Chinese input method is too annoying (yes I'm Chinese). Since it's not possible to install WIN OS on G4, ubuntu for PPC became the only choice for me.

My problem is that, all RW discs I got now are DVD-RW, but G4 can write on CD-RW only, while i really don't want to walk miles for just 1 piece of CD-RW disc. (I'm acting a lamer now, I know that)

Also I've tried to search for a solution for this, but it seems that each solution needs a boot  CD first.

So the question is that, *_is it possible to skip the step of burning a live CD to create a USB boot disk for the iBook G4?_* My goal is to install ubuntu on G4, dual-boot, without burning a live CD.

Any help is appreciated. Thanks!

---

### Post by linuxopjemac on 2010-06-10
yes it works, see [here]("http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1").

---

### Post by transmixer on 2010-06-10
> **linuxopjemac said:**
> yes it works, see [here]("http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1").
Many thanks! I'll try that.

---

### Post by transmixer on 2010-06-10
Sorry there's just more problem.
dd doesn't work properly, always prompts "device busy".
```
$ sudo dd if=~/Desktop/mini.iso of=/dev/disk2s1
dd: /dev/disk2s1: Device busy
```
where disk2s1 is my usb device.
I checked with lsof | grep /dev/disk2s1 and nothing output.

Any further help plz?

---

### Post by linuxopjemac on 2010-06-11
you are working in OSX I presume. Why don't you try it from some Linux box /Linux live environment ? I have no experience in dd-ing from OSX.

PS
That the device is busy could point to the fact that the drive is mounted. Unmount it with Disk Utility or something. In Linux it would be:

```
sudo umount /dev/disk2s1
```

---

### Post by transmixer on 2010-06-11
> **linuxopjemac said:**
> you are working in OSX I presume. Why don't you try it from some Linux box /Linux live environment ? I have no experience in dd-ing from OSX.
It's exactly what i'm trying to do.
The problem here is that, i've got no other available OS but mac os currently, all operations have to be under OS X.
In the link above the author didn't seem to initiate with linux neither. So I guess there's just something wrong here with my computer...

It could be much easier if I can work on a second notebook.:(

Thanks any way!

---

### Post by linuxopjemac on 2010-06-11
umount the USB device and then dd

---

### Post by transmixer on 2010-06-11
It works! :p
I'll try the left steps. Thanks a lot!

---

### Post by transmixer on 2010-06-11
open firmware ok, but can't boot linux.
when trying "boot usb0/disk@1:2,\\yaboot", it prompts can't locate the partition. what does that mean?
seems just not my day, every step gives me a surprise!

---

### Post by linuxopjemac on 2010-06-12
try:
```

boot usb1/disk@1:2,\\yaboot
```

---

### Post by shawnhcorey on 2010-06-12
To determine which drive to boot from, see the section **HOWTO Boot PowerMacs From A USB Drive In Open Firmware** in [HOWTO Create A Bootable USB Drive From An ISO Image For PPC]("http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=85").

---

### Post by transmixer on 2010-06-12
to linuxopjemac: sorry my mistake, I should give all the error information.
in fact I've tried both usb0 and usb1, and usb1 prompts no such file or something like that.

to shawnhcorey: thanks for the information, the page seems useful. i'll check that and see if it solves my problem.

---

### Post by linuxopjemac on 2010-06-12
I would first make the USB drive empty and then dd the iso onto it. I normally (within Linux :( ) use gparted and install a new partition table. This deletes the whole drive. Maybe you can do something similar with Disk Utility. Then I dd it. Hope that helps

---

### Post by bbertram on 2010-06-14
you did the same error here, as i first did on linux (analogously):

sudo dd if=~/Desktop/mini.iso of=/dev/disk2s1

in that way, you ddump to the first partition on the stick. 
Instead ddump to the stick as a whole:

sudo dd if=~/Desktop/mini.iso of=/dev/disk2

but first double check (with mount for example) that its the right device and not one of your harddrives :)

after dd finishes write some 10 seconds.
if you now unplug the stick and plug it in again. it will even be mounted and can be seen in the Finder as
"Debian-Installer/PPC"

---

### Post by bbertram on 2010-06-14
But now my Problem is: As Debian mini.iso works fine, how can I boot some Ubuntu/Xubuntu/Kubuntu iso? at least the boot ... command in open firmware should be different

For four days now I am trying out (x)ubuntu 10.04 boot images without ANY success to even see the boot menu after pressing 'c'.
Xubuntu Desktop is way too big (> 740 MB), I can not even burn it on a 800 MB CD-R.
All other versions just don't reach a linux boot prompt and fall back to booting Mac OS X.
(tried all desktop/alternate X ubuntu/xubuntu combinations, even one of the PS3 images)

There is no such problem with the Debian PPC 5.04 Netinstall iso though. The CD was burned on my Linux PC and boots fine. An older gutsy CD is also detected as a bootable and starts up (with the known Problems listed on the PowerPC FAQ).

It would be fine to have at least ANY up-to-date Ubuntu CD image that can be booted on PowerPC.

the install target:  iBook G3 'Dual USB'

---

### Post by linuxopjemac on 2010-06-15
The Ubuntu mini.iso boots in the same way as Debian does on USB.

```
boot usb1/disk@1:2,\\yaboot
```
or
```
boot usb0/disk@1:2,\\yaboot
```

Via the Ubuntu mini.iso you can opt for a desktop. If you have some sort of a system you can for example go for LXDE by:

```
sudo apt-get install lubuntu-desktop
```

The netinstaller for Ubuntu is here:
[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/)

---

### Post by shawnhcorey on 2010-06-15
> **linuxopjemac said:**
> The Ubuntu mini.iso boots in the same way as Debian does on USB.

```
boot usb1/disk@1:2,\\yaboot
```
or
```
boot usb0/disk@1:2,\\yaboot
```


OpenFirmware uses backslashes as directory separators.

If yaboot is in the root directory, the command is:
```
boot usb1/disk@1:2,\yaboot
```

If it's in the install directory:
```
boot usb1/disk@1:2,\install\yaboot
```

Or use:
```
boot usb1/disk@1:2,\\:tbxi
```

The sequence **\\:** means search the file system for a file with the tag **tbxi**, which is Apple's special tag for boot loaders.

Also, I think the yaboot.conf should be in the same directory as yaboot but I haven't confirmed this yet.

---

