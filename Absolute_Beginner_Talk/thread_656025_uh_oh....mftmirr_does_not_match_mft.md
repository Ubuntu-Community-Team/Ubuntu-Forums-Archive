---
title: "uh oh....mftmirr does not match mft"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by missed her show on 2008-01-02
so after rebooting, i get the following error regarding my external HDD::
> 

$mftmirr does not match $mft (record0) . Failed to Mount '/dev/sdb':  Input/Output error NTFS is either inconsistant, or your have hardware faults, or you have a SoftRaid/FakeRaio hardware.


ugh.   I can't unmount it....i'm still totally nooob.    thanks for the help.

---

### Post by ~LoKe on 2008-01-02
Type this into the terminal:
```
sudo fdisk -l
```
What's the output?

---

### Post by missed her show on 2008-01-02
```
Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd835d835

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            1276        2480     9679162+   5  Extended
/dev/sda5            1276        2361     8723263+  83  Linux
/dev/sda6            2362        2480      955836   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8be2f02b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


```


thanks.

---

### Post by ~LoKe on 2008-01-02
And the output of this?
```
cat /etc/fstab
```

---

### Post by missed her show on 2008-01-02
here you go

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=586ff6b3-b74d-4f2f-a926-617beb0d20be /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9E283F7E283F548D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=420e1625-0f3f-4966-b3c2-ec23047fab8a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


---

### Post by ~LoKe on 2008-01-02
This is just a shot in the dark, but your fstab should probably look like this...

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=586ff6b3-b74d-4f2f-a926-617beb0d20be / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb1 /media/sdb1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=420e1625-0f3f-4966-b3c2-ec23047fab8a none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0 

Replace your old one with this one by typing this into the terminal:
```
gksu gedit /etc/fstab
```
Then pasting my block over yours.  Save and exit gedit, then type this into the terminal:
```
sudo mount -a
```

---

### Post by missed her show on 2008-01-02
tried it.   nothing seems to have changed.

---

### Post by missed her show on 2008-01-02
thanx for the assistance.   i'm going to get some shuteye.

---

### Post by ~LoKe on 2008-01-02
If the error still occurs when rebooting, then it's likely the drive is corrupted.  I would suggest waiting for someone better...accustomed...to these issues to come by and help you correct it.  Sorry for making you jump through hoops. ;)

---

### Post by teshne on 2008-01-02
Have you tried using the external drive on a windows box? It sounds like some of your structures are a damaged, it could well be hardware damage as it says... be careful with chkdsk, if it tries to run I wouldn't let it.

Cheers.

---

### Post by missed her show on 2008-01-02
Yeah.   

This happened after i went about monkeying with (deleting/formatting)  the windows partition on the primary hd (Not the ext hd that i'm having problems with.)


Shoot.   any help would be greatly appreciated.

---

### Post by teshne on 2008-01-02
Ok, what I mean is what happens if you plug the usb drive to a windows box? 
I don't know much about linux so I cannot help you in that respect.
The mftmirror get constantly updated by the mft in windows.. were you writing to the external drive in linux or just reading from it?
 I don't know how good is linux at writing NTFS at the moment. 
Maybe you can explain what you did to the primary NTFS partition.

Cheers.

---

### Post by missed her show on 2008-01-02
i plugged the external hdd into a separate windows XP box and it works fine.   


Before i had the problems with the linux box, i had deleted/formatted the windows partition on it, since i was using it and wanted to ultimately regain that windows partition for Linux use.

---

### Post by teshne on 2008-01-03
OK, I would write a bunch of files to the drive in windows so the mftmirror gets updated, maybe defrag the drive in windows, that would certainly create some changes in yours file records and if the error is only what it says, a mft mismatch then it should be fixed after that.
Cheers.

---

### Post by missed her show on 2008-01-03
problem solved, thanks for the help.

---

### Post by SneakyWho_am_i on 2008-03-27
My partition hdc1 had the same problem in Knoppix (would have persisted in Ubuntu of course)

Sadly, booting Windows was not an option because I am stubborn.
Fortunately, I was able to do this instead:

```
sudo -i
ntfsfix /dev/hdc1
ntfs-3g /dev/hdc1 /mnt/ntfs -o force
```

Before you do this, make sure the device is not mounted (then again could it be mounted?? lol)

The first line is like a "su" or sudoing the next two things.
The third line failed, despite which I was able to mount on subsequent attempts (although I used the GUI so I can't say what command exactly - it isn't relevant.)

I hope this helps someone in the future.
Use it at your own risk, your mileage may vary etc.
Still, if you're fearless and you can't afford to boot Windows, this MIGHT be appropriate. rtfm etc.

---

### Post by hell_yes on 2008-05-08
> **SneakyWho_am_i said:**
> My partition hdc1 had the same problem in Knoppix (would have persisted in Ubuntu of course)

Sadly, booting Windows was not an option because I am stubborn.
Fortunately, I was able to do this instead:

```
sudo -i
ntfsfix /dev/hdc1
ntfs-3g /dev/hdc1 /mnt/ntfs -o force
```

Before you do this, make sure the device is not mounted (then again could it be mounted?? lol)

The first line is like a "su" or sudoing the next two things.
The third line failed, despite which I was able to mount on subsequent attempts (although I used the GUI so I can't say what command exactly - it isn't relevant.)

I hope this helps someone in the future.
Use it at your own risk, your mileage may vary etc.
Still, if you're fearless and you can't afford to boot Windows, this MIGHT be appropriate. rtfm etc.

Thanks for posting this.  It was really helpful and saved my data!  I appreciate you posting it even though the OP had solved their problem.

---

### Post by ununoctium on 2008-05-20
woah, thanks :D ntfsfix really saved my predicament, i was in the same situation as you and funnily enough, this has only happened to me with Hardy Heron. Dapper, Edgy, Feisty and Gutsy have never given me this error

---

### Post by theLegend on 2008-07-05
> **SneakyWho_am_i said:**
> My partition hdc1 had the same problem in Knoppix (would have persisted in Ubuntu of course)

Sadly, booting Windows was not an option because I am stubborn.
Fortunately, I was able to do this instead:

```
sudo -i
ntfsfix /dev/hdc1
ntfs-3g /dev/hdc1 /mnt/ntfs -o force
```

Before you do this, make sure the device is not mounted (then again could it be mounted?? lol)

The first line is like a "su" or sudoing the next two things.
The third line failed, despite which I was able to mount on subsequent attempts (although I used the GUI so I can't say what command exactly - it isn't relevant.)

I hope this helps someone in the future.
Use it at your own risk, your mileage may vary etc.
Still, if you're fearless and you can't afford to boot Windows, this MIGHT be appropriate. rtfm etc.

Thank you SO much for posting this! You have saved all my hair from being pulled out! I tried lots of websites for this solution and it seemed so simple! I was so close to reformatting my spare hard drive but I resisted as there was an important spreadsheet I needed saving! 
I will nominate you in the new years honours list for this!

theLegend :)

---

### Post by koushik.ms on 2008-07-06
> **SneakyWho_am_i said:**
> My partition hdc1 had the same problem in Knoppix (would have persisted in Ubuntu of course)

Sadly, booting Windows was not an option because I am stubborn.
Fortunately, I was able to do this instead:

```
sudo -i
ntfsfix /dev/hdc1
ntfs-3g /dev/hdc1 /mnt/ntfs -o force
```

Before you do this, make sure the device is not mounted (then again could it be mounted?? lol)

The first line is like a "su" or sudoing the next two things.
The third line failed, despite which I was able to mount on subsequent attempts (although I used the GUI so I can't say what command exactly - it isn't relevant.)

I hope this helps someone in the future.
Use it at your own risk, your mileage may vary etc.
Still, if you're fearless and you can't afford to boot Windows, this MIGHT be appropriate. rtfm etc.

Great! Thank you so very much for posting. 

I had the "$MFTMirr does not match $MFT" issue on my external harddrive and I tried ntfsfix and it worked like a charm. Got right to the point and fixed it. Now I am able to access all my pictures once again. Thank you.

You Rock! :guitar:

---

