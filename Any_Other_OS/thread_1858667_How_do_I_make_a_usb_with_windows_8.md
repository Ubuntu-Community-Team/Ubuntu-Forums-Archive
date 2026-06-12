---
title: "How do I make a usb with windows 8"
date: 2011-10-12
forum: Any Other OS
---

### Post by Sonicrulz12 on 2011-10-12
How can I make a bootable Windows 8 USB on Ubuntu without any DVDS or CDS
" I am not leaving Linux, am going to dualboot "

---

### Post by wolfen69 on 2011-10-12
Install windows 8 in virtualbox [http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/](http://www.addictivetips.com/windows-tips/how-to-install-windows-8-on-virtualbox/) then install the iso to usb [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

### Post by Sonicrulz12 on 2011-10-12
I dont have a CD or DVD drive for this

---

### Post by Frogs Hair on 2011-10-12
The Current version Win 8 is a pre beta developers preview  .

---

### Post by Sonicrulz12 on 2011-10-12
I know

---

### Post by Sonicrulz12 on 2011-10-12
Basically i need a program for ubuntu which lets me write the windows 8 iso to a usb

---

### Post by wolfen69 on 2011-10-12
> **Sonicrulz12 said:**
> I dont have a CD or DVD drive for this

I thought maybe you had the iso on ubuntu, not the disc itself.

---

### Post by oldos2er on 2011-10-12
Moved to Other OS/Distro Talk.

---

### Post by Sonicrulz12 on 2011-10-12
i have a windows 8 iso

---

### Post by Sonicrulz12 on 2011-10-12
so are there any programs to put a windows 8 iso on an ntfs usb with ubuntu

---

### Post by wolfen69 on 2011-10-12
> **Sonicrulz12 said:**
> so are there any programs to put a windows 8 iso on ubuntu?

What is the iso on now?

---

### Post by Sonicrulz12 on 2011-10-12
well i cant get it on an NTFS usb since unetbootin doesnt support ntfs

---

### Post by Linux_junkie on 2011-10-13
have you searched software manager for USB creator utility?

---

### Post by westie457 on 2011-10-13
Have you tried formatting the stick to FAT32, that might work with 'unetbootin'

Otherwise AFAIK the only ways are with a tool provided by Microsoft
or from within Windows itself with 'unetbootin'

---

### Post by mips on 2011-10-13
Try this in WINE [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) as it might work.
Alternatively try this [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) if it works for windows 7 it should/might work for windows 8.

---

### Post by Starks on 2011-10-13
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

Borrow a Windows PC or load in Vbox.

---

### Post by Sonicrulz12 on 2011-10-14
well i found out i didnt have ntfs 3g to open ntfs drivers in ubuntu then i extracted the windows 8 iso to the usb itself but thanks everybody

---

### Post by linuxaddix on 2011-10-16
this should work perfectly for any iso...
[http://liveusb.info/multisystem/install-depot-multisystem.sh.tar.bz2](http://liveusb.info/multisystem/install-depot-multisystem.sh.tar.bz2)
thats what i use to load iso's on usb

---

### Post by Geezanansa on 2012-03-26
> **Sonicrulz12 said:**
> well i found out i didnt have ntfs 3g to open ntfs drivers in ubuntu then i extracted the windows 8 iso to the usb itself but thanks everybody


What is "ntfs 3g" Sonicruiz12?

I too am trying to go for a full clean installation of window8 on a seperate partition from ubuntu partition but on same hdd.

There are many guides that i have tried.  My hunch is something to do with windows8 boot exe.  and windows installer....

Sonicruiz12 Have you successfully managed to boot into windows8 installer?

The closest i have got is loading  windows recovery option screen from usb boot.When it aint been installed yet?) After learning windows installer can only be burnd to disc from a windows machine i tried the recommended windows seven usb download tool to burn .iso to usb on a windows machine
Using unetbootin on a ubuntu machine was even less successful as was using livecd/usb method.
Did use gpart on a livecd/usb version to create a NTFS partition for windows to be installed successfully.(on same hdd as ubuntu 11.10)




Please do provide a step by step guide sonicruiz12 of how to windows 8 on usb.

It appears to be more to it than what folks think or i am missing something.

---

### Post by Geezanansa on 2012-03-26
THis how to mentions ntfs-3g
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html) Thank you mips. 
Older version of unetbootin is used which does recognise ntfs on usb:-)
Hope it works for me too....

---

### Post by Sonicrulz12 on 2012-03-27
Yes mine worked, you have to download the Unetbootin version mentioned earlier, using gparted format the usb to a ntfs, btw you need to install ntfs-3g with the terminal, by typing in code: sudo apt-get install ntfs-3g after that, in unetbootin look for the usb drive name then let unet do all the work, boot up ur pc and it should work nicely

---

### Post by _albatros on 2012-05-06
Hi,
you know some proven ways?
I tried various methods, but unfortunately none of them work :/

---

