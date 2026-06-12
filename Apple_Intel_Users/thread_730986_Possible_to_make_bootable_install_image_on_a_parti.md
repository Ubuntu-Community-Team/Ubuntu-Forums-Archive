---
title: "Possible to make bootable install image on a partition?"
date: 2008-03-21
forum: Apple Intel Users
---

### Post by cooleyj on 2008-03-21
I have a MacBook Air (without the external drive) so I am unable to install directly from the boot CD.  

I have read the forums and I know that people have been having difficulty making a bootable USB drive (one option I tried).  MY QUESTION is whether there is an easy way to image the boot CD to either a separate partition on an external USB drive or to a USB flash drive.

Again, I am not trying to run a full Ubuntu this way; I just want to get a bootable install on one so that I can install onto a partition of my internal drive in my MacBook Air.

So far I have tried just copying everything with finder--this doesn't seem to produce a bootable image.  using "dd" on the command line also doesn't seem to produce a bootable image.

I have rEFIt installed but neither that nor booting with 'option' pressed picks up these partitions as bootable.

I also tried restoring the image to a partition using OS X's disk utility but it always results in an error saying the source image (ubuntu 7.10 alternative install) could not be verified.

Can anyone tell me how to do this from within OS X (please go slowly and give directions as if I were a 5 year old, please!) or just tell me that it isn't possible I would really appreciate it.

Thank you!

---

### Post by cooleyj on 2008-03-24
1 pitiful bump.

---

### Post by mrsteveman1 on 2008-03-27
You can't dd the image because the iso is an iso9660 filesystem which isn't really supposed to go on block devices like USB sticks, and the mac firmware probably wouldn't boot an eltorito image on a usb stick anyway (bios PCs won't either).

What you will have to do is follow one of the bootable usb guides, but it should work, the mac firmware should detect the MBR code on the stick and give you an option to boot from it when you hold option at boot time.

Guide is here: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

Everything in that guide can be done from OS X, except perhaps installing syslinux to the drive, but you can do that from any other machine, windows or linux. There might be OS X binaries for syslinux but i have never used them.

---

### Post by cyberdork33 on 2008-03-27
By all means try the above, but the EFI doesn't like to boot "legacy" operating systems from USB...

---

