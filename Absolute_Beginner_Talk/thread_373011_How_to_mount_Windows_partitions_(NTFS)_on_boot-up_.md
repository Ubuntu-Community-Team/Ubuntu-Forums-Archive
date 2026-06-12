---
title: "How to mount Windows partitions (NTFS) on boot-up : I can not start XP now"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by stevand on 2007-02-28
I followed [http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

and I was able to see mounted XP data .... after I restarted ... machine to do some work in Windows .. I could not start

Please HELP if you have any advise

---

### Post by Tsen on 2007-02-28
At what point during the boot does it fail, and does it give a GRUB error?

---

### Post by skale on 2007-02-28
Do you mean boot into windows?  If so, then add:

```
# Windows XP
title Windows XP
hd(<disk no. - 1>,<partition - 1>)
makeactive
chainloader +1
```

to your /boot/grub/menu.lst text file.

---

### Post by stevand on 2007-02-28
it starts with the windows logo and then I get a blue screen ....
with the small icon "windows is starting up ..." however it hangs like this ... for some time ...

the icon is
the same one that ususally says use Alt+Del or something similar .... to invoke login screen with login and password

---

### Post by stevand on 2007-02-28
Scale
I see the window the black one where it says
linux ubuntu 386
....
....
XP-Windows

and then I chhose XP-Windows ... and it starts ... but it does not giev me Ctrl+ALt-DEL to login screen

---

### Post by stevand on 2007-02-28
Scale
how do I get to do this ...

# Windows XP
title Windows XP
hd(<disk no. - 1>,<partition - 1>)
makeactive
chainloader +1

to file 
/boot/grub/menu.lst

---

### Post by stevand on 2007-02-28
I found the /boot/grub/menu.lst text file.

the last few lines are 


title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1



so what I sholud  write  ? ..... 
when I did procedure as in  How to mount Windows partitions (NTFS) on boot-up, and allow all users to read only
I had sda2 instead of hda1

---

### Post by Tsen on 2007-02-28
EDIT: Nevermind, there doesn't seem to be a problem with your menu.lst, so the problem is likely elsewhere.

---

### Post by stevand on 2007-02-28
I can not start XP in windows OS ... while whenever I boot in Linux I mount on the boot my windows partition .....

I followed the procedure and I do not understand why I can not get back my XP to work ....
I did not change anything else ..... and it is read only so it should not interefere with XP

---

### Post by stevand on 2007-02-28
Finally I was able to get XP to work ONCE I disconnected external heard drive
I just unplugged it ... and I got windows back...

---

