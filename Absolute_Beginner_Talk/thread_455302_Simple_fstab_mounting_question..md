---
title: "Simple fstab mounting question."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1fd98cda-4b20-4166-b8f5-0866088ff37c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=c1f05557-02be-43ab-8a07-74013bf8dc97 /home           ext3    defaults        0       2
# /dev/sda1
UUID=343CEEAE3CEE6A76 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=a4795e73-acf5-4b59-bb3f-4b8086f8619b /media/sdb2     ext3    defaults        0       2
# /dev/sda2
UUID=7363b24d-bbb2-427c-bc8c-2e1699072d72 none            swap    sw              0       0
# /dev/sdb5
UUID=85983bba-6bc7-4bf3-a92a-0c5a053acf74 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0




I don't want sda1 or sdb2 to mount upon system startup.

I thought taking the # out would work. But they still showed up. I already made an fstab backup called "fstabbackup" in my /etc folder to prevent any damage, however I figured I'd still ask to make sure.

---

### Post by earobinson on 2007-05-26
That should work, sounds like you need to turn off auto mounting (this may stop dvd's cd's usb keys from mounting) take a look at System -> Preferences -> Removable Drives and Media

---

### Post by Roasted on 2007-05-26
Everything under storage is unchecked......

---

### Post by matthinckley on 2007-05-27
you need to comment out the lines underneath /dev/sda1 and /dev/sdb2

# /dev/sda1
# UUID=........

---

### Post by cmayo on 2007-05-28
The #'s comment out lines so they are ignored - which is OK if you never want to mount the partitions.

Changing the defaults option to noauto instead:
[FONT="Fixedsys"][INDENT]UUID=343CEEAE3CEE6A76 /media/sda1 ntfs noauto,nls=utf8,umask=007,gid=46 0 1
UUID=a4795e73-acf5-4b59-bb3f-4b8086f8619b /media/sdb2 ext3 noauto 0 2[/INDENT][/FONT]
Then you can still mount manually.

---

