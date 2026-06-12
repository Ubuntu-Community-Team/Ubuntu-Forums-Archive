---
title: "[SOLVED] got an external harddrive...now what?"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by kyalee on 2008-03-28
Okay, I finally got an external hard drive. Beyond Micro 80Gb 3.5". Took it out of the box, plugged it in, and Ubuntu recognized "New Volume" immediately. Now, I can see inside of the drive, but I can't do anything with it like write to it or create new folders or anything.

I'm assuming I have to format it, but I have no idea how. It came with a CD, but it's for Windows. I've done a search, but I can't seem to find anything relevant. 

Help?

---

### Post by stefangr1 on 2008-03-28
Congratulations with your new drive!

What you can do is:
(1) look up the name of your device with the command "fdisk -l"
(2) partition it using - for example - gparted, with the command "gparted /dev/sd#"

---

### Post by jan quark on 2008-03-28
if you are going to use this driver only with linux then format it to ext3

you can use the live CD and then the application gparted
[http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted)

please before we start to partition and format things make a back up of your important data
and please post the output of these terminal commands
```

mount
sudo fdisk -l
```

---

### Post by kyalee on 2008-03-28
fdisk - l yeilds

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

```

I would like to be able to use it with both Windows and Linux. This computer is Linux-only, but I might be able to squeeze some of the purchase price out of my dad if I offer to back up data on his (Windows) computer too. ;)

---

### Post by virtuallinux on 2008-03-28
hmm... looks like you've got an NTFS volume. All versions of Ubuntu previous to Gutsy don't have built in support for writing to NTFS.  If you're not using Gutsy, you've got a couple of options.  You can:

1) Format the drive to something like FAT32, which will work for both Ubuntu and Windows
2) Install NTFS 3g, a utility which allows Ubuntu (and linux in general) to write to NTFS partitions
3) Upgrade to Gutsy, it has NTFS support built in

---

### Post by kyalee on 2008-03-28
> **jan quark said:**
> 
please before we start to partition and format things make a back up of your important data


I don't have any data on the external. Hopefully I don't screw up the internal. Backing up data from that drive is the whole reason I got the external. LOL.

---

### Post by kyalee on 2008-03-28
> **virtuallinux said:**
> hmm... looks like you've got an NTFS volume. All versions of Ubuntu previous to Gutsy don't have built in support for writing to NTFS.  If you're not using Gutsy, you've got a couple of options.  You can:

1) Format the drive to something like FAT32, which will work for both Ubuntu and Windows
2) Install NTFS 3g, a utility which allows Ubuntu (and linux in general) to write to NTFS partitions
3) Upgrade to Gutsy, it has NTFS support built in

Well, I'd rather not upgrade to Gutsy. I got the external in part so I could back up everything before doing the upgrade. (I know the chances of losing my data b/c of the upgrade are slim, but I didn't want to take a chance.

So I guess it'll be either option 1 or option 2. Hmm...

---

### Post by Inxsible on 2008-03-28
try installing ntfs-3g, its pretty stable in Feisty too.

---

### Post by kyalee on 2008-03-28
Okay, I unmounted the volume and unplugged the USB cable, and installed NTFS 3g. Then I opened NTFS and clicked the "enable write support for external device" button. But when I plugged it back in, it's not mounting the drive. The first time the "New Volume" just showed up on my desktop like it does when I plug in my flash drive. Now, nothing. :-/

Also, now when I try to open NTFS I get a message saying "Error : An error occured when trying to initialize HAL. Can't search for new partition." before the box letting me check/uncheck the "enable write support for external device" option opens.

---

### Post by kyalee on 2008-03-28
fdisk -l still gives me 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

```

but df -h gives

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              54G   33G   19G  65% /
varrun                237M  112K  236M   1% /var/run
varlock               237M     0  237M   0% /var/lock
procbususb            237M   96K  236M   1% /proc/bus/usb
udev                  237M   96K  236M   1% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   33M  204M  14% /lib/modules/2.6.20-16-generic/volatile

```

It looks like it's not there. Weird. But then why is it showing up when I do fdisk -l?

---

### Post by Inxsible on 2008-03-28
are you using admin privs on one command and not on the other ?

i m not sure if that's the issue but you could try the commands with sudo on both of them.

---

### Post by kyalee on 2008-03-28
sudo fdisk -l

```
Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7126    57239563+  83  Linux
/dev/hda2            7127        7301     1405687+   5  Extended
/dev/hda5            7127        7301     1405656   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

```

sudo df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              54G   33G   19G  65% /
varrun                237M  112K  236M   1% /var/run
varlock               237M     0  237M   0% /var/lock
procbususb            237M   96K  236M   1% /proc/bus/usb
udev                  237M   96K  236M   1% /dev
devshm                237M     0  237M   0% /dev/shm
lrm                   237M   33M  204M  14% /lib/modules/2.6.20-16-generic/volatile

```

Edit: So...now fdisk is just showing the internal 60GB harddrive. So the external still isn't mounted, but at least that makes more sense. Um, I think.

---

### Post by Inxsible on 2008-03-28
fdisk is showing you the external drive ( the 80 gb one?)

its just not mounted. you can use pmount to mount external drives.

```
pmount /dev/sda1 MOUNT_POINT
```change the MOUNT_POINT to any name you want to give, and a new folder will be created under /media. Make sure you DO NOT already have a folder by that name, since pmount actually creates a new folder.

---

### Post by kyalee on 2008-03-28
Okay, now it's showing up. Thanks!

But, bleh, I'm back where i started. I can see it, but I can't do anything to it. I think maybe because I had the NTFS -3g control turned off when I finally got it mounted. Maybe if I unmounted it and then tried again with it turned on?

How do you unmount via the command line? The GUI is not letting me unmount the way I usually do. It's saying that since it was mounted manually, it's not controlled by HAL. (2001 flashbacks anyone?)

---

### Post by Inxsible on 2008-03-28
the command would be ```
pumount /media/MOUNT_POINT
```but it should also unmount if you right click it and select unmount. Strange !!

It could also be a permissions issue since you cannot write to it.

Try this```
sudo chown -R <your username>:<your group> <path to mount point>
```Assuming your username to be kyalee  the command would be
```
sudo chown -R kyalee:kyalee /media/MOUNT_POINT
``` Of course you need to change the MOUNT_POINT to whatever you created and also change the group if you have ever changed it.

---

### Post by kyalee on 2008-03-28
Still can't write to it. 

```
<my username>@<my username>-desktop:~$ sudo chown -R <me>:<me> /media/External
chown: changing ownership of `/media/External/System Volume Information/MountPointManagerRemoteDatabase': Read-only file system
chown: changing ownership of `/media/External/System Volume Information': Read-only file system
chown: changing ownership of `/media/External': Read-only file system

```

---

### Post by virtuallinux on 2008-03-28
Well, if NTFS 3g is turned on and not working, you may want to reinstall it, otherwise, you could try and reformat.  Also, I think you may have to turn NTFS 3g on after the drive is mounted, for what it's worth.
Aside from that, you may want to try and reformat it.

---

### Post by kyalee on 2008-03-28
When I unmounted it via the command line and then plugged the USB in again, I got the attached message. I can mount it via the command line, but it doesn't want to auto mount.

The weird thing is, I have never had this thing hooked up to a windows machine (just opened the box an hour or so ago), so why is it telling me to do things with windows? 

Hmm. Maybe I should uninstall the NTFS Config tool and try another approach like formating the drive to FAT32.

---

### Post by Inxsible on 2008-03-28
connect it to windows and do the 'Safely remove hardware'  on it.

then connect it to ubuntu again.it should work after that.

---

### Post by Inxsible on 2008-03-28
aha !!

looks like thats the issue. and no you do not need to re-install ntfs-3g or format it to fat32. drives are mostly configured for windows. just do the safely....and connect back to ubuntu.

---

### Post by kyalee on 2008-03-28
How odd, but it seems to have done the trick. Working now, and I'm in the process of transferring some files. I guess this is why I'm holding off on converting my laptop to Linux. I love my Ubuntu, but having a windows machine around does come in handy at times. Ah well.

Thanks very much. :D

---

### Post by Inxsible on 2008-03-28
Cool. glad to know it works now :)

---

