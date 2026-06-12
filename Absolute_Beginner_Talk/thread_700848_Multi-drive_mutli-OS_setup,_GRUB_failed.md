---
title: "Multi-drive mutli-OS setup, GRUB failed"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by danopia on 2008-02-18
Hi. My problem involves a SATA builtin harddrive and a USB external one... I have two harddrives and use the first SATA one for Windows (a Dell XPS HDD, complete with the Dell partitons) and planned to use the second USB one for Xubuntu.

After installing Xunbuntu via the LiveCD to the USB HDD, I rebooted to that drive and got "Missing operating system". I then tried booting into Windows (SATA) to talk to some friends about the error and to go on Google but got a GRUB error.

I think that GRUB installed to the wrong drive and overwrote the Windows master boot record. To get Windows bootable again, I believe I need to replace GRUB with the Windows MBR

If this is the cause of the error (GRUB being on my Windows SATA drive and not the Linux USB one), then disconnecting the SATA HDD before installing to the USB one should result in GRUB going on the correct drive and therefore be bootable.

Any help restoring the Windows MBR would be appreciated. Thanks in advance.

PS: I don't need a menu of which OS to boot, since the USB HDD is higher on the BIOS's boot list and the power switch on it can be used to select the OS to use.

---

### Post by petersonjacob on 2008-02-18
problem is ur using a drive external on grub i think it has to do something with your boot sequence, so try editing that first

---

### Post by danopia on 2008-02-18
THe bot sequence allows USB, as I said the error I get depends on whether or not the USB device is present. USB Device is #1 on my list. With the USB on I get a "Missing operating system" where nothing happens, but with the USB turned off the SATA kicks in and GRUB gives me an error.

---

### Post by nixeagle on 2008-02-18
Hello, I've been helping danopia on IRC, and when he ran into troubles I asked him to post here. I'm not sure if he is being clear here, but the problem is his mbr is screwed up and he does not know how to restore it, or the ways he was attempting to restore it failed. 

This problem seems to stem from the ubuntu installer screwing up the fact that he did not want the mbr overwritten on the man harddrive.

---

### Post by randy78 on 2008-02-18
> **nixeagle said:**
> Hello, I've been helping danopia on IRC, and when he ran into troubles I asked him to post here. I'm not sure if he is being clear here, but the problem is his mbr is screwed up and he does not know how to restore it, or the ways he was attempting to restore it failed. 

This problem seems to stem from the ubuntu installer screwing up the fact that he did not want the mbr overwritten on the man harddrive.

Just insert your Windows disk and wait until it gets to the first actual options screen, then select R for repair.

Select the drive you wish to enter, type your Admin password and then type:
fixmbr

select ok (or Y) and then reboot.

---

### Post by danopia on 2008-02-18
Now I just need to find my Windwos disk that disappeared a few months ago when I last reinstalled some old PC in my garage.  If someone konws where to downlaod a disc with "fixmbr", please tell me where to get it, otherwise I'll look for my disc tomarrow.

---

### Post by MasterJS on 2008-02-18
And if you want to install Ubuntu correctly to the external hard drive, I have a post on the blog link in my signature. Go there and you'll find it.

---

### Post by randy78 on 2008-02-18
> **danopia said:**
> Now I just need to find my Windwos disk that disappeared a few months ago when I last reinstalled some old PC in my garage.  If someone konws where to downlaod a disc with "fixmbr", please tell me where to get it, otherwise I'll look for my disc tomarrow.

Download SuperGrubDisk here:
[http://linux-live-usb.org/download/Super_Grub_Disk/download/binaries/sgd/cdrom/sgd_0.9588.iso]("http://linux-live-usb.org/download/Super_Grub_Disk/download/binaries/sgd/cdrom/sgd_0.9588.iso")

Burn it to an ISO that is set to bootable, and then follow the instructions for booting Windows :D

---

### Post by danopia on 2008-02-19
randy78, thanks for the link, I had Windows MBR restored within a couple minutes.

Cheers

PS: MasterJS, I skimmed your blog and didn't see your post about USB HDDs and Linux.

---

