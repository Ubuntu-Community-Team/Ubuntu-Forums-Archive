---
title: "Mount EXT2/3 in Mac OS X 10.6"
date: 2011-02-15
forum: Apple Hardware Users
---

### Post by el_heffe on 2011-02-15
The other day, I wanted to access my Ubuntu partitions on my OS X side. First things first, I downloaded MacFuse from:

[http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)

Then, I went to 

[http://sourceforge.net/projects/fuse-ext2/](http://sourceforge.net/projects/fuse-ext2/)

and got their software. From there I mounted the .DMG files and ran the installers. I was able to get all of the software installed and running with no reboot required. Then I loaded the MacFuse control panel, enabled beta, and updated. **NOTE:** I am unsure if you need the beta for this to work as I did not try without it! Upon the completion of the update, I fired up terminal.

Now, I needed to know exactly which partition my /home/ was located on, so I typed:

```
$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *160.0 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Artemis                 65.9 GB    disk0s2
   3:       Microsoft Basic Data UNTITLED                22.0 GB    disk0s3
   4:       Microsoft Basic Data UNTITLED                68.0 GB    disk0s4
   5:                 Linux Swap                         4.0 GB     disk0s5
/dev/disk5
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *1.0 TB     disk5
   1:                  Apple_HFS Traboom                 307.1 GB   disk5s1
   2:                 DOS_FAT_32 TRANSMIT                693.1 GB   disk5s2

```

From this, and my basic knowledge of how I setup my Ubuntu partitions, I was able to tell that my 68 GB disk, disk0s4, was my Ubuntu /Home.  Then I created a directory in my /Volumes folder to mount the EXT partition to by typing:
```

sudo mkdir /Volumes/Ubuntu

```
Now that I knew what the disk was and had the all software installed, all I needed to do was mount disk0s4.  This is accomplished with:

```
sudo mount -t fuse-ext2 /dev/disk0s4 /Volumes/Ubuntu/
```

*sudo* gives you the root privileges required to make this happen.  mount is the command used to mount the volume.
*-t fuse-ext2* is to specifiy the filesystem type, in this case ext2 works for ext2 or ext3.[I]
/dev/disk0s4[/I] is the volume we want to mount.
*/Volumes/Ubuntu* is where we are mounting the volume too.

Then, I went into the Finder and saw a volume on the left side of the window called "disk0s4".  In there are all my files from my home directory of Ubuntu that I can easily access.  Great success!

The system that all of this was done on is a Dell Min 10v dual booting between OS X 10.6.6 and Ubuntu 10.10.

---

### Post by cfr42 on 2011-04-23
Would this work on a PPC? diskutil obviously gives rather different output in that case, but the basic problem should be the same?

It looks to work on 10.4+ and doesn't specify Intel so...

I'm not very impressed by this:
```

# Make Spotlight aware of debug symbols for libfuse and the Objective-C framework.
# We do this for the user that is logged in at the console.
sudo -u `stat -f %Su /dev/console` mdimport /Library/Frameworks/MacFUSE.framework/Resources/Debug/

# Remove our receipt; MacFUSE.pkg doesn't have a payload.
rm -rf "$FINAL_RECEIPT"

```Not only does MacFUSE insist on installing stuff under /System/Library rather than /Library, it then deliberately destroys the record of what was installed where. I have no idea what the comment explaining this line is meant to mean but the rm line is rather worrying.

And I do wish developers wouldn't assume that everyone is enamoured of Spotlight!

---

