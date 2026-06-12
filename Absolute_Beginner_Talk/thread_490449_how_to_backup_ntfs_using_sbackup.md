---
title: "how to backup ntfs using sbackup?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-07-02
I liked the simplicity of Simple Backup and I was wondering if it can be configured to backup my ntfs partition.

I access my ntfs through the ntfs-3g without any problem, but when I tried to add some directories on that partition in the SimpleBackup configuration and I clicked Backup Now, it gives me a process id number, but nothing happens and if I look at the output of .. top -u root ...there is nothing there...

If Simple backup cannot do it, could you kindly mention possible alternatives?

D.

---

### Post by ukripper on 2007-07-03
can you post output of the following :

```
ls -l /media/and your NTFS drive id( such as hda?)
```
 and 
```
ls -l /media
```

---

### Post by jdrodrig on 2007-07-03
> **ukripper said:**
> can you post output of the following :

```
ls -l /media/and your NTFS drive id( such as hda?)
```

I mount my ntfs with the name "trino_win"
jdrodrig@Trino-Ubuntu:/media$ ls -l /media/trino_win
total 3150218
drwxrwxrwx 1 root root       4096 Jun 17  2006 1M30V15
drwxrwxrwx 1 root root          0 Nov 15  2006 33e19532686006bfe4e4254d
drwxrwxrwx 1 root root          0 Nov 15  2006 7c4402abb164187663b70960b4
-rwxrwxrwx 1 root root          0 Jun 16  2006 AUTOEXEC.BAT
-rwxrwxrwx 1 root root          0 Jun 16  2006 CONFIG.SYS
drwxrwxrwx 1 root root     397312 Jun 30 13:13 Config.Msi
drwxrwxrwx 1 root root          0 Jun 18 00:01 Cygwin packages
drwxrwxrwx 1 root root       4096 Feb 25 15:38 DOCS
-rwxrwxrwx 1 root root         81 Nov 24  2006 DVDPATH.TXT
drwxrwxrwx 1 root root      12288 Feb 27 12:42 Display.temp
drwxrwxrwx 1 root root       4096 Jul  2 17:35 Documents and Settings
drwxrwxrwx 1 root root       4096 Nov 30  2006 EVIEWS
-rwxrwxrwx 1 root root          0 Feb  6  2004 IO.SYS
-rwxrwxrwx 1 root root       1600 Jun 24  2006 IPH.PH
-rwxrwxrwx 1 root root          0 Dec 29  2006 Log.txt
drwxrwxrwx 1 root root       4096 Apr 27 01:11 MATLAB6p1
-rwxrwxrwx 1 root root          0 Feb  6  2004 MSDOS.SYS
drwxrwxrwx 1 root root          0 Feb  6  2004 MSOCache
-rwxrwxrwx 1 root root      47564 Aug  3  2004 NTDETECT.COM
drwxrwxrwx 1 root root      36864 Jun 17 23:56 Program Files
drwxrwxrwx 1 root root       4096 Jul 22  2006 RECYCLER
drwxrwxrwx 1 root root          0 Oct 31  2006 Start Menu
drwxrwxrwx 1 root root       4096 May  5 14:43 System Volume Information
-rwxrwxrwx 2 root root        398 Jun 24  2006 T4Metrics.log
-rwxrwxrwx 1 root root     919540 Jun  1 14:26 TB.log
drwxrwxrwx 1 root root          0 Sep  7  2006 TEMP
drwxrwxrwx 1 root root          0 Feb  9  2004 TOSHIBA
drwxrwxrwx 1 root root     126976 Jun 29 15:21 WINDOWS
drwxrwxrwx 1 root root          0 Feb  9  2004 WORKSSETUP
-rwxrwxrwx 1 root root        150 Sep 28  2006 YServer.txt
-rwxrwxrwx 1 root root        226 May 27 14:47 boot.ini
drwxrwxrwx 1 root root       4096 May  9 21:22 cygwin
drwxrwxrwx 1 root root          0 Jun 16  2006 data
-rwxrwxrwx 1 root root 1609551872 Jul  2 18:03 hiberfil.sys
drwxrwxrwx 1 root root          0 Mar 23 09:48 iPAQ
drwxrwxrwx 1 root root          0 May 29 20:43 irstex
-rwxrwxrwx 2 root root    2638744 Mar  6 11:13 latex-beamer-3.06.tar.gz
-rwxrwxrwx 1 root root     250032 Aug  3  2004 ntldr
-rwxrwxrwx 1 root root 1609482240 Jul  2 18:03 pagefile.sys
-rwxrwxrwx 2 root root    2178472 Mar  6 11:14 pgf-1.01.tar.gz
drwxrwxrwx 1 root root       4096 Dec 20  2006 sj646
-rwxrwxrwx 2 root root        232 Mar  5 23:04 sqmdata00.sqm
-rwxrwxrwx 2 root root        232 Mar  6 00:26 sqmdata01.sqm
-rwxrwxrwx 2 root root        232 Mar  6 08:54 sqmdata02.sqm
-rwxrwxrwx 2 root root        232 Mar  6 09:20 sqmdata03.sqm
-rwxrwxrwx 2 root root        232 Mar  6 09:59 sqmdata04.sqm
-rwxrwxrwx 2 root root        232 Mar  6 10:35 sqmdata05.sqm
-rwxrwxrwx 2 root root        232 Mar  6 12:17 sqmdata06.sqm
-rwxrwxrwx 2 root root        232 May  4 10:52 sqmdata07.sqm
-rwxrwxrwx 2 root root        232 May  4 22:42 sqmdata08.sqm
-rwxrwxrwx 2 root root        232 May  4 23:30 sqmdata09.sqm
-rwxrwxrwx 2 root root        232 May  4 23:57 sqmdata10.sqm
-rwxrwxrwx 2 root root        232 May  5 14:31 sqmdata11.sqm
-rwxrwxrwx 2 root root        232 May  5 15:18 sqmdata12.sqm
-rwxrwxrwx 2 root root        232 Mar  5 18:36 sqmdata13.sqm
-rwxrwxrwx 2 root root        232 Mar  5 20:16 sqmdata14.sqm
-rwxrwxrwx 2 root root        232 Mar  5 21:05 sqmdata15.sqm
-rwxrwxrwx 2 root root        232 Mar  5 22:02 sqmdata16.sqm
-rwxrwxrwx 2 root root        232 Mar  5 22:25 sqmdata17.sqm
-rwxrwxrwx 2 root root        232 Mar  5 22:45 sqmdata18.sqm
-rwxrwxrwx 2 root root        232 Mar  5 22:51 sqmdata19.sqm
-rwxrwxrwx 2 root root        244 Mar  5 23:04 sqmnoopt00.sqm
-rwxrwxrwx 2 root root        244 Mar  6 00:26 sqmnoopt01.sqm
-rwxrwxrwx 2 root root        244 Mar  6 08:54 sqmnoopt02.sqm
-rwxrwxrwx 2 root root        244 Mar  6 09:20 sqmnoopt03.sqm
-rwxrwxrwx 2 root root        244 Mar  6 09:59 sqmnoopt04.sqm
-rwxrwxrwx 2 root root        244 Mar  6 10:35 sqmnoopt05.sqm
-rwxrwxrwx 2 root root        244 Mar  6 12:17 sqmnoopt06.sqm
-rwxrwxrwx 2 root root        244 May  4 10:52 sqmnoopt07.sqm
-rwxrwxrwx 2 root root        244 May  4 22:42 sqmnoopt08.sqm
-rwxrwxrwx 2 root root        244 May  4 23:30 sqmnoopt09.sqm
-rwxrwxrwx 2 root root        244 May  4 23:57 sqmnoopt10.sqm
-rwxrwxrwx 2 root root        244 May  5 14:31 sqmnoopt11.sqm
-rwxrwxrwx 2 root root        244 May  5 15:18 sqmnoopt12.sqm
-rwxrwxrwx 2 root root        244 Mar  5 18:36 sqmnoopt13.sqm
-rwxrwxrwx 2 root root        244 Mar  5 20:16 sqmnoopt14.sqm
-rwxrwxrwx 2 root root        244 Mar  5 21:05 sqmnoopt15.sqm
-rwxrwxrwx 2 root root        244 Mar  5 22:02 sqmnoopt16.sqm
-rwxrwxrwx 2 root root        244 Mar  5 22:25 sqmnoopt17.sqm
-rwxrwxrwx 2 root root        244 Mar  5 22:45 sqmnoopt18.sqm
-rwxrwxrwx 2 root root        244 Mar  5 22:51 sqmnoopt19.sqm
drwxrwxrwx 1 root root      28672 Mar  7 23:14 swp40
drwxrwxrwx 1 root root       8192 Jun 17  2006 toshbios.upd
-rwxrwxrwx 2 root root      68129 Mar  6 11:14 xcolor-2.00.tar.gz

And > **ukripper said:**
> can you post output of the following :
[CODE]ls -l /media

gives,
total 40
lrwxrwxrwx 1 root root     6 May 17 04:49 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 May 17 04:49 cdrom0
drwxrwxrwx 1 root root 32768 Jul  2 17:35 trino_win
drwxr--r-- 2 root root  4096 Jun  4 15:12 win_trino

---

