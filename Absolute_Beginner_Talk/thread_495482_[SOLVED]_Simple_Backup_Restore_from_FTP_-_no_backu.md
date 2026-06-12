---
title: "[SOLVED] Simple Backup Restore from FTP - no backups found"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Tybion on 2007-07-08
Using 'Simple Backup Config' 0.10 I ran a full backup to an FTP site (on a Windows XP PC)

The result was like so  ...

[FONT="Courier New"] 
Directory of C:\ftproot\buddha-backup\2007-07-08_15.53.13.894514.Buddha.ful
08/07/2007  03:53 PM               218 excludes
08/07/2007  03:53 PM            29,688 packages
08/07/2007  03:53 PM                 4 ver
[/FONT]

I then ran 'Simple Backup Restore', it displayed the correct FTP location, but reported ...
Error: no backups found in the target directory

Some of the FTP log (while 'Simple Backup Restore' was talking to it) is ...

[FONT="Courier New"]
Jul 08 16:38:59  32  250 Change directory ok  
Jul 08 16:38:59  32  CWD 2007-07-08_15.53.13.894514.Buddha.ful
Jul 08 16:38:59  32  250 Change directory ok  
Jul 08 16:38:59  32  TYPE I
Jul 08 16:38:59  32  200 Type Binary  
Jul 08 16:38:59  32  PASV 
Jul 08 16:38:59  32  227 Entering Passive Mode (192,168,1,2,4,62)  
Jul 08 16:38:59  32  LIST -a
Jul 08 16:38:59  32  150 Opening data connection  
Jul 08 16:38:59  32  226 Transfer complete  
Jul 08 16:39:00  32  PWD 
Jul 08 16:39:00  32  257 "/buddha-backup/2007-07-08_15.53.13.894514.Buddha.ful" is the current directory  
Jul 08 16:39:00  32  CWD /buddha-backup/2007-07-08_15.53.13.894514.Buddha.ful
Jul 08 16:39:00  32  250 Change directory ok  
Jul 08 16:39:00  32  CWD flist
Jul 08 16:39:00  32  550 Path does not exist  
Jul 08 16:39:00  32  PWD 
Jul 08 16:39:00  32  257 "/buddha-backup/2007-07-08_15.53.13.894514.Buddha.ful" is the current directory  
Jul 08 16:39:00  32  CWD /buddha-backup/2007-07-08_15.53.13.894514.Buddha.ful
Jul 08 16:39:00  32  250 Change directory ok  
Jul 08 16:39:00  32  CWD tree
Jul 08 16:39:00  32  550 Path does not exist
[/FONT]

---

### Post by Tybion on 2007-07-10
I fixed this myself -

The job had not completed - there were files missing - this is the full list of files that should be generated ..

[FONT="Courier New"]
-rw------- 1 root root        91 Jul  9 13:11 excludes
-rw------- 1 root root 713260751 Jul  9 13:17 files.tgz
-rw------- 1 root root    680988 Jul  9 13:11 flist
-rw------- 1 root root    363947 Jul  9 13:11 fprops
-rw------- 1 root root     29810 Jul  9 13:17 packages
-rw------- 1 root root         4 Jul  9 13:17 ver
[/FONT]

For some reason things had stuck - there were no message boxes appearing when I clicked 'Save' or 'Backup Now'.  I ended up uninstalling and re-installing Simple Backup and then backing up to a local disk, and everything has worked fine since.

---

