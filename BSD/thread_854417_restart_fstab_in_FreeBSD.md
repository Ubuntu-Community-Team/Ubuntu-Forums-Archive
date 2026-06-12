---
title: "restart fstab in FreeBSD"
date: 2008-07-09
forum: BSD
---

### Post by mt85m on 2008-07-09
estart fstab
Hello all, I am wanting to know a way to restart the drive mountings. When I edit the fstab file I have to reboot for the changes to take effect?

Is there a command to restart the drive mounting process?

P.S: i think if i do sudo mount -a, this will should do the trick, however, when i did this it gave me an error message saying, permission denied"[tcp] operations:/var/log/ehds/combinedServerLogs: Permission denied"
all the permissions for the mount folders are set to true.

P.S 2:# in case you guys need more info here you go.  Please help as i am completly stuck! 

Device Mountpoint FStype Options Dump Pass#
/dev/da0s1b none swap sw 0 0
/dev/da0s1a / ufs rw 1 1
/dev/da0s1d /var ufs rw 2 2
/dev/da1s1d /clients ufs rw 3 3
/dev/acd0 /cdrom cd9660 ro,noauto 0 0
# {NFS}-->Operations /usr/{src,ports} [HH] 20071204
operations:/usr/guests/src /usr/src nfs rw,tcp 0 0
operations:/usr/ports /usr/ports nfs rw,tcp 0 0
operations:/var/log/ehds/combinedServerLogs /var/log/ehds/combinedServerLogs nfs rw,tcp 0 0

and

usage: fdisk [-BIaipstu] [-b bootcode] [-1234] [disk]
fdisk -f configfile [-itv] [disk]

------------------------------------------------------
/dev/da0s1a on / (ufs, local)
devfs on /dev (devfs, local)
/dev/da0s1d on /var (ufs, local, soft-updates)
operations:/usr/guests/src on /usr/src (nfs)
/dev/da1s1d on /clients (ufs, local, soft-updates)
operations:/usr/ports on /usr/ports (nfs)
Thanks

---

### Post by mt85m on 2008-07-10
come on people...i need a little help here!

---

### Post by cardinals_fan on 2008-07-10
Sorry, but I'm not sure what's going on.  Try posting to the FreeBSD mailing lists.

---

### Post by mt85m on 2008-07-15
when i do mount -a it works for all the commands in the file exept the command that i entered, it gives me a mesaage: Permission Denied.  so its kindaof working but iam missing something and i can not figure out WHAT THE HECK IT IS!!!

---

