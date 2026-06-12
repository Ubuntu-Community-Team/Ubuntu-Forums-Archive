---
title: "Install issue"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Primaris on 2006-12-18
I have installed Ubuntu using the 6.10 version.  The live portion of the CD runs fine.  The install was done to the "Largest available free space" and I chose only default options.  The install appeared to complete successfully.  However when I boot all I get is **noting **after the BIOS splash screens finish up.  So does anyone know how to get past this black screen (BSOD?!)?
[LIST]
[*]DFI Lanparty nF4 SLI-DR
[*]AMD 64 3000
[*]1Gig RAM
[*]Maxtor 250 GB HD
[*]Installed on to 50 GB partition
[/LIST]

---

### Post by dbbolton on 2006-12-18
i would use the live cd to check whether the filesystem and grub are set up correctly

---

### Post by macogw on 2006-12-18
```

sudo -s
mount /dev/hda /mnt
chroot /mnt
apt-get install grub-install
```
see if you can do that from the LiveCD.  Grub may not have installed correctly.  If it still doesn't work, redo everything up to chroot, then 
```

gedit /boot/grub/menu.lst
```
and tell us what it says in there

---

