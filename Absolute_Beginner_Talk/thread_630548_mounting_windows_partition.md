---
title: "mounting windows partition"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by yuffie8 on 2007-12-03
hey, complete rookie here, is it possible to mount my windows partition ? When i click on the volume in 'computer' file browser i get:-
 'Cannot mount volume:
 You are not privileged to mount this volume.' 

I am the computer admin on windows so i dont know what this is all about ...

Any help would be greatly appreciated, i checked the other threads before i posted and none have what im looking for. Thanks

---

### Post by lvleph on 2007-12-03
did you try sudo? EDIT: I guess not if you were doing it through the GUI.

you will need ntfs-3g and ntfs-config.

```
sudo apt-get install ntfs-3g ntfs-config
```


EDIT: It looks like you have ntfs-3g if in the GUI you see the partition.

Try this in the terminal
```
sudo mount -a
```

---

### Post by yuffie8 on 2007-12-03
hey, thanks for the quick reply, i just typed in the code

this is what i got when i typed it in :```
yuffie@yuffie8:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
ntfs-3g set to manual installed.
ntfs-config is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni mysql-common libgtk-jni libmysqlclient15off
  ruby1.8 libcairo-java libglib-jni python-qt3 ruby libbcprov-java python-sip4
  libglib-java libifp4 libpq5 libgtk-java libruby1.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
yuffie@yuffie8:~$ 

```

i closed terminal and tried to access it again and it said the same thing again.


EDIT: typed sudo mount -a 
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/fumoffu -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/fumoffu ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

```

---

### Post by anaconda on 2007-12-03
actually you only need ntfs-3g if you want to get read/write access to your windows partition.

If reading it is enough you can simply mount your windows partition from terminal with eg:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sdXX /media/windows
```

You just need to change the XX to whatever is your windows partition.. it can be eg. sda1 sdb1 ..

with
sudo fdisk -l
will show the partitions with their correct names  and some info of them..

---

### Post by yuffie8 on 2007-12-03
hey, this is the readout i get from sudo fdisk -1

```
Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3769    30274461    7  HPFS/NTFS
/dev/sda2            3770        4943     9430155   83  Linux
/dev/sda3            4944        4998      441787+   5  Extended
/dev/sda5            4944        4998      441756   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bb1edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    b  W95 FAT32
```

---

### Post by lvleph on 2007-12-03
It looks to be sda1 from the output to sudo mount -a. However, I don't know what to do about that message it gave you.

EDIT: it is fdisk -l not -1. Anyway, the drive is definitely sda1. The problem seems to be a dirty drive. You need to boot into windows and then 

windows button+r 
type cmd  and then enter 
type chkdsk /r at the command prompt 
reboot to windows.
It will check that partition and clean it up. 
boot back into ubuntu, and hopefully everything works.

---

### Post by JohnPta on 2007-12-03
I am also a new new in this environment however try this one.
Go to "**Places**" in my case on the top Panel. Click (sorry for that windows expression) on "**Computer**"  than you will see the windows HD. As soon as you click on it the system will ask you for the password. When the system not asks you for a password you do not have the rights. Get out and login again as a user with the root privileges. Than it should work.

---

### Post by yuffie8 on 2007-12-03
no worries mate, thanks! hopefully someone else can help

---

### Post by lvleph on 2007-12-03
Looks like I edited my post after you read it so...

It is fdisk -l not -1. Anyway, the drive is definitely sda1. The problem seems to be a dirty drive. You need to boot into windows and then

windows button+r
type cmd and then enter
type chkdsk /r at the command prompt
reboot to windows.
It will check that partition and clean it up.
boot back into ubuntu, and hopefully everything works.

---

### Post by yuffie8 on 2007-12-03
thankyouthankyouthankyou!

worked a treat, thanks guys.
I went into windows and 'cleaned' it, cheers!

---

### Post by lvleph on 2007-12-03
Yeah, you don't want to mount dirty drives you don't know where they have been. You may catch something. :)

---

### Post by mkquist on 2007-12-05
Had a similar problem.  Tried the 'boot to windows, chkdsk' thing.  After hours of chkdisk, on just one drive got tired of waiting and just shut it down.  After a couple of reboots, problem seems to have resolved itself.  Window drives are mounted and on my desktop like they should be.

---

### Post by Jeztastic on 2007-12-08
Hi, I am not sure I fully understand the mounting thing either. I am mounting the drives via the file browser in Gutsy. They show up in the left hand navigation, and I left click > mount. Enter password, mounted. This gives me read and write access. However, I have to do this each time I log on. Is this usual, or do I need to follow a tutorial to permanantly mount them? What is happening with me does not seem to correspond to any other posts/tutorials I have read.

---

### Post by thelatinist on 2007-12-08
> **Jeztastic said:**
> Hi, I am not sure I fully understand the mounting thing either. I am mounting the drives via the file browser in Gutsy. They show up in the left hand navigation, and I left click > mount. Enter password, mounted. This gives me read and write access. However, I have to do this each time I log on. Is this usual, or do I need to follow a tutorial to permanantly mount them? What is happening with me does not seem to correspond to any other posts/tutorials I have read.

1) Use the following command to create a mount point for this drive (change *mountpoint* to a name that is not already in use and will be easy to recognize and remember):

```
sudo mkdir /media/*mountpoint*
```

2) Use the following command to back a back up of your fstab file in case something goes wrong:

```
sudo cp /etc/fstab /etc/fstab.bak
```

3) Use the following command to open fstab for editing:

```
sudo gedit /etc/fstab
```

Add one of the following line (depending on filesystem type) to your fstab to cause it to automatically mount (replace *sda#* with the name of the device you wish to mount and *mountpoint* with the mountpoint you created in step 1):

**For ext3:**
```

/dev/*sda#* /media/*mountpoint* ext3 defaults,errors=remount-ro 0 1
```

**For NTFS:**
```
/dev/*sda#* /media/*mountpoint* ntfs-3g defaults,nls=utf8,umask222 0 0
```

**For Fat32 or Fat16:**
```
/dev/*sda#* /media/*mountpoint* vfat user,utf8,fmask=0111,dmask=0000 0 0
```

**For reiserfs:**
```
/dev/*sda#* /media/*mountpoint* reiserfs nodev,nosuid 0 0
```

---

### Post by Jeztastic on 2007-12-09
Thanks, URA*.

All sorted now. Tried to follow another tutorial earlier, but it got me confused.

Jez

---

### Post by sporkubus on 2007-12-13
> Add one of the following line (depending on filesystem type) to your fstab to cause it to automatically mount (replace sda# with the name of the device you wish to mount and mountpoint with the mountpoint you created in step 1):

How do I find the "name" of my drive?

---

### Post by sporkubus on 2007-12-13
I figured out the name from the partition editor and I tried this, but it didn't work, and now I can't access my drive at all within Linux. When I try to mount the drive manually, it gives me an error, "Cannot mount volume, you are not privileged to mount this volume." How can I fix this?

---

### Post by jken146 on 2007-12-13
Mount it as sudo.

---

### Post by sporkubus on 2007-12-13
Okay, but how can I get it to automatically mount? I think the problem is that for this

> /dev/sda# /media/mountpoint ext3 defaults,errors=remount-ro 0 1

for sda# I put hda3 because that's the partition name in gparted. In the file manager thing the name of the drive is "34.2 GB Volume" so is that what I put for sda# or is there some other name that I'm not seeing?

---

### Post by kefurd06 on 2007-12-13
> **sporkubus said:**
> Okay, but how can I get it to automatically mount? I think the problem is that for this



for sda# I put hda3 because that's the partition name in gparted. In the file manager thing the name of the drive is "34.2 GB Volume" so is that what I put for sda# or is there some other name that I'm not seeing?

if you're trying to mount a windows partition u need to change ext3 to either ntfs or whatever it is (listed in gparted)

also i see mountpiont in that code. mountpoint should be replaced with the folder that you created under media. if you haven't done this, 
```

sudo mkdir /media/win

```
and replace mountpoint with win .

---

### Post by sporkubus on 2007-12-13
Sorry, I quoted the wrong one. I did use the NTFS one and it didn't work. I think the problem is that I have the wrong name, but I don't know where to get the correct one. Does hda3 sound right?

---

### Post by sporkubus on 2007-12-13
Yes, I did this, I did sudo mkdir /media/Media and my final output looked like this 

/dev/hda3 /media/Media ntfs-3g defaults,nls=utf8,umask222 0 0

---

### Post by kefurd06 on 2007-12-13
if i had it my way i'd have you go ahead and sudo mkdir /media/win . having a folder under media named Media is just a bad idea. but try this:

```

/dev/hda3 /media/Media ntfs defaults 0 1

```

also, if that didn't do it, is the drive mounting okay manually? and is this vista or at least are u sure it's ntfs?

---

### Post by stchman on 2007-12-13
> **yuffie8 said:**
> hey, complete rookie here, is it possible to mount my windows partition ? When i click on the volume in 'computer' file browser i get:-
 'Cannot mount volume:
 You are not privileged to mount this volume.' 

I am the computer admin on windows so i dont know what this is all about ...

Any help would be greatly appreciated, i checked the other threads before i posted and none have what im looking for. Thanks

I have a tutorial on partition mounting:

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by sporkubus on 2007-12-13
I changed the name of mount point and it seems to be working now! Thanks very much for your help!

---

### Post by csaga on 2007-12-28
How can I create a user to no have privileges to automatically mount a Windows drive, evrey time after logon?
Thanks for help!

---

