---
title: "USB HDD Filesystem Help Needed"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by aaron_summer on 2007-05-16
Good Day,

I have a pair of external USB HDD that are currently formated with NTFS. When I power on the drives in KDE the system detects the drive, however it does not appear to mount.

I want to use these drives for network storage and would like to know if I format the drives with a different filesystem (other than NTFS) will I be able to share them with Samba? And if so, which FileSystem should I use?

Thanks for any assistance you can provide.

Aaron S

---

### Post by LaRoza on 2007-05-16
You can use ntfs with Linux, but you need ntfs3g to write to it.

If you are not reading these drives with Windows, EXT3 would probably be best.

If you want to share things easily (nothing to install) use FAT32.

Windows can be made to read EXT3; however, I forget the utility.

---

### Post by dannyboy79 on 2007-05-16
ok, so you're using KDE correct? If your ultimate goal is to use them as Samba shares than it shouldn't matter what filesystem they are BUT since they are NTFS I am not completely sure how that works. You may or may not need to install NTFS-3g to be able to write to them thru samba but I don't think so. If you're going to be writing to them from your native computer Kubuntu and you don't have anything on them now, you might as well just format them as EXT3 for BEST linux compatibility or if you want to disconnect them ever and take them to a windows computer WITHOUT having to install the fs-driver in windows, than you could format them as FAT32 but you won't be able to store anything over 4gb in file size.

To recap,
NTFS-3g allows read and write in linux on NTFS drives that are hooked natively to the linux computer. (the driver has been around for a while but it is in beta form so you could have data loss. I am not saying that you will, I am merely saying that the NTFS-3g driver had to be reverse engineered by linux developers and it didn't come from microsoft so there may still be some issue. I can state from experience that I have used it to write 168gb of Xbox games from a ext3 drive to a external ntfs drive thru usb and it worked fine but the decision is still up to you.)

FAT32- linux and windows can both read and write to this filesystem without any extra drivers, the only downfall is that you can only write files to it that are less than 4gb in files size.

EXT3=linux writes to it great, it's the equivalent of NTFS in linux as it has journaling. Windows can read and write to it only by using a 3rd party driver called fs-driver. you install into windows, then use that fs-driver program to assign the ext3 drive a letter and then you can access it contents thru windows.

I am only pointing out the different filesystems  because you stated that these are external drives and if you ever wanted to take them somewhere with the data on  them I wanted to you to know the limitations of each of the filesystems.

I am pretty sure that you can mount any filesystem within samba and be able to write to it so you might as well try it out just leavintg them as NTFS to start out. When you plug them in, are you sure they don't mount or are you merely saying that they aren'ty showing up on your desktop? I just thought about something, I would think that the native computer has to be able to write to them in order to share them, so you'll ahve to install ntfs-3g and configure it using the ntfs-config. so do this:

sudo aptitude install ntfs-3g ntfs-config

then you would just go up into your pull down menu and look for ntfs-config and click on it, and tell it to make external drives writable. then you should be able to plug it  in and then type in this command to see what it returns

mount

you should see your external drives being mounted somewhere in /media/ and it should say fuseblk for the mount results. or you can type in 

ps aux

and you should see something like mount.ntfs-3g or something along those lines at the end of the ps aux cxommnad. let me know if i can help anymore.

---

### Post by aaron_summer on 2007-05-16
> **LaRoza said:**
> You can use ntfs with Linux, but you need ntfs3g to write to it.

If you are not reading these drives with Windows, EXT3 would probably be best.

If you want to share things easily (nothing to install) use FAT32.

Windows can be made to read EXT3; however, I forget the utility.

Thanks for the prompt response. I will format as FAT32.

Regards,

---

### Post by dannyboy79 on 2007-05-16
> **aaron_summer said:**
> Thanks for the prompt response. I will format as FAT32.

Regards,

if you're going to be using this as a backup drive, you won't be able to store any backup that's over 4gb in size! just an FYI

---

### Post by aaron_summer on 2007-05-16
I intend to use Samba to share the drives to the other windows systems on my network.

After the install of Ubuntu I did install the kubuntu-desktop (cause I need the GUI to learn). The drive did not appear on my desktop so that is why I assumed it did not mount.

Your suggestions are amazing and I will get back to you with the results!

Thanks again

---

### Post by aaron_summer on 2007-05-16
I will stay away from FAT32. Is there a utility to format the drives in windows as EXT3?

---

### Post by vanadium on 2007-05-16
If you are sharing from an ubuntu machine, no reason to format in fat32. To format a drive, use mkfs

sudo fdisk -l

will show you the name of the partition you want to format. Suppose it is /dev/sdc1

Unmount it if it is mounted:

sudo umount /dev/sdc1

The formatting utility is mkfs

sudo mkfs -t ext3 /dev/sdc1

-t ext3 tells to format in ext3. You can also choose msdos for old fat16, vfat for fat32, ext2, or other file systems. See man mkfs

---

### Post by dannyboy79 on 2007-05-16
well if you want a gui and are a little shy of the command line, you can always use gnome partition editor. just download it if it isn't installed. 

sudo aptitude intall gparted

then it'll show up under system, admin, 

and you'll have a gui you can format with.

---

### Post by aaron_summer on 2007-05-17
Your recommendation to install ntfs-3g worked perfectly!

Thank you all for your help I now have my external 320GB NTFS Drives mounted in Ubuntu!!

Needless to say I am incredibly impressed.

Thanks again

---

### Post by veloce on 2007-05-17
Whereas I'm having a lot of trouble mounting my usb external ntfs disk  even after installing ntfs-3g.

I get the following error message when attempting to mount:

```
Volume is scheduled for check.  Please boot into Windows TWICE, or use the 'force' mount option.
```

i have attached it to a windows machine and booted twice - I think this would only work if it was connected by ide cable not usb

When I try the 'force' mount option, I get 

```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/SwannMP3 -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /mnt/SwannMP3: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (SwannMP3)

```

Not sure what to try next, any ideas?

EDIT: Doh!  I created the folder /media/SwannMP3 and it worked (of course).

---

### Post by dannyboy79 on 2007-05-17
> **veloce said:**
> Whereas I'm having a lot of trouble mounting my usb external ntfs disk  even after installing ntfs-3g.

I get the following error message when attempting to mount:

```
Volume is scheduled for check.  Please boot into Windows TWICE, or use the 'force' mount option.
```

i have attached it to a windows machine and booted twice - I think this would only work if it was connected by ide cable not usb

When I try the 'force' mount option, I get 

```
sudo mount -t ntfs-3g /dev/sdb1 /mnt/SwannMP3 -o force
WARNING: Dirty volume mount was forced by the 'force' mount option.
fusermount: failed to access mountpoint /mnt/SwannMP3: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdb1 (SwannMP3)

```

Not sure what to try next, any ideas?

EDIT: Doh!  I created the folder /media/SwannMP3 and it worked (of course).

just so you are aware, the reason that this happend is because somehow the drive was not unplugged from windows properly so it's journal was messed up and linux ntfs-3g driver doesn't know how to fix it like it know hoe to fix ext3 journal mess ups. so all it wanted you to do was to hook it up to windows and use the "remove device" for the external usb ntfs driver using the lower right hand corner, this will ensure that the journal for the drive is written to it before windows ejects it. so there was no need to use the force option if you haev a windows install. simply plug it into a usb port, maybe open windows explorer and write a .txt file to the drive or jsut something small, then use the proper means to "eject" the drive from windows and all would have been fine for the ntfs-3g driver.

---

### Post by gn2 on 2007-05-17
If you install Automatix, one of the options it gives is an NTFS / Fat32 auto-mounter which mounts and makes any connected NTFS or Fat32 partition or drive writeable.

It's under the "Miscellaneous" category.

[www.getautomatix.com](www.getautomatix.com)

---

### Post by veloce on 2007-05-17
> **dannyboy79 said:**
> just so you are aware, the reason that this happend is because somehow the drive was not unplugged from windows properly so it's journal was messed up and linux ntfs-3g driver doesn't know how to fix it like it know hoe to fix ext3 journal mess ups. so all it wanted you to do was to hook it up to windows and use the "remove device" for the external usb ntfs driver using the lower right hand corner, this will ensure that the journal for the drive is written to it before windows ejects it. so there was no need to use the force option if you haev a windows install. simply plug it into a usb port, maybe open windows explorer and write a .txt file to the drive or jsut something small, then use the proper means to "eject" the drive from windows and all would have been fine for the ntfs-3g driver.

Thanks for that.  Unfortunately, I need to do more than just get it to eject nicely.  Now that it is in this state, it wants to run a the check.  I tried to do this from a virtual machine, but no go.  So I need to find a windows machine that I can log into with administrator priviledges to perform the test.  I'll get to that.

This is all because the disk was in a machine that died and has been "rescued" to the external usb drive, but has a whole lot of data files that we want to continue having access to.

---

