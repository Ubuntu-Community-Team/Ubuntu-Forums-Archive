---
title: "No keyboard or monitor install of Ubuntu Server"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by adrianelliott on 2007-08-04
I have an install of slackware 10 on an old PC and want to replace it with ubuntu server edition and use the box as a home router.  

However the box does not have a keyboard (it uses the old skool large connector so i don't have one that fits), it also has no monitor.

Is there any way of doing a fully automatic install, or to ssh in during the install process?

---

### Post by ptillemans on 2007-08-04
The 'no keyboard' requirement is challenging.

For net boots (provided the PC supports it) it must be enabled in the BIOS, very difficult without keyboard. Server class machines typically allow the 'screen' to be redirected to the serial port, but I guess this will not help either.

I would take the disk out of the machine, put it in another machine and use 

debootstrap feisty /wher/ever/it/is/mounted [http://favorite.repo.si..tory/](http://favorite.repo.si..tory/)...

make it bootable with grub.

A very practical way to do this is to use one of the el-cheapo external USB disk drive boxes which sell for around 20$. 

good luck!

---

