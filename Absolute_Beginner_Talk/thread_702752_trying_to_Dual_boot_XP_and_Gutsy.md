---
title: "trying to Dual boot XP and Gutsy"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by munoz8 on 2008-02-20
I'm a total n00b trying to dual boot Gutsy and XP. I installed Gutsy first, repartitioned half my harddrive for use by XP, and installed. I then used the livecd to set up Grub for a dual boot with Gutsy as my default. The grub menu comes up with my options, The problem is, the XP option does nothing. I hit enter and it just sits there. The linux option works fine. 

I followed these instructions: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Thanks

---

### Post by Duck2006 on 2008-02-20
In the terminal type

fdisk -l

and

cat /boot/grub/menu.lst

and post the outputs

---

### Post by spiderbatdad on 2008-02-20
could you post your /boot/grub/menu.lst

---

### Post by timbounceback on 2008-02-20
> **Duck2006 said:**
> In the terminal type

fdisk -l

and

cat /boot/grub/menu.lst

and post the outputs

correction; make that ```
sudo fdisk -l
``` instead of ```
fdisk -l
```

---

### Post by Duck2006 on 2008-02-20
> **timbounceback said:**
> correction; make that ```
sudo fdisk -l
``` instead of ```
fdisk -l
```

I some times forget to put the sudo but i assume the person would know to do that.

---

### Post by munoz8 on 2008-02-20
fdisk returns:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3370    27069493+  83  Linux
/dev/sda2   *        3371        6992    29093715    7  HPFS/NTFS
/dev/sda3            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

And cat /boot/grub/menu.lst returns: 

default 3
fallback 0
timeout 10
hiddenmenu

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a316fde9-9d00-4fbd-9d4b-1d5892f19a85 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=a316fde9-9d00-4fbd-9d4b-1d5892f19a85 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title WindowsXP
root (hd0,1)
makeactive


Thanks!

---

### Post by Duck2006 on 2008-02-21
Change the windoze lines from

title WindowsXP
root (hd0,1)
makeactive

To

title WindowsXP
root (hd0,1)
makeactive
chainloaders +1

---

### Post by jcitguy78 on 2008-02-21
quick question what does the 'chainloaders +1' command do? semi-new to ubuntu just trying to break down the code thanks

---

### Post by Duck2006 on 2008-02-21
> **jcitguy78 said:**
> quick question what does the 'chainloaders +1' command do? semi-new to ubuntu just trying to break down the code thanks

The chainloaders +1 passes to the next boot loader ie from grub to the windoze loader

from the grub manual
> 13.3.4 chainloader
— Command: chainloader [--force] file

    Load file as a chain-loader. Like any other file loaded by the filesystem code, it can use the blocklist notation to grab the first sector of the current partition with `+1'. If you specify the option --force, then load file forcibly, whether it has a correct signature or not. This is required when you want to load a defective boot loader, such as SCO UnixWare 7.1 (see SCO UnixWare). 


[http://www.gnu.org/software/grub/manual/grub.html#chainloader](http://www.gnu.org/software/grub/manual/grub.html#chainloader)

---

### Post by munoz8 on 2008-02-21
thanks for the tip. I added the chainloader +1 line (without the 's' I realized) and it helped a bit. It now leaves the Grub screen and displays "Starting up..." but just sits there. Is it possible that I have the loader pointed to the wrong place?

Thanks for the help

---

### Post by Forrest Gumpp on 2008-02-21
munoz8,

You state in your opening post that you installed Gutsy *before* you installed XP.

There is much advice throughout the Forum in threads on this issue of dual booting that XP should be installed first, then Gutsy.  Perhaps this is the source of your problem.

---

### Post by spiderbatdad on 2008-02-21
notice in your menu.lst default is set to 3. this is memtest, not a bootable kernel. edit menu.lst so that default is 0.

---

