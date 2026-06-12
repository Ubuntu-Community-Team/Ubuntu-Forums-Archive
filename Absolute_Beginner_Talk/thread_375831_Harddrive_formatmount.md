---
title: "Harddrive format/mount?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by bodyboarding_bum on 2007-03-04
Hi again, Im STILL having problems with my dual monitor and no-one has replied ... [http://www.ubuntuforums.org/showthread.php?t=375728](http://www.ubuntuforums.org/showthread.php?t=375728)

But here is my question... 
I have 2 internat hard-drives
I used to be running windows (vista), like everyone hey? And i wanted to become completely windows free on this computer. So i formatted my main drive that had vista installed on it, and this is where i installed ubuntu. I put all my media on the other drive so it was safe while i was changing OS. I have now copied everything off the second drive and reformatted it into an etx3 partition, my question is... How do i make it mount automatically each time i start my computer, and is it possilbe to make the drive show up in the 'computer' file (Places>Computer) ? just like my cd drive and other HD?

When i type in : 
```

 sudo fdisk -l

``` 

This is what i get : 
```

 Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081   83  Linux

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9539    76621986   83  Linux
/dev/sda2            9540        9726     1502077+   5  Extended
/dev/sda5            9540        9726     1502046   82  Linux swap / Solaris
kyle@kyle-desktop:~$ 
 
```

So i know ubuntu has detected my HD as it is listed above as hdb1.

Thanks in advance

---

### Post by Rui Pais on 2007-03-04
hi,
make a folder where you want to mount it, 
and after that just edit your /etc/fstab:
```
gksudo gedit /etc/fstab
```(or if you have kubuntu replace gedit with kedit, if you have xubuntu replace gedit with mousepad)

 and add a line:
```
/dev/hdb1  <my_mount_folder>  ext3  defaults,noatime   0  2 
```
replace <my_mount_folder> for the folder you choose or created.

---

### Post by bodyboarding_bum on 2007-03-04
Thanks, but no luck :( ... 
i followed your codes, and i guessed u meant 
```

sudo gedit /etc/fstab

```

But it still doesnt work.
Is it possible to mount it so is appears in the 'computer folder' ? if you know what im talking about.

---

### Post by overdrank on 2007-03-04
> **bodyboarding_bum said:**
> Thanks, but no luck :( ... 
i followed your codes, and i guessed u meant 
```

sudo gedit /etc/fstab

```

But it still doesnt work.
Is it possible to mount it so is appears in the 'computer folder' ? if you know what im talking about.

Hi this worked for me in 6.06 dapper

4.2.3.&#8195;Make partitions automatically available

Again, Windows and other partitions should be automatically available from Ubuntu. If they are not, the following procedure will make them automatically available:

   1.    						

      Read Section 4.3.7.1 &#8213; Check disk space usage and view the partition table
      						
     					
   2.    						

      First make a directory where the partition can be made available ("mounted"):
   						

      sudo mkdir /media/windows
           					
   3.     						

      Next, backup your disk configuration file and open the file in a text editor with administrative privileges:
      						

      						
     sudo cp /etc/fstab /etc/fstab_backup
      gksudo gedit /etc/fstab   		

     			
   4.    						

      Append the following line at the end of file:
      							

      /dev/hda1 /media/windows ntfs umask=0222 0 0 						
     					
  			

      Replace /dev/hda1 with the correct device name for your partition.

      							

      If your Windows partition uses the FAT32 filesystem, replace ntfs with vfat in the above command.     							

      If you have a FAT32 filesystem, it is also safe to allow read-write access. To do this, change the value of umask to 0000.   						

      					
   5.    						

      Save the edited file (an example)

      		
   6.    				

      The changes will take effect when the computer is restarted.

---

### Post by Rui Pais on 2007-03-04
> **bodyboarding_bum said:**
> Thanks, but no luck :( ... 
i followed your codes, and i guessed u meant 
```

sudo gedit /etc/fstab

```

But it still doesnt work.
Is it possible to mount it so is appears in the 'computer folder' ? if you know what im talking about.

Sorry, a made a typo. 
Should be gksudo, (i writed gkduso, it's corrected now. Some people advise to use gksudo for gui apps and sudo for terminal... although i never understand the point...) 

what exactly failed? Have you reboot or made:
```
sudo mount -a
```
can you post your /etc/fstab?


**@paul capps**
hi, 
you missed the 1st. post of the OP. He/she moved for no Windows and according to the first post there are only ext3 partitions, no ntfs.

---

### Post by bodyboarding_bum on 2007-03-04
it mounts now, following ur instructions Rui Pais.
Thanks :)
but is there anyway to make it mount as a drive in the 'computer' file?

Heres my fstab file 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90868e37-a385-4628-a2b8-f3eef8f5b138 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7bd2db94-ccfc-40d3-912e-c80555525f72 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdb1  /Home/Kyle/Other_Harddrive  ext3  defaults,noatime   0  2


```

---

### Post by Rui Pais on 2007-03-04
yes, just make the mount point inside /media.

Like :
```
sudo mkdir /media/hdb1
```
and replace in your fstab /Home/Kyle/Other_Harddrive with /media/hdb1

reboot or do sudo mount -a

that should do the trick :)

---

