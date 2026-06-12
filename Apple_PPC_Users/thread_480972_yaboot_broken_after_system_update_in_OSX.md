---
title: "yaboot broken after system update in OSX?"
date: 2007-06-22
forum: Apple PPC Users
---

### Post by TonySmash on 2007-06-22
this happened a couple days ago and i frankly don't remember the exact details (and i'm incredibly afraid to reboot my computer - it may not come back to life!), but after an OSX system update i rebooted my computer and suddenly yaboot was acting all funky. now, i was still able to boot into ubuntu using the apple boot loader (option key at startup), but i'm afraid...

anywho, a while ago i had this problem when i upgraded to tiger, and someone instructed me how to fix the yaboot files and stuff. so, could someone please tell me how to do that again? it would be greatly appreciated!!

---

### Post by pxwpxw on 2007-06-22
funky how?

post the output from these:
```

 sudo nvsetenv boot-device
 sudo mac-fdisk -l
 cat /etc/yaboot.conf

```

---

### Post by TonySmash on 2007-06-22
```
sudo nvsetenv boot-device
``` returned
```
boot-device=/pci@f4000000/ata-6@d/disk@0:2,\\:tbxi
```

```
sudo mac-fdisk -l
``` returned
```
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           28226563 @ 2018     ( 13.5G)  Linux native
/dev/hda4               Apple_HFS Apple_HFS_Untitled_3 29040336 @ 29564768 ( 13.8G)  HFS
/dev/hda5         Apple_UNIX_SVR2 swap                1336187 @ 28228581 (652.4M)  Linux swap
/dev/hda6              Apple_Free Extra                    16 @ 58605104 (  8.0k)  Free space

Block size=512, Number of Blocks=58605120
DeviceType=0x0, DeviceId=0x0

```

and finally...
```
cat /etc/yaboot.conf
``` returned
```
boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda4

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"
```

and by funky i mean when i started the computer, yaboot started running, but i couldnt boot into linux or even osx (it choked and returned some error message when i typed "l" or "x" like i usually do)

---

### Post by pxwpxw on 2007-06-22
Good thanks, I cant see anything wrong there, all looks correct. It should default to booting Linux, and you should see the boot menu even when you use the option key/icon start. Funky, yes.

First, try again starting with the boot menu.

If that is still no good, then get into ubuntu and rerun the yaboot installer, macosx might have interfered with yaboot files or the boot partition.
```

 sudo ybin -v

```
post the result. Check if the boot-device is the same as before. 

That should redo the Apple_Bootstrap configuration. Try another restart.
I dont see how any damage can result.

---

### Post by TonySmash on 2007-06-22
pxwpxw-

i tried rebooting, and actually everything seems fine....mebbe it was just confused that one time :-P this wouldnt be the first time i've made a stupid mistake like this with ubuntu...

thanks a bunch!!!

---

