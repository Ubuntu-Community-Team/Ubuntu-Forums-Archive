---
title: "I Found a Bug in Ubuntu"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-17
Hello All !!!

I noticed something that needs improvement.

Hopefully in the Next Ubuntu Version this is going to Get Fixed.


_What is strange is This_:

! have 3 Hard Drives plugged in Ubuntu:

Hard Drive 1:     SATA - with Ubuntu OS Only

Hard Drive 2:     SATA - with: 1 NTFS Partition (All My Files) & 1 FAT32 Partition (Used as Swap)

Hard Drive 3:     IDE ATA - with Windows OS Only.


I have automated the "Mount" of ALL the above Partitions when I Boot my Ubuntu.


Now, I try to access the Partitions from "root", by the Terminal:

root@ubuntu:/#     cd /ntfs_files                       ( < - Accessing: Hard Drive 2 - Partition 1)
root@ubuntu:/ntfs_files#     ls

All Desktop            Drivers                         Songs
Games                   For Evaluation            RECYCLER
Basic Setup           Songs - Maria's

root@ubuntu:/ntfs_files#     cd ..
root@ubuntu:/#     cd /fat32_files
root@ubuntu:/fat32_files#     ls                          ( < - Accessing: Hard Drive 2 - Partition 2)

Linux Files              Funny Pics                  My E-mails

root@ubuntu:/fat32_files#     cd ..
root@ubuntu:/#     cd /ntfs_os
root@ubuntu:/ntfs_os#     ls                                ( < - Accessing Hard Drive 3 - Windows OS)

AUTOEXEC.BAT               IO.SYS                    RECYCLER                               hiberfil.sys
Printer                                MSDOS.SYS           System Volume Information   ntldr
CONFIG.SYS                    NTDETECT.COM   WINDOWS                                 pagefile.sys
Documents & Settings   Program Files        boot.ini

root@ubuntu:/ntfs_os#     cd ..                             ( < - Everything were OK !)

root@ubuntu:/#     umount -a                                ( < - Here I "UNMOUNT" ALL Hard Drives)

umount: /dev: device is busy                                 ( < - THIS IS STRANGE)
umount: /: device is busy                                        ( < - THIS IS STRANGE)

root@ubuntu:/#     cd /ntfs_files
root@ubuntu:/ntfs_files#     ls                                ( < - This is OK, since I "unmounted")
root@ubuntu:/ntfs_files#     ls
root@ubuntu:/ntfs_files#     cd ..

root@ubuntu:/#     cd /fat32_files
root@ubuntu:/fat32_files#     ls                              ( < - This is OK, since I "unmounted")
root@ubuntu:/fat32_files#     cd ..

root@ubuntu:/#     cd /ntfs_os
root@ubuntu:/ntfs_os#     ls                                    ( < - This is OK, since I "unmounted")
root@ubuntu:/ntfs_os#     cd ..

root@ubuntu:/#


_To Explain_:

Since EVERYTHING was OK after I "unmounted" ALL Drives...

... & I could NOT access them (afted I "unmounted"),,,

... Why was there this output after I performed the "unmount":

umount: /dev: device is busy
umount: /: device is busy

_To Conclude_:

To Get an Output AFTER the "unmount" procedure that says that SOME "DEVICE IS BUSY"... 

... makes ME conclude that SOME HARD DRIVE's "unmount" procedure went wrong...

... OR failed to "unmount"...

... It ALSO makes me wonder "which" did NOT "unmount"...

... & makes me want to go check by myself to see "which" did NOT "unmount"...

... ONLY to find that ALL "unmounted" successfully...


Now, Is that considered a BUG or what?

Maybe the Ubuntu Programmers should go & check this !

I know that it is NOT so serious & that Ubuntu is FANTASTIC !!! ...

... But I hope I helped to identify this...

So, I hope I helped... 

Take care,

Dimitris.

---

### Post by vruum on 2006-02-17
this is not a bug, all is as it should be, it failed to unmount the / and /dev because those where busy, umount -a reads /etc/fstab, and tries to unmount every drive mounted, including the ubuntu drives, which can't be unmounted, because ubuntu is using them. The only thing that puzzles me a little is the line /dev: device is busy, do you have a seperate /dev partition?

---

### Post by souteneur3190 on 2006-02-17
next time try bugzilla

---

### Post by mustang on 2006-02-17
[QUOTE=souteneur3190]next time try bugzilla[/QUOTE]

There's nothing wrong with checking here before going to bugzilla. It saves the developer's at bugzilla some of their (precious) time.

---

### Post by dvarsam on 2006-02-17
"vruum" Said:

"The only thing that puzzles me a little is the line /dev: device is busy, do you have a seperate /dev partition?"

How can I see if I have a separate /dev partition?

---

