---
title: "FAT32 partition recognition - Dual Boot"
date: 2011-07-14
forum: Apple Hardware Users
---

### Post by platyiwings on 2011-07-14
Hello there,

I've been using Mac OSX10.4 intel iMac.  I could successfully install both Mac OSX 10.4  and Ubuntu to intel iMac referring forum;  Dual boot. In addition I made a FAT 32 partition for trying to use both Mac OSX 10.4 and Ubuntu mode.   So far, dual booting and  hard disk drive works well.  However
I have a problem for the following.

I can see the HDD drive icon on Mac OSX 10.4 mode but I can't see HDD on Ubuntu mode.  I created FAT32 partition under /windows mount point.  I can see the FAT32 partition if I go to disk utility on Ubuntu's "mount point" and click the hyper linked "/windows". 

(The fact is that I created two FAT32 partitions on HDD drive and one is under /windows and the other is 
/dos because I couldn't create partition under the same mount point.  )


Is there any way to move HDD icon to Desktop or other area so that I could access more easily. 

The reason why I make FAT32 partition is that I have many photos burned CDs both readable Macintosh OSX and WIndows OS. But I couldn't move the data burned to CDs to Ubuntu.

However, I could copy from Cds to FAT32 partitioning area on Mac OSX 10.4 and it is also possible to readable  from Ubuntu as well....

Thanks for your kind help.


Platyiwings,

---

### Post by ajgreeny on 2011-07-14
> **platyiwings said:**
> (The fact is that I created two FAT32 partitions on HDD drive and one is under /windows and the other is 
/dos because I couldn't create partition under the same mount point.  )


Is there any way to move HDD icon to Desktop or other area so that I could access more easily. 


I'm sorry to say that I don't really understand what you are meaning by the first paragraph quoted above, unless it is the mounpoints of the partitions you have set in /etc/fstab  If so, you need to ensure that the two folders for mountpoints already exist in your filesystem, and if not make them with ```
sudo mkdir /windows /dos
```  The second paragraph is perhaps more easy to deal with by using gconf-editor, but before going too deep into things, can you explain a bit more about what you are trying to do, and exactly how you are trying to do it.  Are these partitions mounted already, or is that the main problem?  The command ```
mount
``` will show you what is mounted at any time, so can you show the output of that now, please.

---

### Post by platyiwings on 2011-07-14
[SIZE=2]> **ajgreeny said:**
> I'm sorry to say that I don't really understand what you are meaning by the first paragraph quoted above, unless it is the mounpoints of the partitions you have set in /etc/fstab  If so, you need to ensure that the two folders for mountpoints already exist in your filesystem, and if not make them with ```
sudo mkdir /windows /dos
``` 



[/SIZE][SIZE=2]Thank you very much for the note.  I'm sorry to make you confusing about my explanations. Under the current condition, all systems works well by using boot chooser.  Also two partitions that I made are fine. The both FAT32 partitions are recognised, formatted and mounted as L[/SIZE][SIZE=2]inux partition.  

When I create the second FAT partition while I was installing under same "/windows"  [/SIZE][SIZE=2]mountpoint [/SIZE][SIZE=2] with the first FAT32 partition. Then, I created under "/dos" but both partition are working without problem.  

The only thing that I wanted to do is that I would like to access both partitioned areas from desktop not going to "Harddisk utilities" and clicking hyper linked words.


>  The second paragraph is perhaps more easy to deal with by using gconf-editor, but before going too deep into things, can you explain a bit more about what you are trying to do, and exactly how you are trying to do it.  Are these partitions mounted already, or is that the main problem?  The command ```
mount
``` will show you what is mounted at any time, so can you show the output of that now, please.
mount command says:
[/SIZE]
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda4 on /dos type vfat (rw,utf8,umask=007,gid=46)
/dev/sda6 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kagechio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxxxx )


thank you for your help. to be continued...

Just few minutes ago...

I changed format type from FAT32 to Mac OS journaling then I came across the fatal error for booting from Linux.
I will be back after reinstall Ubuntu again.

---

### Post by platyiwings on 2011-07-15
> **platyiwings said:**
> [SIZE=2]



[/SIZE][SIZE=2]Thank you very much for the note.  I'm sorry to make you confusing about my explanations. Under the current condition, all systems works well by using boot chooser.  Also two partitions that I made are fine. The both FAT32 partitions are recognised, formatted and mounted as L[/SIZE][SIZE=2]inux partition.  

When I create the second FAT partition while I was installing under same "/windows"  [/SIZE][SIZE=2]mountpoint [/SIZE][SIZE=2] with the first FAT32 partition. Then, I created under "/dos" but both partition are working without problem.  

The only thing that I wanted to do is that I would like to access both partitioned areas from desktop not going to "Harddisk utilities" and clicking hyper linked words.



mount command says:
[/SIZE]
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda4 on /dos type vfat (rw,utf8,umask=007,gid=46)
/dev/sda6 on /windows type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kagechio/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=xxxxxxx )


thank you for your help. to be continued...

Just few minutes ago...

I changed format type from FAT32 to Mac OS journaling then I came across the fatal error for booting from Linux.
I will be back after reinstall Ubuntu again.

The  following links are useful explanation regarding dual booting from Mac OSX.

[http://help.ubuntu.com/community/DualBoot/MacOSX]("http://help.ubuntu.com/community/DualBoot/MacOSXThe")





I tried to reinstall Ubuntu several times since then added partitioning FAT32 as mountpoint "/dos" to intel iMac and I found a file folder named "dos" under  "File System" .  It was the partition of FAT32.  However I have deleted the partition and reinstalled  Ubuntu without additional partition for dual boot because It may be easier way for beginner.


It works fine so far.... what I wanted to do is... I will post it making new thread.   oops.. I missed how to make a new thread...


If someone knows that how to transfer the data backed up CDs while I was using Mac OSX 10.4.  I burned data; photos and .AVI formatted file to  CDs. (DVD-R/CD-R)   All data is wholly-owned my personal property and I made them for readable on windows OS and Mac OS.  

The issue is that Ubuntu system tells me that there's no permission to copying to anyplace on Ubuntu...

Thanks for taking your time.

:(
Sincerely yours,

---

### Post by platyiwings on 2011-07-15
[QUOTE=platyiwings;11049395]The  following links are useful explanation regarding dual booting from Mac OSX.

[http://help.ubuntu.com/community/DualBoot/MacOSX]("http://help.ubuntu.com/community/DualBoot/MacOSXThe")





I tried to reinstall Ubuntu several times since then added partitioning FAT32 as mountpoint "/dos" to intel iMac and I found a file folder named "dos" under  "File System" .  It was the partition of FAT32.  However I have deleted the partition and reinstalled  Ubuntu without additional partition for dual boot because It may be easier way for beginner.


It works fine so far.... what I wanted to do is... I will post it making new thread.   oops.. I missed how to make a new thread...


If someone knows that how to transfer the data backed up CDs while I was using Mac OSX 10.4.  I burned data; photos and .AVI formatted file to  CDs. (DVD-R/CD-R)   All data is wholly-owned my personal property and I made them for readable on windows OS and Mac OS.  

The issue is that Ubuntu system tells me that there's no permission to copying to anyplace on Ubuntu...

Thanks for taking your time.

:(
Sincerely yours,

---

### Post by ajgreeny on 2011-07-15
I have no idea how you get icons for drives on your desktop, nor even if it is possible if you are using unity in 11.04, but for classic gnome, open **gconf-editor ->apps ->nautilus->desktop** and select the **volumes_visible** at the bottom of the list.  Any mounted partitions will now show as icons on the desktop.

---

### Post by platyiwings on 2011-07-15
> **platyiwings said:**
> [QUOTE=platyiwings;11049395]The  following links are useful explanation regarding dual booting from Mac OSX.

[http://help.ubuntu.com/community/DualBoot/MacOSX]("http://help.ubuntu.com/community/DualBoot/MacOSXThe")





I tried to reinstall Ubuntu several times since then added partitioning FAT32 as mountpoint "/dos" to intel iMac and I found a file folder named "dos" under  "File System" .  It was the partition of FAT32.  However I have deleted the partition and reinstalled  Ubuntu without additional partition for dual boot because It may be easier way for beginner.


It works fine so far.... what I wanted to do is... I will post it making new thread.   oops.. I missed how to make a new thread...


If someone knows that how to transfer the data backed up CDs while I was using Mac OSX 10.4.  I burned data; photos and .AVI formatted file to  CDs. (DVD-R/CD-R)   All data is wholly-owned my personal property and I made them for readable on windows OS and Mac OS.  

The issue is that Ubuntu system tells me that there's no permission to copying to anyplace on Ubuntu...

Thanks for taking your time.

:(
Sincerely yours,



To prepare two softwares which we can get from Software Center.  

To make iso image -> data (readable only at this point) -> move the data to certain area at home folder -> unmount data -> delete iso image.


1. Brasero  
     We make iso image from data burned readable only DVD/CD 
     (Please don't delete iso image till all data has been copied to linux HDD)

 2. Gmount-iso
We make data from iso image and move to certain area of home folder.  Because unless we move the data, all data is under protection.

3. Once we moved extracted data to home folder , then we unmount the place to data extracted.
    once we confirm unmount, then we can delete iso image that we created.

 :)

---

### Post by platyiwings on 2011-07-15
> **ajgreeny said:**
> I have no idea how you get icons for drives on your desktop, nor even if it is possible if you are using unity in 11.04, but for classic gnome, open **gconf-editor ->apps ->nautilus->desktop** and select the **volumes_visible** at the bottom of the list.  Any mounted partitions will now show as icons on the desktop.




Thank you very much for the kind instruction.  Let me check the gconf-editor and command.
The problem is I don't know much about computer.  I have done dual booting almost without reading 
documents on Ubuntu linked above.  I just took a look at documents and increased imagination.
Let me learn more about Linux command and how Linux partitioning works.

Special thanks to Mr. ajgreeny 

:)


Sincerely yours,



:)

---

### Post by platyiwings on 2011-07-15
> **platyiwings said:**
> [QUOTE=platyiwings;11049809]



To prepare two softwares which we can get from Software Center.  

> To make iso image -> data (readable only at this point) -> move the data to certain area at home folder -> unmount data -> delete iso image.We can delete iso image after we move data to home folder.  Then we unmount disk by clicking mouse right button.


[QUOTE]
1. Brasero  
     We make iso image from  burned readable only DVD/CD 
     (Please don't delete iso image till all data has been copied to linux HDD)

 2. Gmount-iso
We make data from iso image and move to certain area of home folder.  Because unless we move the data, all data is under protection.

3. Once we moved extracted data to home folder , then we unmount the place to data extracted.
    once we confirm unmount, then we can delete iso image that we created.

 :)Amendment: we can delete iso image file at anytime and unmount above mentioned procedure.



Thank you very much for all of everybody's help, support and encouragement posting here and documentations.  I appreciate giving me lots of valuable information from the partitioning to FAT32 and documentations.   I will keep all information to archive in my memory  and I'd like to extract them while I learn about Linux commands and Operating Systems.



Thx

---

### Post by platyiwings on 2011-07-15
> **platyiwings said:**
> [QUOTE=platyiwings;11050033][QUOTE=platyiwings;11049809]



To prepare two softwares which we can get from Software Center.  

We can delete iso image after we move data to home folder.  Then we unmount disk by clicking mouse right button.


Amendment: we can delete iso image file at anytime and unmount above mentioned procedure.



Thank you very much for all of everybody's help, support and encouragement posting here and documentations.  I appreciate giving me lots of valuable information from the partitioning to FAT32 and documentations.   I will keep all information to archive in my memory  and I'd like to extract them while I learn about Linux commands and Operating Systems.



Thx

One thing I need to add is that I couldn't recognize the images burned in Mac OS format.  It should be better to burn CD with iso image + mac OS format when we make back up to CD on Mac OSX mode.

---

### Post by platyiwings on 2011-07-17
> **platyiwings said:**
> [QUOTE=platyiwings;11049809]



To prepare two softwares which we can get from Software Center.  

To make iso image -> data (readable only at this point) -> move the data to certain area at home folder -> unmount data -> delete iso image.


> 
1. Brasero  
     We make iso image from data burned readable only DVD/CD 
     (Please don't delete iso image till all data has been copied to linux HDD)

 2. Gmount-iso
We make data from iso image and move to certain area of home folder.  Because unless we move the data, all data is under protection.

Furius  ISO mount software might be better than Gmount-iso for further research when we have other than iso 9660+joilet format.  We can get it from Software Center as well.



3. Once we moved extracted data to home folder , then we unmount the place to data extracted.
    once we confirm unmount, then we can delete iso image that we created.

 :)

---

