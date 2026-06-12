---
title: "Xubuntu does not mount my 2nd int. HD"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by natgab on 2009-11-04
Odd Xubuntu glitch,

I have a Power Mac with Ubuntu 9.04, which has two internal SATA HDs. Ubuntu shows both HDs in Home folder, desktop, etc. But when I switch to Xubuntu I can only see my main HD w/ Home. My main HD is ext3, BUT my 2nd HD is still HTFS (apple format)

Could there be any problem with the fact that I installed only XFCE with apt-get and did not install Xubuntu?  I did not want to have duplicate applications.

I found this thread, but it would not work. I could not get it to work when I changed the extension to HTFS but it gave an error.

[http://art.ubuntuforums.org/showthread.php?p=7416965](http://art.ubuntuforums.org/showthread.php?p=7416965)

---

### Post by oswaldkelso on 2009-11-08
xfce is lighter than gnome so you'll need to add the apple drive to your /etc/fstab file.

run mac-fdisk to list your drives. heres the out put of mine.
```

debian800:/home/ok# mac-fdisk -l
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2              Apple_Free                      262144 @ 64       (128.0M)  Free space
/dev/hda3               Apple_HFS Apple_HFS_Untitled_1 12332736 @ 262208   (  5.9G)  HFS
/dev/hda4              Apple_Free                          16 @ 12594944 (  8.0k)  Free space

Block size=512, Number of Blocks=12594960
DeviceType=0x0, DeviceId=0x0

/dev/hdb
        #                    type name                  length   base      ( size )  system
/dev/hdb1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hdb2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/hdb3         Apple_UNIX_SVR2 untitled            13671876 @ 2018      (  6.5G)  Linux native
/dev/hdb4         Apple_UNIX_SVR2 swap                 1494141 @ 13673894  (729.6M)  Linux swap
/dev/hdb5         Apple_UNIX_SVR2 untitled           383129053 @ 15168035  (182.7G)  Linux native

Block size=512, Number of Blocks=398297088
DeviceType=0x0, DeviceId=0x0

debian800:/home/ok# 
```

/dev/hda3 is the apple hfs partition on my drive so I would add that to the /etc/fstab file. I have no idea as to the formate for htfs so you'll have to google that. 

Create a mount point e.g. ```
 # mkdir /media/apple
```.  Once added your apple partition to you fstab file will be mounted on boot. Or with ```
 # mount -a /dev/hda3 /media/apple (replace with your osx device path and mount point not mine)
``` 

See for more info [http://art.ubuntuforums.org/showthread.php?t=657225&](http://art.ubuntuforums.org/showthread.php?t=657225&)

---

