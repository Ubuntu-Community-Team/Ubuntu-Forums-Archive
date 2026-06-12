---
title: "fat32 weirdness"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by slipmat on 2007-01-11
Hi there

Probably not the right forum for this kinda problem but here goes...

Last week I blew my SUSE partition away to have a go with Ubuntu Edgy. I have a 30GB fat32 partition I share between Linux and WinXP, mainly consists of music, photos and some TiVo stuff I'm doing a lot of conversion with.

The /Documents directory is "My Documents" in windoze, I mount the partition to /windows/D in Ubuntu and have a symlink in my home directory to the Documents directory. This is where I want to stuff all my movies and photos. The entry for this partition in fstab is as follows:

```
$ grep vfat /etc/fstab
UUID=ACEC-889B  /windows/D      vfat    defaults,umask=007,uid=1000,gid=1000,iocharset=utf8 0       1
```

As in any M$ "My Documents" folder I have the usual My Pictures and My Movies. Even though my local login is the owner of the mounted partition, and I can write to the Documents directory, both the My Pictures and My Movies directories are read only:

```
$ ls -la /windows/D/Documents/
total 176
drwxrwx---  9 xyzzy xyzzy 16384 2007-01-12 16:00 .
drwxrwx---  8 xyzzy xyzzy 32768 1970-01-01 12:00 ..
drwxrwx---  3 xyzzy xyzzy 16384 2006-12-25 20:13 Access Connections
drwxrwx---  2 xyzzy xyzzy 16384 2006-12-25 20:08 Bluetooth Exchange Folder
drwxrwx---  2 xyzzy xyzzy 16384 2006-12-28 17:03 Check Point CCSE NGX study material
-rwxrwx---  1 xyzzy xyzzy    76 2006-12-25 21:10 desktop.ini
drwxrwx---  3 xyzzy xyzzy 16384 2006-12-25 20:23 matt recover
[COLOR="Red"]dr-xr-x--- 28 xyzzy xyzzy 16384 2006-12-25 21:10 Music
dr-xr-x--- 10 xyzzy xyzzy 16384 2006-12-31 20:07 Pictures[/COLOR]
drwxrwx---  5 xyzzy xyzzy 16384 2006-12-28 21:37 tivo
```



I thought it had something to do with the space in "My Pictures" etc, so in Windows I renamed these to Music and Pictures. Still, both of these directories are read-only.

Anyway my quick and nasty workaround was to chmod those directories to give my account write access and I could write some files... for the duration of that session anyway. It all turned to custard when I restored a bunch of files to these directories under Linux. The files existed and were readable even after a reboot, however when I booted into XP the files were missing and XP complained about filesystem inconsistencies, and reccomended a "chkdisk /F". Now the restored files are completely missing and I can see them from either OS. The original stuff is still there.

Also there was a binary file in /Documents called .directory, I think fsck created it, thought that may have been some sort of safety feature so I deleted it, still no difference.

Since FAT32 does not support permissions, what is setting the directory permissions to read-only and how? What is really happening when I change the permissions of a FAT32 directory? And why after I wrote to these directories were my files invisible from XP? I have tried all manners of remounting the partition and stuff in fstab but still I have these problems. Is writing to FAT32 safe if Linux doesn't write the 8.3 filename in the FAT? Am I going nuts? Oh and I can write all I please to the tivo directory with no problems at all. I think the missing file thing may have been a result of modifying the permissions on those directories (?) and the entries were written to some phantom allocation table...

Perhaps the easier fix is to blow it away and make it an ext3 partition and use one of those ext reader thingies in XP.

TIA...

Matt

---

### Post by rccharles on 2007-01-12
> **slipmat said:**
> 
```
$ ls -la /windows/D/Documents/
total 176
drwxrwx---  9 xyzzy xyzzy 16384 2007-01-12 16:00 .
drwxrwx---  8 xyzzy xyzzy 32768 1970-01-01 12:00 ..
drwxrwx---  3 xyzzy xyzzy 16384 2006-12-25 20:13 Access Connections
drwxrwx---  2 xyzzy xyzzy 16384 2006-12-25 20:08 Bluetooth Exchange Folder
drwxrwx---  2 xyzzy xyzzy 16384 2006-12-28 17:03 Check Point CCSE NGX study material
-rwxrwx---  1 xyzzy xyzzy    76 2006-12-25 21:10 desktop.ini
drwxrwx---  3 xyzzy xyzzy 16384 2006-12-25 20:23 matt recover
[COLOR="Red"]dr-xr-x--- 28 xyzzy xyzzy 16384 2006-12-25 21:10 Music
dr-xr-x--- 10 xyzzy xyzzy 16384 2006-12-31 20:07 Pictures[/COLOR]
drwxrwx---  5 xyzzy xyzzy 16384 2006-12-28 21:37 tivo
```



There is a Dos read-only flag.  I assume the read-only flag is implemented in vfat.

To see if the Dos read-only flag is set, go into the Windows command line and try these commands:

dir
attrib

The attrib command will show what flags are set.  It doesn't seem by default attrib will display attributes of directories.  

attrib directoryName 

seems to work.

attrib /s | more

displays everything, but the actual directory name.

help attrib 

will give you some words.

attrib -r 

will get rid of the read-only flag see the help.

Don't know if directories can have read-only flags.  Why don't you look in windows at the two different directories and see if you can see a difference.

Robert

---

### Post by slipmat on 2007-01-12
Thanks Robert

attrib /S /D | find <stuff> worked for me.

The /D switch processes folders when using /S, this was the only way I could see the attributes on directories. Both Pictures and Music were +R and removing the attribute seems to have solved the problem.

Interesting to note that changing the folder permissions in windows GUI makes no difference.

Thanks again for your help!

Matt

---

### Post by rccharles on 2007-01-12
> **slipmat said:**
> Thanks Robert

attrib /S /D | find <stuff> worked for me.



Great!

Nothing like special case within an unique case Windows.  Drive one nuts!

Robert

---

