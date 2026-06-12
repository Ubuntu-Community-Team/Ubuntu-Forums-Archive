---
title: "How do I unmount a floppy drive - Device is busy error!"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by agarwaldvk on 2006-02-24
Hi Everybody

I copy files from floppy to the Desktop on Ubuntu (with reference to scanModem). I forgot to unmount it then. I am trying to do tha now but it says "Device is busy".

How do I unmount my floppy drive now?


I am also attaching herewith the "ModemData.txt" file generated using scanModem. Can someone tell me if that says to me that I can find a driver for this modem from "Linuxant" website. Is "125d..." the modem identifier of mine?

Best regards


Deepak Agarwal

---

### Post by abhaysahai on 2006-02-24
Hi Deepak,
Just make sure that no process is using the flopy drive. 
In most cases yoou might be having a terminal with cd to floppy or a flie browser ( nautilus) open the floppy folder.

man umount::
 Note  that  a  file  system cannot be unmounted when it is busy - for
       example, when there are open files on it, or when some process has  its
       working  directory  there,  or  when  a swap file on it is in use.  The
       offending process could even be umount itself - it opens libc, and libc
       in  its  turn may open for example locale files.  A lazy unmount avoids
       this problem.

Options::
   -f     Force unmount (in case of an unreachable NFS system).  (Requires
              kernel 2.1.116 or later.)

       -l     Lazy unmount. Detach the filesystem from the filesystem  hierarâ
              chy now, and cleanup all references to the filesystem as soon as
              it is not busy anymore.  (Requires kernel 2.4.11 or later.)

Cheers 
Abhay Srivastava

---

