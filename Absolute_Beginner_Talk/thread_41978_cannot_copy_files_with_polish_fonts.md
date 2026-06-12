---
title: "cannot copy files with polish fonts"
date: 2005-06-15
forum: Absolute Beginner Talk
---

### Post by Chopin on 2005-06-15
Hi there,

I new in Linux stuff, so far everything went ok (with little help from ubuntu.pl forum guyz), but finally I got stuck with coping files with polish fonts (like: &#261;&#281;&#347;&#263;) from cdrom to my fat partition - I copy other files on this partition but no one with polish font in name - it says that there is invalid parimeter). What's weird I can copy them to my Desktop (but even from Desktop cannot copy it to fat partition when I store all my docs.) Where is the problem? I think it is not fonts coz I can create dirs. with name incl. polish fonts. I also downloaded all possible locals, and other fonts (inlc. times n.roman - cd was burned in Win98). Also I reached this thread:
[polish font problem in KDE](http://ubuntuforums.org/showthread.php?postid=113602#poststop) 

ps aha instead polish fonts I have ? (question marks) - I tried to copy it even from terminal - with the same result...

---

### Post by GTvulse on 2005-06-15
The problem is related to codepage conversion.

Off the top of my head, Polish MS Windows uses cp1251 as its default codepage, which is closest to ISO-8859-2 (or is it the Baltic encoding cp1256 ~ ISO-8859-6?). Try mounting your FAT partition with  the option "nls=iso-8859-2", that should work. Same goes for the CD, but rather use "nls=utf8" because the Joliette filesystem used by MS to allow long file names on CDs uses the UCS2-LE UNICODE  vector encoding (UTF-8 and UCS2-LE are not identical, but it works, sort of).

If you have already mounted the FAT partition, you can use ```
sudo mount -o remount,nls=iso8859-2 /mnt/your_windows_mount_point
```

EDIT

OK. out of curiosity I checked the contents of /lib/modules/2.6.10-5-k7/kernel/fs/nls/ and found out that **there is** support for some MS Windows codepages. I guess you could use "nls=cp1251" as an argument to the mount command.

---

### Post by Chopin on 2005-06-16
Thank you for your answ. dradul - you are codepages expert!!! I changed encoding by remounting both hda and cdrom but unfortunate it did not solved my problem - stil polish fonts on cd are (?) and still I cannot copy them. Hm maybe my fstab can help: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /dane           vfat    umask=000        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

any other ideas ?

---

### Post by GTvulse on 2005-06-16
Nahh! I'm not an expert, and memory fails... :-)

I checked some codepage lists I have around and realized I mixed up the real codepage names in my mind. The Windows codepage you want to use is cp1250 (Slavic/Central European Languages), which is the equivalent (but not equal!) to ISO-8859-2. Another codepage to try is ISO-8859-4 (not 6) that corresponds to Baltic languages (I know that Polish is quite unique in that respect and sometimes neither ISO codepage fits exactly).

Try this:

```

    .
    .
    .
/dev/hda3       /dane           vfat    user,noauto,nls=cp1250,umask=000        0       2
    .
    .
    .
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto,nls=utf8  0       0
    .
    .
    .

```

---

