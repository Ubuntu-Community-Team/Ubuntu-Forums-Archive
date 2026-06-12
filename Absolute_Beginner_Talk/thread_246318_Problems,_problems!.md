---
title: "Problems, problems!"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by sammyboy on 2006-08-29
Hi there, I've installed ubuntu and it works really well, the only snag I'm having is, unsurprisingly with Windows XP. I'm doing a dual boot with partitions and basically I cannot boot windows. I'm getting an Autochk error (canonot find autochk.exe) on a windows blue screen and then I'm getting just a (bad) blue screen saying fatal system error. I've done searches for all of these but they mention something about GoBack. I don't have GoBack installed. Can anyone help (windows won't boot up, it just restarts after the fatal system error - won't even boot in safe mode) The only reason I want to know is that all of my files are currently on windows and I want to put them in my linux section (haven't got enough space on HDD to copy and paste). 
Thanks all!

---

### Post by carverj on 2006-08-29
I think I have had the same problem a while back.
I remember someone mentioning the chainloader in GRUB having something to do with it ! ? !

Here is someone else's code... oops, sorry.They removed the Linux systems here and am trying to fix my dual boot system at home.

```
This is the /boot/grub text:

    ## ## End Default Options ##

    title Ubuntu, kernel 2.6.15-26-amd64-generic
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb1 ro quiet splash
    initrd /boot/initrd.img-2.6.15-26-amd64-generic
    savedefault
    boot

    title Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
    root (hd1,0)
    kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdb1 ro single
    initrd /boot/initrd.img-2.6.15-26-amd64-generic
    boot

    title Ubuntu, memtest86+
    root (hd1,0)
    kernel /boot/memtest86+.bin
    boot

    ### END DEBIAN AUTOMAGIC KERNELS LIST

    # This is a divider, added to separate the menu items below from the Debian
    # ones.
    title Other operating systems:
    root


    # This entry automatically added by the Debian installer for a non-linux OS
    # on /dev/sda1
    title Microsoft Windows XP Home Edition
    root (hd0,0)
    savedefault
    makeactive
    chainloader +1
```

---

### Post by alecjw on 2006-08-29
It does the same thing for me, too.
It's a feature of windows. If it finds an OS which it doesn't like, if it can access the partition on which the OS it stored, it mucks it up. Otherwise, it goes off in a strop and corrupts its own drive and does the blue screen until you uninstall linux. Get over it. Windows does that. You just need to move the hdd to asnother computer and run chkdsk every few days. Then it works. It's the same for OS/2. Windows hates that too.

---

### Post by sammyboy on 2006-08-29
ok while that might be a good idea to move the hard drive. I'm using a laptop so it's not as simple as it sounds! I do NOT want to uninstall Linux i know Xp is a pain but i just want to be able to move my files or do I have to wait until microsoft decide to let everyone know how NTFS works so I can write to it as well.

---

### Post by xyz on 2006-08-29
Take a look here for a HOWTO: NTFS with read/write support using the NEW ntfs-3g (easy & safe method)
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

