---
title: "[SOLVED] Cant see my external drive"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-21
I am currently setting up my first real try with Ubuntu, it looks good but I need to iron out a few issues. This one seems odd. When I open device manager I can see my seagate external drive, which is used for all my data only, and I can also see the USB externally  powered hub that connects it to the computer, however when I go into 'places' 'computer' I cannot find the drive. I can double click 'file system' and access the second on board ntfs hard drive, that contains all my windows XP programs etc, so the installed ntfs-3g is working fine. 

Can anyone throw some light on this for me?

Douglas

---

### Post by ubrox on 2008-03-21
execute the following command at any shell

cat /proc/partitions

See if the displayed partitions make sense and if the partitions from external drive are showing.

You should see:
sda
sda1 etc

for your internal disk

sdb
sdb1 etc for you external disk assuming you have only one internal disk.

instead of sda, it can be hda, hdb also. Your CD ROM will not show here.

Also, what file system do you have on the external drive?

Do you have any other USB devices connected? If yes, do they work?

thanks,
Kalyan

---

### Post by tropdoug on 2008-03-21
This is what I got returned,   

8     0   78150744 sda
   8     1   78140128 sda1
   8    16   78150744 sdb
   8    17   75119908 sdb1
   8    18          1 sdb2
   8    21    3028221 sdb5
   8    32  312571224 sdc
   8    33  312568641 sdc1

Sda is the linux hard drive, sda1 is the XP hard drive, both internal. sdb1 is the external drive. I am not sure what the other ones are. 

Douglas

---

### Post by tropdoug on 2008-03-21
Sorry kalyan the external drive is an ntfs file system like the XP drive.
thanks 
Douglas

---

### Post by herbster on 2008-03-22
Paste the output of:

```
df -h
```

and

```
sudo fdisk -l
```

Of course with the external drive connected.

---

### Post by tropdoug on 2008-03-22
Here we go, I was wrong in previous post the external drive I am trying to access is a Fat32, not ntfs. Its dev/sdc, and contains all my documents,music etc, Thanks for the help.


Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1              71G  2.1G   65G   4% /
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   88K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              75G   22G   53G  30% /media/disk

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eab4176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by herbster on 2008-03-22
Okay, can you also paste your fstab:

```
cat /etc/fstab
```

Also, is your external drive one you pick up and take elsewhere or is it always connected to your box?

Go to System > Preferences > Removable Drives and Media, what is checked for Removable Storage?

---

### Post by oedha on 2008-03-22
what if.......open terminal then
sudo mkdir /media/sdc1
sudo mount /dev/sdc1 /media/sdc1
after this can you see the icon appear or even in places ?
if yes...later on you have to put something on your fstab....

---

### Post by tropdoug on 2008-03-22
Herbster

douglas@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=89c666d3-ffd5-454d-86af-07338cbc19b4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=a502e511-361d-4b95-8a18-4e8115eb359a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
douglas@desktop:~$ A

Yes the drive can be turned off and taken elsewhere, although I usually don't at this stage, it is left connected. 

In the removable media the top three boxes are ticked, 

mount removable drives when hotplugged
mount removable media when instered
browse removable media when inserted

---

### Post by tropdoug on 2008-03-22
oedha

this is what I got

douglas@desktop:~$ sudo mkdir /media/sdc1
[sudo] password for douglas:
douglas@desktop:~$ sudo mount /dev/sdc1 /media/sdc1
mount: you must specify the filesystem type
douglas@desktop:~$ 

so would the command be 

sudo mount /dev/sdc1 /fat32 media/sdc1

?????

---

### Post by oedha on 2008-03-22
sudo mount -t auto /dev/sdc1 /media/sdc1

Edit :
sudo mount -t vfat /dev/sdc1 /media/sdc1

then open your fstab :==> gksudo gedit /etc/fstab

insert below line
/dev/sdc1   /media/sdc1   vfat   user,fmask=0111,dmask=0000   0   0

details :==> [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by tropdoug on 2008-03-22
Hmmm
it's still telling me to specify the filesystem type?

---

### Post by whitewizardcoder on 2008-03-22
What version of ubuntu are you using?  I have a Seagate external drive, and in Gutsy, I needed to power it down (as in, pull the power cord out of the drive) and then power it up again before connecting it for Gutsy to correctly recognize it.  Hardy fixes this, however it's still in beta so I wouldn't necessarily recommend using it as of right now.

---

### Post by garyed on 2008-03-22
try this , just a shot. 
sudo mount  -t  vfat  /dev/sdc1  /media/sdc1

---

### Post by tropdoug on 2008-03-22
Okay 

I have a new icon in media but this is weird, I have 

cdrom, thats easy.
'disk' which is the windows HD 
sdb2 which is the Ubuntu HD
and now sdc1 which wasn't there before, but is a copy of sdb2 - its the same drive. 

When I power down the drive, and watch 'device manager' it disappears, and when I power up, it reappears, so obviously the system is seeing it, but not as a file that I can access yet. 

I do love a challenge. :lolflag:

thanks for all the help so far, please keep them coming, I know it's something simple.

The version is 7.10, (I think that's gutsy? isn't it)

---

### Post by herbster on 2008-03-23
tropdoug, you more than likely don't need to add a line to your fstab as this is not a permanent/fixed drive to your box, and if anything it would be better suited to your mtab. The fstab suggestion won't work because you require the UUID if it's a USB drive and is in your fstab.

To keep things simple, make sure your fstab is as it was in your previous post where I asked you to paste it.

Curious, have you rebooted since you plugged it in initially? Try turning it off, rebooting, then once you're back in Ubuntu and ready to go, hit Places > Computer and see what's there. You can right click on the visible icons and hit Mount if you do see it. If you are sure it's not there, power it down and plug it into a different USB port on your box, then power again and see if nautilus (the file browser) shows the icon.

---

### Post by tropdoug on 2008-03-23
Herbster

OK my fstab is back to where it started. I rebooted, powered up the drive, but it doesn't appear as an icon in the nautilus. It does appear in device manager. 

I attached it to a main usb port on the back of the box, rather than through a hub, re booted, powered up, same result. 

What is confusing me is that device manger is correctly seeing it, but apparently no other part of the file system is. 

Further suggestions will be eagerly followed. 

Douglas:confused:

---

### Post by herbster on 2008-03-23
Well we've eliminated that, you don't want to fudge the fstab and all when it could be as simple as a reboot/usb port issue (which it is many times).

And what does this now give (paste output):

```
sudo mkdir /media/stuff && sudo mount /dev/sdc1 /media/stuff
```

---

### Post by tropdoug on 2008-03-23
mount: you must specify the filesystem type

---

### Post by tropdoug on 2008-03-23
Ok, I did 

sudo mount -t vfat /dev/sdc1 /media/stuff

because the dir had been created, and right now I have the busy thingy ma bob going round and round. No icons yet. (it is a 320 gig drive, with probably 60 gig of lectures., talks and presentations on it as well as music, would that make it take a long time to load into the dir?)

---

### Post by tropdoug on 2008-03-23
YAHOOOOO ! Herbster you little Beautyyyy (as we say here in tropical north Australia) its there, so please can you tell me, in the future am I going to have to manually mount this drive each time I want to access it, and if so is the command

sudo mount -t vfat /dev/sdc1 /media/stuff

and then just wait for it to load?

Hey thanks a million just a few more things to iron out, and I will be up and away with Ubuntu, hopefully never to return to XP or Vista

Douglas  :guitar:  :popcorn:

---

### Post by herbster on 2008-03-23
Glad ya got it going. Hit Places > Computer, now you see the icon right? For "stuff". Now right click it, can you see Mount or Unmount Volume there? You should be able to just click either whenever you want to mount/unmount it.

---

