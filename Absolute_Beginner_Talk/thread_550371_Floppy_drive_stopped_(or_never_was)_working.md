---
title: "Floppy drive stopped (or never was) working"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-09-13
I'm fixing a Ubuntu Feisty Fawn 7.04 computer at the moment, and it appears the floppy drive is not working.

Is it even pluged in you ask? Yes, I opened it up and double checked it myself.

How do you know its working you say? The BIOS won't pass to the HDD if a floppy disk is in ("non-system disk in place, please remove and strike any key"). That way I know the floppy is working.

[SIZE=5]**FSTAB**[/SIZE]
My /etc/fstab is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c667030a-1df4-44ab-9bfa-944d1747e9bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7f28f70b-9117-432f-881e-d1d2917ce364 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=def1194c-0dff-41a4-a652-82bfeb0d69f5 /home/vmware    ext3    defaults        0       2
# /dev/sda6
UUID=3a40562e-e914-4a6b-9c7f-8919dbd35941 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
[SIZE=5][B]MODPROBE
[/B][/SIZE]I've tried:
```
modprobe floppy
```and it returns nothing.

[SIZE=5]**MOUNT**[/SIZE]
I've also tried:
```
mount /dev/fd0
```and it returned:
> mount: /dev/fd0 already mounted or /media/floppy0 busy
[SIZE=5]**LS -LA**[/SIZE]
```
ls -la /media/floppy0
```> total 8
drwxr-xr-x 2 root root 4096 2007-08-11 14:03 .
drwxr-xr-x 4 root root 4096 2007-08-11 14:36 ..
[SIZE=5]**FDUTILS**[/SIZE]
Lastly:
```
sudo aptitude purge fdutils && sudo aptitude install fdutils
```does nothing.

What else can I do or what are your thoughts?

---

### Post by Happy_Man on 2007-09-13
See what is in /etc/modprobe.d, and if there is a floppy or whatever something related to that in there. If so, run ```
modprobe -v <whatever is found>
```, then reboot for good measure.

---

### Post by Johnny3 on 2007-09-13
Did you install KFloppy in Synaptic Package Manager? If floppy shows on dasktop right click and unmount it. Make shore it not right protected. 
Johnny3
Gainesville Fl

---

### Post by altonbr on 2007-09-13
> **Happy_Man said:**
> See what is in /etc/modprobe.d, and if there is a floppy or whatever something related to that in there. If so, run ```
modprobe -v <whatever is found>
```, then reboot for good measure.

This is all I found in /etc/modprobe.d:
> " ============================================================================
" Netrw Directory Listing                                        (netrw v98)
"   /etc/modprobe.d
"   Sorted by      name
"   Sort sequence: [\/]$,*,\.bak$,\.o$,\.h$,\.info$,\.swp$,\.obj$
"   Quick Help: <F1>:help  -:go up dir  D:delete  R:rename  s:sort-by  x:exec
" ============================================================================
../
./
arch/
aliases
alsa-base
arch-aliases
blacklist
blacklist-framebuffer
blacklist-modem
blacklist-oss
blacklist-scanner
blacklist-watchdog
bluez
ibm_acpi.modprobe
ipw3945
isapnp
libpisock9
lrm-video
nvidia-kernel-nkc
options
toshiba_acpi.modprobe

---

### Post by altonbr on 2007-09-13
> **Johnny3 said:**
> Did you install KFloppy in Synaptic Package Manager? If floppy shows on dasktop right click and unmount it. Make shore it not right protected. 
Johnny3
Gainesville Fl

I'm using Gnome and KFloppy is for formatting is it not?

---

### Post by Johnny3 on 2007-09-13
I just use it to check the floppy. Can you boot to a floppy in your BIOS. That would tell you if it was a hardware problem.
 Johnny3
Gainesville Fl

---

### Post by Johnny3 on 2007-09-13
Sorry I meant can you boot to the a drive. I use my WD life Guard disk. Does it show up in Device Manager?
Johnny3
Gainesville Fl

---

### Post by altonbr on 2007-09-13
Well shoot, I can only SSH in at the moment... I'll test some boot floppies next time.

PS: A floppy is sitting there at the moment for testing.

---

### Post by altonbr on 2007-09-20
Is there anything I can do via SSH? I don't have access to the computer and therefore a boot floppy.

---

### Post by altonbr on 2007-09-21
I'm sitting at the computer now with an extra floppy drive in-hand and Smart Boot Floppy in the computer. I rebooted it and it loaded the Smart Boot Floppy screen. That means the floppy drive is not broken.

I tried to read the floppy in Ubuntu 7.04 Feisty however, and it fails to do anything after double clicking "Floppy" in "Computer".

What are some command lines tools I can use to read the floppy or to reinstall the floppy packages?

```
lillian@rooster:~$ **mount /dev/fd0**
mount: /dev/fd0 already mounted or /media/floppy0 busy
lillian@rooster:~$ **sudo umount /dev/fd0**
umount: /dev/fd0: not mounted
lillian@rooster:~$ **ls -la /media/floppy0**
total 8
drwxr-xr-x 2 root root 4096 2007-08-11 14:03 .
drwxr-xr-x 4 root root 4096 2007-08-11 14:36 ..

```

---

### Post by altonbr on 2007-09-21
This isn't an upgrade by the way, it's a fresh install of Feisty. I can't reinstall Feisty either because it's running a important server in VMware.

---

### Post by altonbr on 2007-10-02
I ended up getting it working a week or so ago in recovery mode (aka: root) and produced this script/thread: [http://ubuntuforums.org/showthread.php?t=557137](http://ubuntuforums.org/showthread.php?t=557137)

I still don't know why it won't work for users however.

---

