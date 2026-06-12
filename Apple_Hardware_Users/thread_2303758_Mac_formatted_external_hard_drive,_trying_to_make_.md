---
title: "Mac formatted external hard drive, trying to make readable and writeable in Ubuntu 14"
date: 2015-11-21
forum: Apple Hardware Users
---

### Post by Tarhawk on 2015-11-21
Ok here is the low down

I have a WD Elements 1tb external hard drive, partitioned and created using a mac some time ago.  It holds most of my sacred documents and of course my music and movie collection.  I cannot access other than through read only permission right now.  I am trying to figure out how to make it readable and writeable in ubuntu but am having no luck.  I have tried to turn off journaling through the mac (OS El Capitan) and no luck, cannot even find an option through which that would be possible.  I tried changing the permissions through mac, and no luck.  I have tried some of the solutions I have found through ubuntu forums and no luck, though some of the solutions were beyond my technical expertise.  I followed the instructions on these two forums

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

[http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

and still no luck, though I think that I might need to modify the path that I would remount the hard drive and I am not sure what code or phrase that is.

Any way, I am in a bit over my head and I would really appreciate any help yall can offer.

---

### Post by weatherman2 on 2015-11-21
If these are your "sacred documents," do you have a backup copy on some other device?  If not, I wouldn't be fooling around with disabling journaling etc. until having made a backup.  It might not be that hard to do something wrong and render that disk unreadable by accident.  Plus, hard drives fail all the time, sometimes without warning (what if your drive falls while it is in operation?) and you might not be able to get any of your documents off.

I have had the same trouble you are having with making a Mac OS volume writable in Linux.  I wasn't seeking a long-term solution - in my case, I mostly needed to get documents OFF of a Mac volume - so I simply copied the contents to a Linux ext4 volume.  Had I used ext2 instead (no journaling) then I could have done read-write on a Mac later too on my new disk - you can add an extension on a Mac to read/write ext2 volumes but, apparently, ext4 is not so easy.

But once you find the solution, I will note it for future use - good luck and please let us know!

---

### Post by sudodus on 2015-11-21
1. You have read only access now. I suggest that you ***backup*** your music and movie collection to another drive.

2. After that you can continue giving the drive write permission with peace of mind.

- There might be better knowledge about MacOS file systems at forums associated to Mac computers.

- You can get help here to remove the current partition table and file system, and create new partitions with file systems that we know have write permission. This will destroy the current data, so you must rely on the backup (item #1). ***gparted*** is a good linux tool to create partitions and file systems.

---

### Post by Tarhawk on 2015-11-23
Hi all, 

Thanks for the responses.  I have now backed up all my data on another hard drive.  I have gparted installed and ready to go.  I am not sure how I am to use gparted though to accomplish reformatting the hard drive so that it is readable and writeable and so that I can copy the files I saved on a mac based external hard drive to the new gparted created hard drive. 

I tried to partition it but that option is no highlighted and is grayed out, there is a little key next to the HFS+ partition so not sure if I can actually override the protection of my hard drive or not.

Any advice on this next step?

---

### Post by slickymaster on 2015-11-23
*Moved to the ***Apple Hardware Users*** sub-forum*

---

### Post by sudodus on 2015-11-23
I think the UDF file system might work for you in all your computers. See the following links. (The first one might be hard to see in Firefox, try with another browser).

[http://tanguy.ortolo.eu/blog/article93/usb-udf](http://tanguy.ortolo.eu/blog/article93/usb-udf)

[https://en.wikipedia.org/wiki/Universal_Disk_Format](https://en.wikipedia.org/wiki/Universal_Disk_Format)

So, to use it, assuming your USB stick is /dev/sdx:

install **udftools** if necessary

sudo apt-get install udftools

```

sudo dd if=/dev/zero of=/dev/sdx bs=1M count=1  # wipe first MB
sudo mkudffs -b 512 --media-type=hd /dev/sdx    # whole drive

```
```

# create a partition table and one partition with gparted or mkusb
sudo mkudffs -b 512 --media-type=hd --lvid=1 /dev/sdx1  # partition

```

The initial dd is to erase the existing partition table or file system information, to prevent you USB stick from being detected as a FAT after it has been formatted with UDF.

The -b 512 is to force a file system block size equal to the USB stick's physical block size, as required by the UDF specification. Adapt it if you have the luck of having a USB stick with an more appropriate block size.

After that, your USB stick will be usable for reading and writing with GNU/Linux and the other free operating systems of course, but also with current versions of Windows (read-only with the outdated version XP) and with MacOS.

---

