---
title: "i need ur suggestion in my partitioning"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-06-06
new to ubuntu, i have dual boot system on one harddisk, windows and ubuntu, where the partitions look like :

windows partition NTFS    mount :  /media/sda1
windows partition NTFS    mount :  /media/sda5
windows partition NTFS    mount :  /media/sda6
linux partition EXT3           mount :  /
linux partition SWAP
linux partition EXT3           mount :  /data1
linux partition EXT3           mount :  /data2
linux partition EXT3           mount :  /data3

now am looking to let ubuntu read/write its partitions and also read/write windows partitions, where i want  widows just to read/write its partitions, is this behavior possible??

another thing that if we go to the computer location in nautilus we can access windows partitions there rather than accessing them from /media/ (also they appear in main menu >> places) , can i do this behavior to linux partitions too except the linux root partition (only data1, data2, data3 in the partitions list above) so that they become accessible in computer location and in places menu??

---

### Post by Dedoimedo on 2007-06-06
Hello,

Windows does not see Linux partitions, so you're automatically set there.

Linux can automatically read and write FAT partitions. If you want to allow write permissions for NTFS, you will need to do the following:

1. Backup your fstab

sudo cp /etc/fstab /etc/fstab_backup

2. Find out which partitions you want to allow write permissions. If you know already, go to step 3.

To see what partitions are available on your disks:

sudo fdisk -l

You seem to be familiar with Linux notation, so I don't foresee problems here.

If your desired drives are not mounted in Linux, you will need to mount them.

A. Create mount point:

sudo mkdir /media/partition_name (eg. windows_drive_1)

B. Edit fstab with relevant permissions.

3. Editing fstab (sudo gedit /etc/fstab)

To allow read-only access for NTFS partitions:

/dev/hdXY /media/partition_name ntfs nls=utf8,umask=0222 0 0

or

/dev/sdXY /media/partition_name ntfs nls=utf8,umask=0222 0 0

In your case, it's sdXY, XY being drive and partition (eg. sda1, sdb3 etc.)

You can also use other charset instead of utf, but if you have non-English characters, some of the drive names might not display properly.

To allow write access, first install ntfs-3g:

sudo apt-get install ntfs-3g.

Then:

/dev/hdXY /media/partition_name ntfs-3g defaults,locale=en_US.utf8 0 0

or

/dev/sdXY /media/partition_name ntfs-3g defaults,locale=en_US.utf8 0 0

Again, substitute XY with what you need, also change the charset if you need.

If you have questions, feel free to ask.

Regards,
Dedoimedo

---

### Post by akkad on 2007-06-06
what about accessing linux ext3 partitions from places menu and computer location in nuatilus

---

### Post by Dedoimedo on 2007-06-06
Hello,
If I understand you correctly, some of the Linux partitions are not mounted?
You can mount them in the same manner, with regard to the filesystem.
Dedoimedo

---

### Post by akkad on 2007-06-06
actually i tried reading the fstab and your given steps but i coudlnt understand what i should exactly do :(

---

### Post by Dedoimedo on 2007-06-06
Please tell me at what step did you get stuck.
Regards,
Dedoimedo

---

### Post by akkad on 2007-06-06
ok first i would like to show u the content of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=39900987-8406-438d-9c50-fd6cecccd29c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda11
UUID=99f9cc71-01de-4d6a-9337-e001bfa38ab8 /Data           ext3    defaults        0       2
# /dev/sda10
UUID=7d71e899-d61c-451b-ae5d-2e58fb0bc256 /VMware         ext3    defaults        0       2
# /dev/sda9
UUID=74800777-1ab2-4202-bf23-5168765c4e34 /Workstation    ext3    defaults        0       2
# /dev/sda1
UUID=94B4B752B4B73618 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=E0F076CFF076AC02 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=ACE839DBE839A48C /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=5EA0C2C6A0C2A3BD /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda12
UUID=e1dd063c-f950-49ec-abbc-2bcdc73fc61d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

i installed the ntfs-3g but what to do next i dont know??

---

