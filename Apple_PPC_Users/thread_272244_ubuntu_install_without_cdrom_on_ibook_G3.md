---
title: "ubuntu install without cdrom on ibook G3"
date: 2006-10-05
forum: Apple PPC Users
---

### Post by dave2701 on 2006-10-05
i recently aquired a IBook Dual USB G3 with PPC support. the cdrom drive DOES NOT work.  

is it possible to install ubuntu (ppc version) onto it without the cdrom drive? 

would it be possible to copy the ubuntu iso onto the hard drive and install it from the harddrive? 

or is it possible to install ubuntu from a shared network cdrom drive on ax xp machine? ive done this before installing mandrake a long time ago.

or could i use an external usb harddrive to install it from?


i would love to be able to install it without having to buy new cdrom drive for it.

thanks,
dave

---

### Post by subzero79 on 2006-10-05
take a look here 

[http://doc.ubuntu.com/ubuntu/install/powerpc/](http://doc.ubuntu.com/ubuntu/install/powerpc/)

My thought would be a netboot, also known as PXE boot, for this you will need a server providing TFTP, it can be another computer attached to the network(ie: if you are behind a router). Other method would be bootable pendrive. But i don't know if iboox G3 books supports pendirve booting or PXE booting. If you manage to install GRUB(or LILO) in the first place that would be a great step. With grub you can follow to load the installer initrd and vmlinuz. The installer then downloads the files from internet and install ubuntu.

---

### Post by LettuceandPickles on 2006-10-06
If you have (or have access to) another Mac you can put the iBook in target mode and connect it to the other Mac via FireWire, then boot the other Mac from the install CD and install to the iBook.

---

### Post by LettuceandPickles on 2006-10-06
> **subzero79 said:**
> take a look here 

[http://doc.ubuntu.com/ubuntu/install/powerpc/](http://doc.ubuntu.com/ubuntu/install/powerpc/)

My thought would be a netboot, also known as PXE boot, for this you will need a server providing TFTP, it can be another computer attached to the network(ie: if you are behind a router). Other method would be bootable pendrive. But i don't know if iboox G3 books supports pendirve booting or PXE booting. If you manage to install GRUB(or LILO) in the first place that would be a great step. With grub you can follow to load the installer initrd and vmlinuz. The installer then downloads the files from internet and install ubuntu.

The iBook would support netboot and booting from almost any form of external media, including pendrive.

---

### Post by subzero79 on 2006-10-06
> **LettuceandPickles said:**
> The iBook would support netboot and booting from almost any form of external media, including pendrive.

Good...then with a pendrive  would be the easyest way.

If you manage to load an the ubuntu in live mode with an x86 Cd in the the XP PC, try starting a tftp server, then the ibook would boot from the net and the installer.

---

### Post by dave2701 on 2006-10-06
> **subzero79 said:**
> Good...then with a pendrive  would be the easyest way.


i dont have a pendrive that large.. BUT i do have an external 250G usb harddrive.. would that work?

---

### Post by subzero79 on 2006-10-06
No, you don't get me. You have to make a bootable pendrive that loads the installer. The installer then downloads the necessary packages file to your harddrive and then proceeds to install. If you have to have a broadband connection in order to download the files. It takes about an hour or two with a 1 mbit connection. The size of the bootable pendrive files are about 8 MB.

In order to make a bootable pendrive follow the link for the first reply. There you will find more info.

PD: Try to research for installing grub through OSX(if you have OSX)

---

### Post by dave2701 on 2006-10-06
alright cool.. ill try that..


thanks man!

---

### Post by siepo on 2006-10-06
I actually did install Ubuntu on a G3 Pismo Powerbook without a working optical drive. I used the directions from [http://doc.ubuntu.com/ubuntu/install/powerpc/ch04s04.html#files-newworld](http://doc.ubuntu.com/ubuntu/install/powerpc/ch04s04.html#files-newworld)

or, to be precise, the Breezy version of those instructions.

---

