---
title: "HD Mounting issues."
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by NamedUser on 2007-09-28
Okay, here's the deal. I get a new HD, I get it to format to ext2, I mess around with stuff for a while, get it to let me copy stuff to it and call it good. Then I reboot. That drive is no longer mounted and I can't get it mounted, then whilst monkeying with things to try and get it to work again, I end up borking my sdb as well as the new sdc.

At this point I no longer have the mtab or fstab entries related to these drives, and while I've been able to get sdb1 to mount it never auto-mounts properly on boot and sdc1 can't seem to mount at all.

So basically... how the frick do I set the mounting stuff up? I've looked around for a while and can't seem to find something to help when all you have is the hard drive identifier and a bunch of random errors.

Here's the fdisk -l for the two drives
> 
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      484521   244198552+  83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux


then fstab followed by mtab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=25abdd76-3a58-46ab-af7d-df699ad22677 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=0A98D79598D77D9F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=46D80F88D80F7609 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

# /dev/hda5
UUID=94bfc68d-6022-4fc2-be3d-6c14e9615ecb none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

> 
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sdb1 /media/sdb1 ext2 rw,noexec,nosuid,nodev 0 0


Note: I'm a complete newb and have probably borked a few things whilst trying to do this stuff and don't really know exactly what I'm doing sometimes.
Other note: I want sdb1 and sdc1 mounted as such on /media, like the sda1 is (but not ntfs)

EDIT: Okay, I guess I lied, there is an mtab for sdb1. Also, I did over 6 hours of engineering labs today and am probably gonna pass out soon.

---

### Post by Arthur Archnix on 2007-09-28
Well, if you only have two hd's then yes, you've really borked your fstab. Fdisk says you have two disks, it calls one sdb which is 250GB, and one called sdc, which is 750 GB.

Post the output of this code, and confirm that you only have two hd's. 
```
ls -l /dev/disk/by-uuid
```
Once we know which one you're booting from we can proceed with confidence and fix this little problem.

Edit: Oh, and add the size of your new hard-drive as well. I'm guessing you have two and that the 750 is the new one, but I don't want to give you advice that leads you with an unbootable system, so I'll need that extra info.

---

### Post by NamedUser on 2007-09-28
```

lrwxrwxrwx 1 root root 10 2007-09-28 01:05 0A98D79598D77D9F -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-09-28 01:05 25abdd76-3a58-46ab-af7d-df699ad22677 -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-09-28 01:06 2903b9fa-c5b2-4258-83cb-364508c736d7 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2007-09-28 01:05 46D80F88D80F7609 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-09-28 01:05 94bfc68d-6022-4fc2-be3d-6c14e9615ecb -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-09-28 01:05 97bb4d9c-eb6e-47bc-be55-f02424ce9093 -> ../../sdb1


```

I have an 80GB drive I boot from (hda), two 250GB and a new 750GB (sda,b,c) I use as media. They DID appear when I did fdisk, I just decided to only copy down the 250 and 750 that I screwed up. Here's the full fdisk:
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5222    41943040    7  HPFS/NTFS
/dev/hda2            8733        9729     8008402+   5  Extended
/dev/hda3            5223        8732    28194075   83  Linux
/dev/hda5            8734        9729     8000370   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484518   244197040+   6  FAT16

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      484521   244198552+  83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   83  Linux

```

---

### Post by Arthur Archnix on 2007-09-28
Ok, so this is roughly what your system looks like:
```

NAME	UUID			              SIZE	TYPE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
hda1 = 0A98D79598D77D9F                       45GB     NTFS
hda3 = 25abdd76-3a58-46ab-af7d-df699ad22677   34GB 	EXT3
hda5 = 94bfc68d-6022-4fc2-be3d-6c14e9615ecb   01GB 	 SWAP
sda1 = 46D80F88D80F7609			       250GB    ?
sdb1 = 97bb4d9c-eb6e-47bc-be55-f02424ce9093    250GB 	?
sdc1 = 2903b9fa-c5b2-4258-83cb-364508c736d7    750GB 	ext2
```

I&#8217;m sure those hda sizes are a bit off, I was just guessing from the cylinders. To mount something properly in fstab we need to know the uuid, the mountpoint, the filetype and any options we want. Let&#8217;s just look at the 80Gig drive in your fstab first, which is booting properly:

 ```
# /dev/hda3 &#8211; Linux
UUID=25abdd76-3a58-46ab-af7d-df699ad22677 / ext3 defaults,errors=remount-ro 0 1
```
The comment tells US that we&#8217;re looking at hda3, but it&#8217;s the uuid that really matters because that&#8217;s what the system reads. We confirm that they match, and they do. After the uuid is the mount point &#8220;/&#8221; meaning your root. Then the filesystem &#8220;ext3&#8221;, which is a default ubuntu install. Then your mount options, then numbers which for filesystems that are read/write usually should be 0 1, and read only 0 0 
```
# /dev/hda1 &#8211; Windows 
UUID=0A98D79598D77D9F /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
Again, uuid matches, mountpoint is at /media/hda1, though if it would make it easier for you you could &#8220;sudo mkdir /media/windows&#8221; then change this part in fstab to &#8220;/media/windows&#8221;, but anyway its fine, the filesystem is ntfs, and so on.
```
# /dev/hda5 &#8211; Linux swap partition
UUID=94bfc68d-6022-4fc2-be3d-6c14e9615ecb none swap sw 0 0
```
Swap drive. Uuid matches, looks good.

Got it? Let&#8217;s just get the 750GB up and running and then you can probably figure out the rest. In your first post you said you formatted it to ext2. We know the name &#8220;sdc1&#8221;, the uuid &#8220;2903b9fa-c5b2-4258-83cb-364508c736d7&#8221;, so the only thing left is the mount point. From the terminal do:
```
sudo mkdir /media/750GB
```
You don&#8217;t have to call it &#8220;750GB&#8221;, but if you do call it something else then don&#8217;t use 750GB in the following example, use whatever you call it.
Now let&#8217;s just test this out. Replace username with your login name.
```
sudo mount /dev/sdc1 /media/750GB
sudo chown &#8211;R username:username /media/750GB
mkdir /media/750GB/test
```
If that worked without errors then we can go ahead. If there were errors then we may have a more serious problem, and you should post back what happened.

In your fstab create this entry:
```
#dev/sdc1 &#8211; 750GB
UUID=2903b9fa-c5b2-4258-83cb-364508c736d7	/media/750GB	ext2	defaults	0	1
```
Comment any remaining entries, leaving only the hda entries and the new sdc entries.

IT"S VERY IMPORTANT YOU DON"T COMMENT OUT YOUR HDA ENTRIES OR YOU WON"T BE ABLE TO BOOT!

Reboot. It should be mounted and writable and give you no errors on boot. Now work on the other two drives one at a time. Google mount options when trying to determine what to use for your fat drive "fat mount options" or the like. Write back if you end up having trouble with the other two drives.

---

### Post by NamedUser on 2007-09-28
Alright, doing this got my sdb1 to work properly and auto-mount on boot-up and everything. Unfortunately, trying to "sudo mount /dev/sdc1 /media/sdc1" got my an error, specifically "you must specify file system type". Oddly, mounding /dev/sdc works.

---

### Post by Arthur Archnix on 2007-09-28
Hmm.. didn't think it would need it, but ok.
```
sudo mount /dev/sdc1 /media/sdc1 -t ext2
```
The important thing is just to make the directory /media/sdc1, then add the new info into the fstab. You can always chown the directory after a reboot.

---

### Post by NamedUser on 2007-09-28
> **Arthur Archnix said:**
> Hmm.. didn't think it would need it, but ok.
```
sudo mount -t ext2 /dev/sdc1 /media/sdc1
```
The important thing is just to make the directory /media/sdc1, then add the new info into the fstab. You can always chown the directory after a reboot.

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Arthur Archnix on 2007-09-28
sdc1 is your 750GB drive right? Which you said you created an ext2 filesystem on?
Try switching it up.
```
sudo mount -t ext2 /dev/sdc1 /media/sdc1
```
If that doesn't work, just for the hell of it toss ext3 in there instead.

---

### Post by NamedUser on 2007-09-28
Curious note: "sudo mount /dev/sdc /media/sdc1" mounted it.

---

### Post by Arthur Archnix on 2007-09-28
I don't understand that. But, assuming that you can see and read and write to your files, you should try adding the information into fstab. Since fstab goes by uuid all this nonsense won't be an issue.

EDIT: Oh, and before I read your post I found this elsewhere:
```
sudo fsck -y /dev/sdc
```

---

### Post by logos34 on 2007-09-28
yeah, fstab is the key.

Try this slight variation on Arthur's suggestion above:
> #/dev/sdc1
UUID=2903b9fa-c5b2-4258-83cb-364508c736d7 /media/sdc1 ext2 defaults 0 0 

or substitute **ext3**

---

### Post by Arthur Archnix on 2007-09-28
But if it's 0 0 it won't get fskd for errors, I can't imagine that's a good thing for an ext2 drive. Or am I misunderstanding the numbered options at the end here...

---

### Post by logos34 on 2007-09-28
yes, you're right, the final column is filesystem check option.  Just throwing out suggestions--anything--to get it to mount.  If sdc1 is external drive it might be better to have '0' (pass), otherwise it can cause boot problems if not connected.  Now that you mention it, why did OP format as ext2 instead of ext3 (journaling)?

---

### Post by NamedUser on 2007-09-29
> **logos34 said:**
> yes, you're right, the final column is filesystem check option.  Just throwing out suggestions--anything--to get it to mount.  If sdc1 is external drive it might be better to have '0' (pass), otherwise it can cause boot problems if not connected.  Now that you mention it, why did OP format as ext2 instead of ext3 (journaling)?

Actually... I don't even know... What's the difference, anyway?
Also, I still don't get this "/dev/sdc" works manually thing, 'cause for some reason it won't auto-mount. Anywho, I'm really tired *passes out*

---

### Post by Arthur Archnix on 2007-09-29
With a hard-drive that size you want journaling. In case of an improper shutdown it will just come back up without requiring a time consuming disk check (fsck = file system check). It also means you're less likely to lose data.

Normallly, you could just convert an ext2 to an ext3 without any problems. But this isn't really a normal situation here, if fdisk -l says the disk is called sdc1 and the only way to mount it is with sdc.

If it were me, I'd manually mount it using the sdc, copy the data to somewhere else, then reformat. It sounds like you didn't format it right the first time though, so try searching the forums for a few threads on that.

---

### Post by NamedUser on 2007-09-29
> **Arthur Archnix said:**
> With a hard-drive that size you want journaling. In case of an improper shutdown it will just come back up without requiring a time consuming disk check (fsck = file system check). It also means you're less likely to lose data.

Normallly, you could just convert an ext2 to an ext3 without any problems. But this isn't really a normal situation here, if fdisk -l says the disk is called sdc1 and the only way to mount it is with sdc.

If it were me, I'd manually mount it using the sdc, copy the data to somewhere else, then reformat. It sounds like you didn't format it right the first time though, so try searching the forums for a few threads on that.

Yeah, that's what I was about to do... luckily I haven't started to utilize the fact that I have the extra space yet.

---

