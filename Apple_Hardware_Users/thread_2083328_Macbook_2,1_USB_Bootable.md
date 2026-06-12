---
title: "Macbook 2,1 USB Bootable"
date: 2012-11-12
forum: Apple Hardware Users
---

### Post by valroadie on 2012-11-12
Hello, 
I have a macbook 2,1 running Ubuntu 12.04 LTS. 
The problem I have is it is not recognizing my USB stick when rebooting trying to boot the OS I have put on the stick. 
I have used unetbootin and startup disk creator, following the instructions to a T. I have tried with 5 different OS's including Backtrack5, Debian, Ubuntu, Fedora and Opensuse. 
I was wondering if anyone had any insight, or has this similar problem? Thank you!

---

### Post by jlangvand on 2012-11-12
I have a Macbook 7,1, and have never been able to boot "natively" from a USB. I think the integrated boot menu only checks USB (and FireWire) media for OsX.

But you CAN boot from USB using Plop Boot Manager. Burn the ISO on a CD, boot from the CD with your USB device plugged in, and choose to boot from USB. I have a weird issue where the internal keyboard won`t work in the Plop menu, though. But any USB keyboard works. This can probably be fixed by tweaking the Plop ISO.

---

### Post by valroadie on 2012-11-12
Ah ok, sounds good. I will see how this goes, but for now the reason I want to boot from a USB stick is because I have no blank cds/dvds haha. 

BUT! When one should come up I suppose I could try it, other ideas are wanted in the mean time. 

Thanks jlangvand.

---

### Post by gwjvan on 2012-11-16
I have a MacBookPro2,2 and I have not been able to get it to boot from USB. Apparently this model just plain doesn't like to boot from external drives (including USB flash drives).

I was able to learn a little trick to resize partitions and create a new 2 gigabyte partition on the hard drive, then tell grub to boot from an iso image on that new partition. A nice thing about this is that you can instantly try out new iso images, and they load faster than off of USB/CD.

If you google around you should be able to find tutorials on how to do it, unfortunately it looks like when I installed 12.10 on this machine it erased my grub configuration file- but you should just be able to insert a menu uption into grub with the hard drive identifier, and the iso filename. If you install from the iso off of the hard drive, you will have to unmount the partition with the live iso image right before committing the install (after going through the preliminary steps of the installer), then it will automatically re-mount it to read the iso file for installation material.

---

### Post by valroadie on 2012-11-19
That sounds like a viable option. You wouldn't happen to have a link on how to do this? I have looked around for Hard drive partition software but haven't found anything in the likes of what you are talking about.
EDIT: I have used Gparted, but to my avail I cannot resize my primary partition /dev/sda2 which is the one I want to resize. Any ideas on how to resize the primary partition?

---

