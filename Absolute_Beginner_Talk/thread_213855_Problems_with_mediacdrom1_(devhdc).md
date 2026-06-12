---
title: "Problems with /media/cdrom1 (/dev/hdc)"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by secdroid on 2006-07-11
Hardware in question works perfectly with Fedora Core 3 & Damn Small Linux 3.0, but I'm having problems with my new Dapper.

DVD reader is /dev/hdd and CD burner is /dev/hdc

Neither recorded nor blank media is "seen" in CD burner --
true for K3B, GnomeBaker and automount desktop icon

Both recorded and blank media is "seen" in DVD reader --
true for K3B, GnomeBaker and automount desktop icon

Activity light never shuts off in CD burner when disk
is in drive, whether disk is blank or recorded

/etc/fstab --
...
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
...

~$ ls -l /media
...
lrwxrwxrwx 1 root root    6 2006-07-09 12:14 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-07-09 12:14 cdrom0
drwxr-xr-x 2 root root 4096 2006-07-09 12:14 cdrom1
...

K3B Settings->Configure K3b...->Devices shows
DVD-ROM is /dev/hdd and Burner is /dev/hdc
It "sees" the properties of both devices correctly.
in terms of drive capabilities & formats supported.
It will even load and eject media in /dev/hdc, but
does not "see" media properties or data (if any)

Tried both "sudo k3b" and "sudo gnomebaker" with no better results.

Suggestions on how to troubleshoot /dev/hdc issues?

---

### Post by secdroid on 2006-07-12
Problem solved! 

To paraphrase Freud, sometimes a coincidence is just a coincidence.  ](*,) 
 
Apparently, my CD burner gave its all burning & verifying my Dapper Alternate Install disk.  That operation succeded, but the drive is now dead.

My new Lite-On DVD burner is working fine as /dev/hdc under Dapper.  I was going to make that swap just as soon as I got comfortable with Dapper, but "Murphy rules!"

---

