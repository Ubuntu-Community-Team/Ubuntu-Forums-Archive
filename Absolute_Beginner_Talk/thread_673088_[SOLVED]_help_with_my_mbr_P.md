---
title: "[SOLVED] help with my mbr :P"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-01-20
Ok i have broken my mbr again and i am trying to repair it with a ubuntu 7.10 livecd (i dont have a windows disc) with the help of the tutorial from [arsgeek]("http://www.arsgeek.com/?p=3340") ([http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)) but its not working for me i put the last command from the tutorial in the terminal and i get a list of options

_Command i put in_
```
sudo ms-sys –mbr /dev/sda1
```

_Code i get out_
```
Usage:
        ms-sys [options] [device]
Options:
    -1, --fat12     Write a FAT12 floppy boot record to device
    -2, --fat32nt   Write a FAT32 partition NT boot record to device
    -3, --fat32     Write a FAT32 partition DOS boot record to device
    -6, --fat16     Write a FAT16 partition DOS boot record to device
    -l, --wipelabel Reset partition disk label in boot record
    -p, --partition Write partition info (hidden sectors and drive id)
                    to boot record
    -m, --mbr       Write a Windows 2000/XP/2003 MBR to device
    -9, --mbr95b    Write a Windows 95B/98/98SE/ME MBR to device
    -d, --mbrdos    Write a DOS/Windows NT MBR to device
    -s, --mbrsyslinux    Write a public domain syslinux MBR to device
    -z, --mbrzero   Write an empty (zeroed) MBR to device
    -f, --force     Force writing of boot record
    -h, --help      Display this help and exit
    -v, --version   Show program version
    -w, --write     Write automatically selected boot record to device

    Default         Inspect current boot record

Warning: Writing the wrong kind of boot record to a device might
destroy partition information or file system!

```


so as im using xp or at least i have an xp partition on my hardrive i selected "m-" but it just comes back with bash command not found:confused:


anyhelp would be much appreciated

---

### Post by mikeyphi on 2008-01-20
Perhaps the command should be:

sudo ms-sys -m, --mbr /dev/sda1

---

### Post by kamitsukai on 2008-01-20
no im afraid not i just get the same list as above... :)

---

### Post by ajgreeny on 2008-01-20
Try just one of the two options;  either -m or --mbr, not both.

---

### Post by mikeyphi on 2008-01-20
I've had a look at the source website: [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

Seems to me that the MBR should be written to sda and not sda1

Have a read of that website and see what you think!

---

### Post by kamitsukai on 2008-01-20
ok i tried this "sudo ms-sys -m /dev/sda1" and what i got is below but im a bit of a newb so i dont really know what it wants me to do?

```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$ 

```

---

### Post by kamitsukai on 2008-01-20
> **mikeyphi said:**
> I've had a look at the source website: [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

Seems to me that the MBR should be written to sda and not sda1

Have a read of that website and see what you think!

hmmm im not sure as i said im new to this so...basically i need to be told what to do:lolflag:

---

### Post by mikeyphi on 2008-01-20
I think its trying to tell you that the MBR is written to the disk and not a partition....have a look at the website from my previous post.

---

### Post by kamitsukai on 2008-01-20
well i had a look and tried what you said but it still comes back with the same thing...but maybe "ajgreeny" was right because i got somthing from that even if i dont know what it means :P

---

### Post by mikeyphi on 2008-01-20
> **kamitsukai said:**
> ok i tried this "sudo ms-sys -m /dev/sda1" and what i got is below but im a bit of a newb so i dont really know what it wants me to do?

```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$ 

```

So - what happens if you enter:
sudo ms-sys -m /dev/sda

---

### Post by kamitsukai on 2008-01-20
Ok thanks for all the help iv'e just decided to reinstall ubuntu on its own and use that :P thanks anyway!

---

