---
title: "Error loading operating system"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Enigmaman on 2008-01-24
I have installed Ubuntu and am booting from CD.

I wanted to retain Dual Bootfor XP  but am getting an error message 'Error Loading Operating System' when I to boot.

I can see all the files are still  on the partitioned disk - how can I get to boot into Windows again please?

TIA

---

### Post by hyper_ch on 2008-01-24
start ubuntu and then run those commands and paste the output here:

```

sudo fdisk -l

```

```

cat /boot/grub/menu.lst > ~/Desktop/output.txt

```

(The second one creates an output.txt file on your desktop, so you can more easily copy'n'paste it all)

---

### Post by Enigmaman on 2008-01-24
Hi - and thanks for your swift response.

here is the output:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Enigmaman on 2008-01-24
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$ 


using 'l' not' 1'

---

### Post by Enigmaman on 2008-01-24
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               8       10735    86172660    7  HPFS/NTFS
/dev/sda2   *       10736       19091    67119570   83  Linux
/dev/sda3           19092       19452     2899732+   5  Extended
/dev/sda5           19092       19452     2899701   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Doh I think I got there in the end!

---

### Post by hyper_ch on 2008-01-24
;) still need the menu.lst ;)

---

### Post by Enigmaman on 2008-01-24
Hi again

I entered the code 'cat etc' into the terminal exactly as above but all I can see is an empty text file on the desktop  :confused:

---

### Post by hyper_ch on 2008-01-24
did you type it or copy'n'paste?

---

### Post by Enigmaman on 2008-01-24
I tried copy'n'paste and it didn't  work - so i typed it. 

As far as I can see the menu list is blank - can that be right?
The text file is empty...:(

---

### Post by hyper_ch on 2008-01-24
and if you edit the original one?

```

gksu gedit /boot/grub/menu.lst

```

---

### Post by Enigmaman on 2008-01-24
Yes even with that one - I get a blank page, an empty file. BTW I am booting Ubuntu from CD - it is not installed - is that relevant?

I was trying to fix this myself from a help page I found online - using the last command you gave me but with 'sudo' instead of 'gksu'.

:confused:

---

### Post by hyper_ch on 2008-01-24
well, booting from cd will not show the right path to it...

---

### Post by Enigmaman on 2008-01-24
OK I will now try to work out how to physically install to hard disk:confused:

---

### Post by hyper_ch on 2008-01-24
not necessarily....

do this:

```

mkdir /media/sda2
mount /dev/sda2 /media/sda2
cat /media/sda2/boot/grub/menu.lst > ~/Desktop/output.txt

```

---

### Post by Enigmaman on 2008-01-25
Hmmm it just will not make the directory :(

---

### Post by hyper_ch on 2008-01-25
how comes?

---

### Post by Enigmaman on 2008-01-28
This is what happens...

ubuntu@ubuntu:~$ mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': Permission denied
ubuntu@ubuntu:~$

---

### Post by hyper_ch on 2008-01-29
then use sudo

---

### Post by Enigmaman on 2008-01-31
Used sudo - got this...

ubuntu@ubuntu:~$ sudo mkdir /media/sda2
ubuntu@ubuntu:~$ sudo mount dev/sda2 /media/sda2
mount: special device dev/sda2 does not exist
ubuntu@ubuntu:~$ sudo cat /media/sda2/boot/grub/menu.lst >Desktop/output.txt
cat: /media/sda2/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

