---
title: "Change ownership on the external USB drive"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by maksym on 2007-04-06
I need to change the ownership of some folders on my external USB drive since I need my proftpd to be able to access them. Proftpd is running under userftp:userftp (User:Group).

External USB drive is mounted as
/media/usbdisk-1/

Assuming that my ftp would be running in:
/media/usbdisk-1/testFolder 
I changed the home directory for userftp to
/media/usbdisk-1/testFolder
Then I tried to make it the owner of it:

--------------------------------------------------------------
max@Haron:~$ cd /media/usbdisk-1/ 
max@Haron:/media/usbdisk-1$ ls -la
total 420
drwx------ 14 max  max  32768 2007-04-06 12:52 .
drwxr-xr-x  5 root root  4096 2007-04-06 12:32 ..
dr-x------ 15 max  max  32768 2004-09-06 06:32 Docs
drwx------  4 max  max  32768 2004-04-17 14:39 film
drwx------  4 max  max  32768 2007-04-05 22:33 FTP
drwx------  2 max  max  32768 2004-04-14 23:01 Max
drwx------  3 max  max  32768 2004-04-18 20:46 movies
drwx------  2 max  max  32768 2007-04-05 22:30 Recycled
drwx------  5 max  max  32768 2004-04-14 23:51 Shared
drwx------  5 max  max  32768 2004-04-15 00:03 System Volume Information
**drwx------  2 max  max  32768 2007-04-06 12:53 testFolder**
drwx------  5 max  max  32768 2007-04-05 21:23 .Trash-max
drwx------  7 max  max  32768 2004-05-07 21:35 UP
drwx------  4 max  max  32768 2004-06-13 15:23 Upload_Temp
**max@Haron:/media/usbdisk-1$ sudo chown -vhR userftp /media/usbdisk-1/testFolder **
changed ownership of `/media/usbdisk-1/testFolder/testFile' to userftp
changed ownership of `/media/usbdisk-1/testFolder' to userftp
max@Haron:/media/usbdisk-1$ ls -la
total 420
drwx------ 14 max  max  32768 2007-04-06 12:52 .
drwxr-xr-x  5 root root  4096 2007-04-06 12:32 ..
dr-x------ 15 max  max  32768 2004-09-06 06:32 Docs
drwx------  4 max  max  32768 2004-04-17 14:39 film
drwx------  4 max  max  32768 2007-04-05 22:33 FTP
drwx------  2 max  max  32768 2004-04-14 23:01 Max
drwx------  3 max  max  32768 2004-04-18 20:46 movies
drwx------  2 max  max  32768 2007-04-05 22:30 Recycled
drwx------  5 max  max  32768 2004-04-14 23:51 Shared
drwx------  5 max  max  32768 2004-04-15 00:03 System Volume Information
**drwx------  2 max  max  32768 2007-04-06 12:53 testFolder**
drwx------  5 max  max  32768 2007-04-05 21:23 .Trash-max
drwx------  7 max  max  32768 2004-05-07 21:35 UP
drwx------  4 max  max  32768 2004-06-13 15:23 Upload_Temp
max@Haron:/media/usbdisk-1$
-----------------------------------------------------------------------------------

chown claims it changed the ownership but in fact it did not..

I thought that something might be wrong with the userftp and how I set it up so I tried to change the ownership to root - just to see if any ownership change would work on that USB drive:

-------------------------------------------------------------------------------
[B]
max@Haron:/media/usbdisk-1$ sudo chown -vhR root /media/usbdisk-1/testFolder [/B]
changed ownership of `/media/usbdisk-1/testFolder/testFile' to root
changed ownership of `/media/usbdisk-1/testFolder' to root
max@Haron:/media/usbdisk-1$ ls -la
total 420
drwx------ 14 max  max  32768 2007-04-06 12:52 .
drwxr-xr-x  5 root root  4096 2007-04-06 12:32 ..
dr-x------ 15 max  max  32768 2004-09-06 06:32 Docs
drwx------  4 max  max  32768 2004-04-17 14:39 film
drwx------  4 max  max  32768 2007-04-05 22:33 FTP
drwx------  2 max  max  32768 2004-04-14 23:01 Max
drwx------  3 max  max  32768 2004-04-18 20:46 movies
drwx------  2 max  max  32768 2007-04-05 22:30 Recycled
drwx------  5 max  max  32768 2004-04-14 23:51 Shared
drwx------  5 max  max  32768 2004-04-15 00:03 System Volume Information
**drwx------  2 max  max  32768 2007-04-06 12:53 testFolder**
drwx------  5 max  max  32768 2007-04-05 21:23 .Trash-max
drwx------  7 max  max  32768 2004-05-07 21:35 UP
drwx------  4 max  max  32768 2004-06-13 15:23 Upload_Temp
max@Haron:/media/usbdisk-1$ 

------------------------------------------------------------------------------------
Again nothing happens. 
The USB drive has Fat32 file system and "max" is the usual user I log as.
I am running Ubuntu 6.10 if that helps

I cannot run the ftp server on my main drive since there is not enough space (it is a laptop), so external drives are the only solution.
Any ideas as to what I am doing wrong or any alternative solution for me???

THANKS!

---

### Post by steve.horsley on 2007-04-06
You can't change the ownership of files or folders on a FAT drive because FAT doesn't store ownership attributes. The ownership of everything on the drive is emulated, and is set by the way it is mounted. So you need to fix up the way the drive gets mounted when it is first plugged in.

A quick experiment shows that the drive gats automounted as being owned by the owner of the desktop when it's plugged in. I can't try to see what happens whe  no-one is logged in without losing this post I'm halfway through. Anyway, I think you need to  unmount the drive and re-mount it by hand. Like this (in my tests, my USB stick was /dev/sdc1 - use the command **mount** to see where it's currently mounted and what device it is:
> steve@StevesPC:~$ mount
----- all my other mount points deldted for clarity -------
/dev/sdc1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
steve@StevesPC:~$ sudo umount /dev/sdc1
steve@StevesPC:~$ sudo mount -o umask=0 /dev/sdc1 /media/UDISK\ 2.0/


---

### Post by maksym on 2007-04-06
Thanks Steve, that helped. Did not know about permissions and Fat 32.

manual mount with umask=0 solved the problem.

=D>

---

