---
title: "Writing to an NTFS external H/D"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by davesmith on 2006-11-22
I have an NTFS external USB H/D and 6.10 Edgy installed on a Toshiba A30 laptop. I want to write some data to the drive, so I installed ntfs-g3 and tried, but I get an error message telling me that I do not have permissions to write to it. Can someone explain how to do this properly? I thought I had understood the permissions bit in the wiki, but it seems not! Thanks in advance,

Dave

---

### Post by taurus on 2006-11-22
The question is how did you mount your external harddrive?  Did you try to mount it by hand, from a terminal, or did you try to mount it through /etc/fstab?

---

### Post by bodhi.zazen on 2006-11-22
> **davesmith said:**
> I have an NTFS external USB H/D and 6.10 Edgy installed on a Toshiba A30 laptop. I want to write some data to the drive, so I installed ntfs-g3 and tried, but I get an error message telling me that I do not have permissions to write to it. Can someone explain how to do this properly? I thought I had understood the permissions bit in the wiki, but it seems not! Thanks in advance,

Dave

Assuming the external HD is /dev/sda1:

unmount the device

Re-mount with:```
sudo mount /dev/sda1 <mount_point> ntfs-3g -o user,umask=000
```

OR

edit fstab```
gksudo gedit /etc/fstab
```Add a line:> /dev/sda1 <mount_point> ntfs-3g users,auto,uid=1000,gid=1000,umask=007 0 0Now mount the device:```
mount /dev/sda1
```

---

### Post by davesmith on 2006-11-22
I mounted the drive initially by plugging it into a usb port. The system recognised it and i can copy from the drive to Nautilus, but i dont have permission to write to it.

Taurus, when i tried to edit fstab, after I saved the edited file Gnome crashed and I lost my desktop and the bar at the top with applications, places, system etc.  It took me an hour to work out how to re-start in safe mode and then re-install my saved fstab file.

Now ive tried to unmount then re-mount using your code <sudo mount /dev/sda1 <mount_point> ntfs-3g -o user,umask=000> and this is what I get in the terminal

<sudo mount /dev/sda1 /media/backup ntfs-3g -o user,umask=000

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount.>

Oh dear, i still cant write to it.....!!@<S!!!

---

### Post by bodhi.zazen on 2006-11-22
Ooops ```
sudo mount -t ntfs-3g /dev/sda1 <mount_point> -o user,umask=000
```

---

### Post by davesmith on 2006-11-22
well thanks, i tried that command and here is what the terminal said:-

<sudo mount -t ntfs-3g /dev/sda1 /media/backup -o user,umask=000

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.>

It seems to think that I have windows installed, but I dont have dual boot. I blew windows away, reformatted my laptop H/D and did a clean install of 6.10 Edgy

---

### Post by houstonbofh on 2006-11-22
This thread is a very good canadate for a FAQ, like the ubuntuguide.  Especially with larger thumb drives comming out that are NTFS.

---

### Post by bodhi.zazen on 2006-11-22
> **davesmith said:**
> well thanks, i tried that command and here is what the terminal said:-

<sudo mount -t ntfs-3g /dev/sda1 /media/backup -o user,umask=000

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) **Run 'ntfsfix' on Linux** which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.>

It seems to think that I have windows installed, but I dont have dual boot. I blew windows away, reformatted my laptop H/D and did a clean install of 6.10 Edgy

Well, ntfsfix it is then....```
ntfsfix /dev/sda1
```

You may need sudo.

---

### Post by bodhi.zazen on 2006-11-22
> **houstonbofh said:**
> This thread is a very good canadate for a FAQ, like the ubuntuguide.  Especially with larger thumb drives comming out that are NTFS.

[Partition basics](http://ubuntuforums.org/showthread.php?t=282018)

[How to fstab](http://ubuntuforums.org/showthread.php?p=1653968#post1653968)

---

### Post by davesmith on 2006-11-22
thanks for your support on what seems to be proving a difficult night...

I tried ntfsfix, and here is what the terminal said:-

<laptop:~$ ntfsfix /dev/sda1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr... 
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... FAILED
Error setting volume flags.>

hmmmm....could be time for a beer and a think about this. Seems to me that lots of windows users are gonna have this issue when they d/l and install the excellent 6.10 Edgy, but wanna copy data to external memory. Is there still some windows code on this laptop maybe?

---

### Post by bodhi.zazen on 2006-11-22
> **davesmith said:**
> thanks for your support on what seems to be proving a difficult night...


Interesting. Sorry :( , I have already told you more then I know ! :p

---

### Post by bodhi.zazen on 2006-11-22
> **davesmith said:**
> thanks for your support on what seems to be proving a difficult night...

I tried ntfsfix, and here is what the terminal said:-

<laptop:~$ ntfsfix /dev/sda1
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr... 
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... FAILED
Error setting volume flags.>

hmmmm....could be time for a beer and a think about this. Seems to me that lots of windows users are gonna have this issue when they d/l and install the excellent 6.10 Edgy, but wanna copy data to external memory. Is there still some windows code on this laptop maybe?

[Hey, check this thread](http://forum.linux-ntfs.org/viewtopic.php?t=290&sid=d6ec34afc166412da6cff0624babbcb8)

---

### Post by davesmith on 2006-11-23
Well thanks to the forum for an interesting evening last night:}}

The solution to the problem was to go out this morning and buy a new Seagate 320G external H/D, take it out of the box and plug it in!  Hey presto, Edgy mounted it and i have full read write access! Amazed.....but very happy.

Next: how to convert ntfs....

---

### Post by taurus on 2006-11-23
You mean how to convert your new harddrive to NTFS!  Well, you first need to unmount it, install gparted, and use it to format it to NTFS.  Then, install ntfs-3g so you can write to it.  Edit /etc/fstab so it would be mounted every time you boot, and mount it again...

---

### Post by davesmith on 2006-11-23
Thanks Taurus.....the new H/D is Fat32.  Which is fastest, Fat32, ntfs or Ext3? I have a large collection of astronomy images and data, 29000 files, and obviously the fastest system is what I need

---

### Post by taurus on 2006-11-23
Do you want to share that drive with XP?  If yes, then leave it as NTFS but if you only have Ubuntu on that machine, then format it as ext3...

---

### Post by davesmith on 2006-11-23
I dont have XP on the machine now, I reformatted the internal h/d and did a new, clean install of Edgy earlier this month. Ive burned my bridges and ive got to learn Ubuntu and the new h/d will be dedicated to Edgy

I tried to use parted from the terminal to format the new h/d but it said im not a superuser.  Do you have time to talk me through converting it to Ext3?  Any help would be appreciated!

---

### Post by taurus on 2006-11-23
Try putting a sudo in front of whatever command you want to use.  Assuming that new harddrive is /dev/hdb1, you would do

```
sudo mke2fs -j /dev/hdb1
```
Please be sure you know where your new harddrive is because I don't want you to format your current partition and you have to reinstall Edgy over again...  If not sure, paste the output of this command here.

```
sudo fdisk -l
```

---

### Post by davesmith on 2006-11-23
i think the new h/d is sda1

here is the output for sudo fdisk -l

sudo fdisk -l


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4688    37656328+  83  Linux
/dev/hda2            4689        4864     1413720    5  Extended
/dev/hda5            4689        4864     1413688+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by davesmith on 2006-11-23
so, to format the new external h/d to ext3 the command would be

sudo mke2fs -j /dev/sda or 

sudo mke2fs -j /dev/sda1

??

---

### Post by taurus on 2006-11-23
> **davesmith said:**
> i think the new h/d is sda1

here is the output for sudo fdisk -l

sudo fdisk -l


Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4688    37656328+  83  Linux
/dev/hda2            4689        4864     1413720    5  Extended
/dev/hda5            4689        4864     1413688+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    c  W95 FAT32 (LBA)

Yip.  Your new drive is a SATA so it is a /dev/sda1 then.  So, 

```
sudo mke2fs -j /dev/sda1
```

---

### Post by davesmith on 2006-11-23
ok, i typed sudo mke2fs -j /dev/sda1

and this is the output from the terminal

mke2fs 1.39 (29-May-2006)
/dev/sda1 is mounted; will not make a filesystem here!

---

### Post by taurus on 2006-11-23
You need to unmount it first before you can format it.  

```
sudo umount /dev/sda1
sudo mke2fs -j /dev/sda1
```

---

### Post by davesmith on 2006-11-23
sudo umount /dev/sda1
sudo mke2fs -j /dev/sda1

that worked!

now, how do i mount it again?

sudo mount /dev/sda1 ......did not work, terminal output said the following

mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by taurus on 2006-11-23
I assume you want to mount it to /media/share so you need to edit your /etc/fstab so it will be mounted automatically every time you boot Ubuntu.  From a terminal, run

```
gksudo gedit /etc/fstab
```
Then, add the following line to the end of it.

```
/dev/sda1   /media/share   ext3   defaults   0   1
```
Save it and then create a mount point and mount it...

```
sudo mkdir /media/share
sudo mount -a
df -h <-- you should see /dev/sda1 mounted on /media/share now.
```

---

### Post by davesmith on 2006-11-23
Taurus, you are most uncommonly kind, in the true spirit of Ubuntu!

I think it&#347; worked, the output of df -h......

laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   16G   18G  47% /
varrun                998M   80K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                998M     0  998M   0% /dev/shm
lrm                   998M   18M  981M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             294G  193M  279G   1% /media/share

Does this look normal, and now do I always have to keep the new drive connected when i boot up?

---

### Post by davesmith on 2006-11-23
Does this look normal, and now do I always have to keep the new drive connected when i boot up?

I asked this, because it wont let me eject the new drive!

---

### Post by taurus on 2006-11-23
> **davesmith said:**
> Taurus, you are most uncommonly kind, in the true spirit of Ubuntu!

Thanks for the kind words.  You now owe me a brand new 320GB harddrive...  :mrgreen:  :twisted:  ](*,) 

> I think it&#347; worked, the output of df -h......

laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   16G   18G  47% /
varrun                998M   80K  998M   1% /var/run
varlock               998M     0  998M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                998M     0  998M   0% /dev/shm
lrm                   998M   18M  981M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1             294G  193M  279G   1% /media/share

Does this look normal, and now do I always have to keep the new drive connected when i boot up?
Everything looks good.  Do you intend to remove it every now and then while you are using/booting Ubuntu?

---

### Post by taurus on 2006-11-23
> **davesmith said:**
> Does this look normal, and now do I always have to keep the new drive connected when i boot up?

I asked this, because it wont let me eject the new drive!
If you want to remove it while Ubuntu is still running, you NEED to unmount it first before you can unplug it.  Please don't just unplug it like you would do with the other OS because doing that can damage your data on that drive...

```
sudo umount /dev/sda1
```

---

### Post by davesmith on 2006-11-23
PC World here in the UK are doing a xmas deal on the Seagate, the h/d was £89.99....i guess thats about $200 i owe you:}}

I would like to be able to eject the new drive when im using ubuntu, because i will mainly be using it to back-up data and there is no need to have it connected all the time

---

### Post by davesmith on 2006-11-23
[QUOTE Please don't just unplug it like you would do with the other OS because doing that can damage your data on that drive...

```
sudo umount /dev/sda1
```[/QUOTE]

ok, the unmount command works just fine, I assume that to mount it one uses

sudo mount /dev/sda1

which seems to work ok too

---

### Post by taurus on 2006-11-23
$200 for a 320GB harddrive!!!  That is expensive...

Since you plan to mount and unmount that harddrive, I recommend you remove the line for it in /etc/fstab (or you can place a # in front of it to comment it out) so the system won't look for it when it boots.  Then, plug it in and mount it when you want to use it and unmount it if you want to remove it.

---

### Post by davesmith on 2006-11-23
ok, thanks once again!

one last question...it was  320G h/d when i started.  Right clicking on the drive icon on my desktop gives a menu with <properties> This says i have 278G of free space. What happened to the other 42G?

---

### Post by taurus on 2006-11-23
When you convert your drive to ext3, 5% of it is reserved for journaling.  Also, 320GB is not really 320GB because of the bit and byte thing...  It's more like 290GB or so.

---

### Post by davesmith on 2006-11-23
Ahem....sorry...i just tried to write a file to the new h/d and i get an error message, i dont have permission....what might be wrong now?

---

### Post by taurus on 2006-11-23
Just change the permissions for /media/share so everyone can write to it.  Right now, only root can write to it...

```
sudo chmod 777 /media/share
```

---

### Post by davesmith on 2006-11-23
Thanks, that seems to have done the trick

<chuckles with glee>

I feel that I have learned something usefull!

---

### Post by taurus on 2006-11-23
> **davesmith said:**
> Thanks, that seems to have done the trick

<chuckles with glee>

I can smell a new nVidia card coming too...  At this rate, I can probably put a new system together in no time!!!  :mrgreen: 

> I feel that I have learned something usefull!
Enjoy and good luck.

---

### Post by lukem on 2006-11-23
Thanks to you both!  I learned something too and appreciate you both sharing your time.  I love reading this forum.

---

