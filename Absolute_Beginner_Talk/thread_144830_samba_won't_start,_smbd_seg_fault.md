---
title: "samba won't start, smbd seg fault"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by jal on 2006-03-15
Hi, I can't get Samba to start up (breezy).
When I run '/etc/init.d/samba start'
smbd and nmbd log startup messages,
```

[2006/03/15 23:10:15, 0] smbd/server.c:main(798)
  smbd version 3.0.14a-Ubuntu started.
  Copyright Andrew Tridgell and the Samba Team 1992-2004

```
but are not running. smbd mails the following
```

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for pid 8103 (/usr/sbin/smbd).

Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occured.  You are
encouraged to submit this information as a bug report to Debian.  For
information about the procedure for submitting bug reports , please see
http://www.debian.org/Bugs/Reporting or the reportbug(1) manpage.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1212016960 (LWP 8103)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7db1543 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d5b3d9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#3  0x081d353e in smb_panic2 ()
#4  0x081d3660 in smb_panic ()
#5  0x08192ba7 in get_global_sam_sid ()
#6  0x082100a0 in init_guest_info ()
#7  0x08246335 in main ()


```

I've lost the link now, but I did find one brave soul on the forums with a similar problem.  In a leap of  faith he deleted all the files in '/var/run/samba' which fixed his problem. I thought to try the same (see below), but even root doesn't seem to have perms. (Actually, those files are really 'weird', even the OS thinks so.)

Cany anyone help? Please tell me I'm a newb and there is some simple answer.


```

root@acknak:/var/run/samba # ls -lrt
total 8589901862
?rwsrwsrwt  65535 4294967295 4294967295  111411199 Jan  1  1970 locking.tdb
?rw---sr-t  65535   17104895  120193023 4294967295 Jan  1  1970 gencache.tdb
?rwsrws--T  65535    4063231 4294902012 4294967295 Jan  1  1970 connections.tdb
?rwsrwsrwt     78 4294967295  111280205 4294967295 Jan  1  1970 brlock.tdb
root@acknak:/var/run/samba # rm *.tdb
rm: remove write-protected weird file `brlock.tdb'? yes
rm: cannot remove `brlock.tdb': Operation not permitted
rm: remove write-protected weird file `connections.tdb'? y
rm: cannot remove `connections.tdb': Operation not permitted
rm: remove write-protected weird file `gencache.tdb'? y
rm: cannot remove `gencache.tdb': Operation not permitted
rm: remove write-protected weird file `locking.tdb'? y
rm: cannot remove `locking.tdb': Operation not permitted


```

---

### Post by gord on 2006-03-15
are you sure your filesystem isn't corrupted?
```
sudo fsck /dev/<harddrive>
```
repleacing <harddrive> with your partition device node (for example hda1, hda2, hdc2 or whatever)

---

### Post by jal on 2006-03-15
oh crap:cry: , but now you mention it...
I'm at work now, will check when I get home. Thanks.

---

### Post by jal on 2006-03-17
Well! What fun! fsck complained about a missing magic number, fell out of the gui, and *pfft* file system was gone, nevermore, history, randomized bits, dead.
I was somewhat taken aback, let me tell you.
Luckily, an aquaintance had an Ubuntu 5.10 CD, so I can start again afresh.

---

