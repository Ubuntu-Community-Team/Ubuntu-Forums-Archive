---
title: "automount with /etc/smb in centos6: kernel: CIFS VFS: cifs_mount failed w/return code"
date: 2013-11-04
forum: Any Other OS
---

### Post by cdtu on 2013-11-04
Hello,

thanks for sharing, it seems to be simple. Could you help me please ?

Why I am not able to mount/ access this Centos6 samba share ? Issue is seen on client:

SERVER
samba.x86_64                      3.5.10-125.el6     
          
[root@6chapter ~]# uname -a
Linux 6chapter.testing 2.6.32-279.el6.x86_64 #1 SMP Fri Jun 22 12:19:21 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

[root@6chapter ~]# testparm 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[printers]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = MYGROUP
    server string = Samba Server Version %v
    security = SHARE
    log file = /var/log/samba/log.%m
    max log size = 50
    cups options = raw

[homes]
    comment = Home Directories
    read only = No
    browseable = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No

[share]
    comment = share
    path = /opt/samba
    read only = No
    directory mask = 0777
    guest ok = Yes
[root@6chapter ~]# 

[root@6chapter ~]# ls /opt/samba/
initialfile  initialfolder
[root@6chapter ~]# ll /opt/
total 8
drwxr-xr-x. 2 root root 4096 Jun 22  2012 rh
drwxr-xr-x. 3 root root 4096 Nov  3 16:32 samba
[root@6chapter ~]# ll /opt/samba/
total 4
-rwxr-xr-x. 1 root root    0 Nov  3 16:32 initialfile
drwxr-xr-x. 2 root root 4096 Nov  3 16:32 initialfolder
[root@6chapter ~]# 





CLIENT:

[root@cl0 6chapter]# grep -v ^# /etc/auto.master 
/misc    /etc/auto.misc
/net    -hosts
/smb    /etc/auto.smb --timeout=300,nonstrict
+auto.master

debug autofs logs:
Nov  4 06:17:30 cl0 automount[1522]: attempting to mount entry /smb/6chapter/share
Nov  4 06:17:30 cl0 automount[1522]: lookup_mount: lookup(program): /smb/6chapter/share -> -nonstrict,fstype=cifs ://6chapter/share
Nov  4 06:17:30 cl0 automount[1522]: parse_mount: parse(sun): expanded entry: -nonstrict,fstype=cifs ://6chapter/share
Nov  4 06:17:30 cl0 automount[1522]: parse_mount: parse(sun): gathered options: nonstrict,fstype=cifs
Nov  4 06:17:30 cl0 automount[1522]: sun_mount: parse(sun): mounting root /smb/6chapter/share, mountpoint /smb/6chapter/share, what //6chapter/share, fstype cifs, options 
Nov  4 06:17:30 cl0 automount[1522]: do_mount: //6chapter/share /smb/6chapter/share type cifs options  using module generic
Nov  4 06:17:30 cl0 automount[1522]: mount_mount: mount(generic): calling mkdir_path /smb/6chapter/share
Nov  4 06:17:30 cl0 automount[1522]: mount_mount: mount(generic): calling mount -t cifs //6chapter/share /smb/6chapter/share
Nov  4 06:17:30 cl0 kernel: CIFS VFS: cifs_mount failed w/return code = -22
Nov  4 06:17:30 cl0 automount[1522]: >> mount: wrong fs type, bad option, bad superblock on //6chapter/share,
Nov  4 06:17:30 cl0 automount[1522]: >>        missing codepage or helper program, or other error
Nov  4 06:17:30 cl0 automount[1522]: >>        (for several filesystems (e.g. nfs, cifs) you might
Nov  4 06:17:30 cl0 automount[1522]: >>        need a /sbin/mount.<type> helper program)
Nov  4 06:17:30 cl0 automount[1522]: >>        In some cases useful info is found in syslog - try
Nov  4 06:17:30 cl0 automount[1522]: >>        dmesg | tail  or so
Nov  4 06:17:30 cl0 automount[1522]: mount(generic): failed to mount //6chapter/share (type cifs) on /smb/6chapter/share
Nov  4 06:17:30 cl0 automount[1522]: dev_ioctl_send_fail: token = 5
Nov  4 06:17:30 cl0 automount[1522]: failed to mount /smb/6chapter/share
Nov  4 06:17:32 cl0 automount[1522]: st_expire: state 1 path /net
Nov  4 06:17:32 cl0 automount[1522]: expire_proc: exp_proc = 140111204247296 path /net
Nov  4 06:17:32 cl0 automount[1522]: expire_cleanup: got thid 140111204247296 path /net stat 0
Nov  4 06:17:32 cl0 automount[1522]: expire_cleanup: sigchld: exp 140111204247296 finished, switching from 2 to 1
Nov  4 06:17:32 cl0 automount[1522]: st_ready: st_ready(): state = 2 path /net
Nov  4 06:18:00 cl0 automount[1522]: st_expire: state 1 path /smb
Nov  4 06:18:00 cl0 automount[1522]: expire_proc: exp_proc = 140111204247296 path /smb
Nov  4 06:18:00 cl0 automount[1522]: expire_cleanup: got thid 140111204247296 path /smb stat 2
Nov  4 06:18:00 cl0 automount[1522]: expire_cleanup: sigchld: exp 140111204247296 finished, switching from 2 to 1
Nov  4 06:18:00 cl0 automount[1522]: st_ready: st_ready(): state = 2 path /smb
Nov  4 06:18:31 cl0 automount[1522]: handle_packet: type = 5
Nov  4 06:18:31 cl0 automount[1522]: handle_packet_missing_direct: token 6, name /smb/6chapter/share, request pid 1743
Nov  4 06:18:31 cl0 automount[1522]: attempting to mount entry /smb/6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: lookup_mount: lookup(program): /smb/6chapter/share -> -nonstrict,fstype=cifs ://6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: parse_mount: parse(sun): expanded entry: -nonstrict,fstype=cifs ://6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: parse_mount: parse(sun): gathered options: nonstrict,fstype=cifs
Nov  4 06:18:31 cl0 automount[1522]: sun_mount: parse(sun): mounting root /smb/6chapter/share, mountpoint /smb/6chapter/share, what //6chapter/share, fstype cifs, options 
Nov  4 06:18:31 cl0 automount[1522]: do_mount: //6chapter/share /smb/6chapter/share type cifs options  using module generic
Nov  4 06:18:31 cl0 automount[1522]: mount_mount: mount(generic): calling mkdir_path /smb/6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: mount_mount: mount(generic): calling mount -t cifs //6chapter/share /smb/6chapter/share
Nov  4 06:18:31 cl0 kernel: CIFS VFS: cifs_mount failed w/return code = -22
Nov  4 06:18:31 cl0 automount[1522]: >> mount: wrong fs type, bad option, bad superblock on //6chapter/share,
Nov  4 06:18:31 cl0 automount[1522]: >>        missing codepage or helper program, or other error
Nov  4 06:18:31 cl0 automount[1522]: >>        (for several filesystems (e.g. nfs, cifs) you might
Nov  4 06:18:31 cl0 automount[1522]: >>        need a /sbin/mount.<type> helper program)
Nov  4 06:18:31 cl0 automount[1522]: >>        In some cases useful info is found in syslog - try
Nov  4 06:18:31 cl0 automount[1522]: >>        dmesg | tail  or so
Nov  4 06:18:31 cl0 automount[1522]: mount(generic): failed to mount //6chapter/share (type cifs) on /smb/6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: dev_ioctl_send_fail: token = 6
Nov  4 06:18:31 cl0 automount[1522]: failed to mount /smb/6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: handle_packet: type = 5
Nov  4 06:18:31 cl0 automount[1522]: handle_packet_missing_direct: token 7, name /smb/6chapter/share, request pid 1801
Nov  4 06:18:31 cl0 automount[1522]: attempting to mount entry /smb/6chapter/share
Nov  4 06:18:31 cl0 automount[1522]: dev_ioctl_send_fail: token = 7
Nov  4 06:18:31 cl0 automount[1522]: failed to mount /smb/6chapter/share
Nov  4 06:18:37 cl0 automount[1522]: st_expire: state 1 path /misc
Nov  4 06:18:37 cl0 automount[1522]: expire_proc: exp_proc = 140111204247296 path /misc
Nov  4 06:18:37 cl0 automount[1522]: expire_cleanup: got thid 140111204247296 path /misc stat 0
Nov  4 06:18:37 cl0 automount[1522]: expire_cleanup: sigchld: exp 140111204247296 finished, switching from 2 to 1
Nov  4 06:18:37 cl0 automount[1522]: st_ready: st_ready(): state = 2 path /misc
Nov  4 06:18:47 cl0 automount[1522]: st_expire: state 1 path /net
Nov  4 06:18:47 cl0 automount[1522]: expire_proc: exp_proc = 140111204247296 path /net
Nov  4 06:18:47 cl0 automount[1522]: expire_cleanup: got thid 140111204247296 path /net stat 0
Nov  4 06:18:47 cl0 automount[1522]: expire_cleanup: sigchld: exp 140111204247296 finished, switching from 2 to 1
Nov  4 06:18:47 cl0 automount[1522]: st_ready: st_ready(): state = 2 path /net
^C




accessing/seeing /smb:

[root@cl0 ~]# ll /smb/6chapter/
ls: cannot access /smb/6chapter/share: No such file or directory
total 0
dr-xr-xr-x 3 root root 0 Nov  4 06:16 .
drwxr-xr-x 3 root root 0 Nov  4 06:16 ..
d????????? ? ?    ?    ?            ? share
[root@cl0 ~]# ll /smb/6chapter/share 
ls: cannot access /smb/6chapter/share: No such file or directory
[root@cl0 ~]# ^C
[root@cl0 ~]# 



Thanks in advance for any input, 

C

---

