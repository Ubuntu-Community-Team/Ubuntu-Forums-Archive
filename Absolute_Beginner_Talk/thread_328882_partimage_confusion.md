---
title: "partimage confusion"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-31
If I want to make a snapshot of my ubuntu system and I want it to go to the usb drive. sudo fdisk -l gives the following.

squrl@squrl-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3197    25679871    c  W95 FAT32 (LBA)
/dev/sdb2            3198        9729    52468290    f  W95 Ext'd (LBA)
/dev/sdb5            3198        6540    26852616    b  W95 FAT32
/dev/sdb6            6541        9729    25615611    b  W95 FAT32

Am I right in doing the backup of sda1 and saving it as /dev/sdb1/savedimage.

Would this be called a snapshot of my system ?

Thanks tosomeone

---

### Post by taurus on 2006-12-31
Did you happen to mount your /dev/sdb1 first before you try to use it?  And assuming you mount it to /media/sdb1, then you should have it to /media/sdb1/savedimage, not /**dev**/sdb1/savedimage since /dev/sdb1 is a device.  You can write stuff to the mount point, not the device...

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by squrl on 2006-12-31
Then I should send it to /media/dev/sdb1. My head is beginning to hurt but some is soaking in.



squrl@squrl-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  3.8G  133G   3% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1              25G  834M   24G   4% /media/V1
/dev/sdb5              26G  320K   26G   1% /media/V2
/dev/sdb6              25G  1.5G   23G   6% /media/V3

---

### Post by pseudonym on 2006-12-31
> **squrl said:**
> IAm I right in doing the backup of sda1 and saving it as /dev/sdb1/savedimage.

Would this be called a snapshot of my system ?

NO! :) That will not work. /dev/sdb1 is just the name of a device on the system. It is not the directory holding the files on your usb drive.

In any caes, for partimage to work, your partition(s) must be unmounted. And if it's your root partition you want to back up, then you can't unmount that while the system is running.

What i highly recommend you do instead is download and burn the [System Rescue CD]("http://www.sysresccd.org/Main_Page"). It has partimiage and a whole lot of other useful tools. Just boot it up, and you can backup whatever partition you want while it is unmounted, and save it your USB drive. This is exactly what i do and it works a treat. :)

---

### Post by taurus on 2006-12-31
> **squrl said:**
> Then I should send it to /media/dev/sdb1. My head is beginning to hurt but some is soaking in.



squrl@squrl-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  3.8G  133G   3% /
varrun                506M   84K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1              25G  834M   24G   4% /media/V1
/dev/sdb5              26G  320K   26G   1% /media/V2
/dev/sdb6              25G  1.5G   23G   6% /media/V3

Since you mount your /dev/sdb1 to **/media/V1** (from the message above), you should send it to /media/V1, NOT /media/dev/sdb1 since there is no such thing.  Now, do you have a write permission to /media/V1?

```
cat /etc/fstab
```

---

### Post by squrl on 2006-12-31
I am talking about using partimage running from the rescue disk. 

What is the correct terminology to save the image to the usb disk.

/media/sdb1/saved image   or   ?????

---

### Post by taurus on 2006-12-31
If you mount your /dev/sdb1 to /media/V1, then it's **/media/V1/savedimage**...

---

### Post by squrl on 2006-12-31
It doesn't look like it. I assumed I did because I use it as the place to store anything I want to be sure doesn't get lost in the confusion.


squrl@squrl-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=26971987-3b36-4b6d-80af-9c8f78ed17bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=2f03bf5b-c2e2-42d4-998a-b0145181f099 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-12-31
Then how did you mount /dev/sdb1 anyway?  Did you mount it from a terminal?

---

### Post by squrl on 2006-12-31
It was just there when I booted up

---

### Post by pseudonym on 2006-12-31
> **squrl said:**
> I am talking about using partimage running from the rescue disk. 

What is the correct terminology to save the image to the usb disk.

/media/sdb1/saved image   or   ?????
OK, once you've booted the rescue disk, you need to create a mount point for your usb drive. Type - ```
mkdir /mnt/usb
``` Now plug in your usb drive if you haven't done so already and type - ```
mount -t vfat /dev/sdb1 /mnt/usb
``` or whatever partition on your usb drive you want to use. It looks like they are all fat32, so '-t vfat' won't change no matter which one you choose (it means -filesystem type fat32).

Once it's mounted you can cd to it if you wish and make a directory to store your image files (you don't have to if you don't want to). now type partimage and follow the steps. Reading the manual at the [partimage homepage]("http://www.partimage.org/Main_Page") beforehand is also highly recommended, of course.

when you're in partimage, the name of the image file it asks you to put in will be like this - ```
/mnt/usb/savedimage.partimg.gz
```. If you made a special directory for it it would be - ```
/mnt/usb/image/savedimage.partimg.gz
```, as an example.
When done, unmount and unplug your usb drive, and boot back into ubuntu :)

---

### Post by squrl on 2006-12-31
Thank you much.  I'll be back after giving this a whirl.

---

### Post by squrl on 2006-12-31
I think it worked.  I now have the following in the usb drive.

savedimage1.partimage.gz.000        2.0 GB   gzip archive
savedimage1.partimage.gz.001       68.4 MB  gzip archive

Not sure I could do it again.   Should I try to redo this compressing a little more to make one file? I want to put this on a DVD now as an iso if thats possible.

Thanks a bunch.

---

### Post by pseudonym on 2007-01-04
> **squrl said:**
> I think it worked.  I now have the following in the usb drive.

savedimage1.partimage.gz.000        2.0 GB   gzip archive
savedimage1.partimage.gz.001       68.4 MB  gzip archive

Not sure I could do it again.   Should I try to redo this compressing a little more to make one file? I want to put this on a DVD now as an iso if thats possible.
Just noticed your post again in some search results which came up. :)

You could use the bzip compression if you want, but it's slower and has been known to be buggy IIRC.

If you want to have just one file for your image, the best way to do it is set the maximum file size to something larger than what you have above, say 2.5GB. Because your total compressed data is less than that (at the moment - it will change as you add stuff to your system), it means only one archive will be made.

You should be able to burn the archives straight onto DVD. I can't see any reason why you would want an iso image (unless you want to make several DVDs of the same thing?). You wouldn't be able to boot it, if that's what you had in mind...

---

### Post by squrl on 2007-01-04
The idea was to be able to restore back to the condition at the time the backup was made with a minimum of effort.  I have yet to find anything better than part image for making a backup. When I first loaded ubuntu I was under the impression I was going to be able to just copy the entire drive file by file and use it as a backup. Guess that would work but you don't get everything that way.

---

### Post by pseudonym on 2007-01-04
Not to mention it would also be a royal PITA to restore. But now you've discovered the wonders of partimage, you can slice and dice, and shake and break your system to your heart's content, without a worry in the world! :)

---

