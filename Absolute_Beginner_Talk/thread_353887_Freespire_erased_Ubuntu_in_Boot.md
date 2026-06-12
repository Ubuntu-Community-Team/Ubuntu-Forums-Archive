---
title: "Freespire erased Ubuntu in Boot"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by WASHAD on 2007-02-05
Hello;

I am completely new to Linux and have been trying a few options. First was Ubuntu, but I though I might give freespire a try. After installing to another partition, it erased Ubuntu from the boot record (I doubt that I am saying that correctly). 

How I get Ubuntu back without removing either the boot to freespire or to Windows?

Thanks

---

### Post by fktt on 2007-02-05
hmm.. well for starters, do you have some free space still left? and i mean unformated space with that ;)

---

### Post by Lil_Eagle on 2007-02-05
Your Ubuntu is most likely still there, but Freespire's grub-install overwrote the MBR (Master Boot Record).  You can add the entry for Ubuntu in Freespires /boot/grub/menu.lst (or menu.conf, not sure which freespire uses).  Here's how:

Boot Freesipre, then open a terminal and change type: su
You should be prompted for the root password.  Enter the password, assuming ubuntu is on hda1 and freespire is on hda2 (substitue the appropriate if not) type
```
mkdir /ubuntu
mount -t ext3 /dev/hda1 /ubuntu

```
If all goes well, it should mount.  Then you can fire up a text editor and open /ubuntu/boot/grub/menu.lst

Look for the entry for ubuntu, which should say something like this:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```
Copy that section of the file and paste it into freespires /boot/grub/menu.lst.  Make the appropriate changes for your system with the root definitions.  (hd0,0) = hda1, (hd0,1) = hda2
The next time you boot the machine you should see an entry for Freespire and for Ubuntu

---

