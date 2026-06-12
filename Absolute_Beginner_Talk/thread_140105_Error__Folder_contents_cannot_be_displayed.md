---
title: "Error : Folder contents cannot be displayed"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-05
i mounted my windows drives in /Windows
there are 4 FAT 32 partitions and 2 NTFS....Details--
Name      Type          Size
C              FAT 32       20 GB
D              FAT 32       20 GB
E              FAT 32        20 GB
G              FAT 32          9 GB
H              NTFS         100 GB
J               NTFS            50 GB

Now i have successfully mounted all of them and my 
/etc/fstab reads as

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               reiserfs notail          0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /Windows/C	vfat	iocharset=utf8,umask=000		
0       0
/dev/hda5       /Windows/D	vfat	iocharset=utf8,umask=000
0	0
/dev/hda6	/Windows/E	vfat     iocharset=utf8,umask=000
0	0
/dev/hda8       /Windows/G	vfat     iocharset=utf8,umask=000
0	0
/dev/hdb5 	/Windows/H	ntfs	nls=utf8,umask=0222	
0	0
/dev/hdb6	/Windows/J	ntfs      nls=utf8,umask=0222
0	0

But on opening /Windows/J  it gives error that 
> You do not have the permissions necessary to view the contents of "J".

No other drive has any such problem and yes i can view the contents of this drive when i su to become root.

ANOTHER PROBLEM  is that i have to run a FTP Server and since it is not possible to write on ntfs systems ....should i convert the two ntfs partitions to FAT like other ones......?? i am afraid to do that since the size of these partitions is quite big and  i don't want to make them smaller.

---

### Post by encompass on 2006-03-05
Wish I could answer your first question... but for the latter...
I wouldn't run Fat or NTFS on any ftp server.  I would format them in to EXT3 so that linux can read them better and faster and mor efficiently... etc etc...

---

### Post by animesh on 2006-03-06
i have installed gparted ....so  should i convert all of my partitions FAT as well as NTFS to EXT 3????? if i have to run a FTP server.
   With Gparted i am not getting an option of converting these partitions.The only options it shows are information and umount

---

### Post by yota on 2006-03-06
Hi,

you have to set umask=0000 to ntfs mounts (like you have done for the fat ones) to give ordinary user the right to browse them.

About the conversion AFAIK there's not the possibility to switch directly from ntfs to ext3, you'll have to move the data to somewhere else, change the partition type with your tool of choice, format in ext3 and then move the data back.

Hope this helps.

---

### Post by LordBug on 2006-03-06
umask=0000 on NTFS is bad.  Very, very, very bad.  Umask=0222 is correct, it removes only write access.  Read access *should* still be there.  Seeing that you can browse 'H' (or I assume, based on what you're saying), I'd say your fstab is correct.

You might want to unmount 'J', chown and chmod the mountpoint so everyone can access it (root:users, mode 777 should do), and then re-mount 'J'.  Can't say for sure if this will fix it, honestly, but it's worth a try.

---

### Post by animesh on 2006-03-06
thanks for the suggestion lordbug ,i just unmounted it by umount and removed the line corresponding to it from /etc/fstab
rebooted
then i again added the line corresponding to J ie mounted it 
and its working now.....

Is there no other way to go around this conversion problem (from FAT ,NTFS to EXT 3)because i have a lot of data and it isn't possible to transfer it to any other comp ???

---

