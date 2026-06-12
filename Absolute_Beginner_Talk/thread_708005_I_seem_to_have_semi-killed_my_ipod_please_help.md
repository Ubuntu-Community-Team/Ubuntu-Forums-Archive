---
title: "I seem to have semi-killed my ipod please help"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by mb184 on 2008-02-25
I have an iPod 5g and i have been messing around with it and i discovered the problem of iTunesLock preventing me from accessing the iPod and putting itself back on. Well in a stroke of genius I deleted the Play Counts file also trying to see if that would stop iTunesLock from reappearing every time i plug in my iPod.
Now my computer (ubuntu 7.10) does not see it at all. Also windows does not see it, until i remove it then it says my iPod is corrupted, but when i connect it, iTunes denies any knowledge of seeing it.

i know there is a .Trash-matthew file on the iPod and i have a great suspicion that if i can get on the iPod and see the hidden files then i could just put the file back.

The dmesg | tail prints:
matthew@matthew-laptop:~$ dmesg | tail
[ 4127.628000] scsi 9:0:0:0: Direct-Access Apple iPod 1.62 PQ: 0 ANSI: 0
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.632000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.632000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.632000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.632000] sd 9:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[ 4127.636000] sd 9:0:0:0: [sdb] Write Protect is off
[ 4127.636000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4127.636000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 4127.636000] sdb:

Is there anyway i can force a restore on it in windows, or fix it in linux?

Thanks,
Matt

---

### Post by ispy on 2008-02-25
Bump/advice

you might be able to do a complete restore with the iPod software from (gag) windows... otherwise, try 

```
sudo nautilus
```

and look for it in there, in case you absolutely need root access in order to mess with you ipod...

---

### Post by mb184 on 2008-02-26
Tried to find it in windows - iTunes and Restore software doesn't see it :(.

Still cant see it even as root... and i ran dmesg |tail again and got a brand new response

```

matthew@matthew-laptop:~$ dmesg |tail
[ 9694.884000] Buffer I/O error on device sdb, logical block 0
[ 9775.112000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9775.112000] end_request: I/O error, dev sdb, sector 0
[ 9775.112000] Buffer I/O error on device sdb, logical block 0
[ 9853.396000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9853.396000] end_request: I/O error, dev sdb, sector 0
[ 9853.396000] Buffer I/O error on device sdb, logical block 0
[ 9933.328000] sd 19:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 9933.328000] end_request: I/O error, dev sdb, sector 0
[ 9933.328000] Buffer I/O error on device sdb, logical block 0

```

---

### Post by ispy on 2008-02-26
is it mounted?

```
sudo mount /media/sdb
```

assuming your ipod is the only other storage drive on your computer... (so if you have two hdds, /media/sdc... etc)

---

### Post by mb184 on 2008-02-26
its not mounted.  The problem now is that /media/sdb isn't in fstab or mtab.  here is the output```
matthew@matthew-laptop:~$ sudo mount /media/sdb
[sudo] password for matthew:
mount: can't find /media/sdb in /etc/fstab or /etc/mtab

```

---

### Post by mb184 on 2008-02-26
i tried to add it to fstab
```
/dev/sdb /media/iPod vfat defaults,sync,user 0 0
```

then i did
```
matthew@matthew-laptop:~$ sudo mkdir /dev/sdb
matthew@matthew-laptop:~$ sudo mount /dev/sdb /media/iPod 
```

and got
```
mount: /dev/sdb is not a block device
```

i have also tried to identify the label with
```
ls /dev/disk/by-id -lah
```
but nothing sdb was listed only sda

i think that i may have labeled it wrong is fstab if it helps the name that it used to be mounted under was ANTHONY RAM
please help me if you have any insight at all

---

### Post by Whiffle on 2008-02-26
Ouch, looks like linux/windows isn't even recognizing it as a block device, ie, something it can mount.

Try
```

sudo fdisk /dev/sdb

```

If it runs without complaint, hit p.  It should show you a list of the partitions on the ipod.  If they're there, find the one that is fat32 or vfat, for example, sdb2.  If it shows, we could possibly just reformat it and see what happens.  It will lose all the data on that partition though;

for example:
```

mkfs.vfat /dev/sdb2

```

If that is successful, try unplugging it and plugging it back in again.  With any luck you'll be able to mount it and then re set it up.

---

### Post by mb184 on 2008-02-26
tried ```
sudo fdisk /dev/sdb
```

and it outputed 
```
matthew@matthew-laptop:~$ sudo fdisk /dev/sdb
last_lba(): I don't know how to handle files with mode 40755
You will not be able to write the partition table.

Unable to read /dev/sdb
```

I treid to run
 ```
mkfs.vfat /dev/sdb2
```

But it came back with:
```
matthew@matthew-laptop:~$ mkfs.vfat /dev/sdb2
mkfs.vfat 2.11 (12 Mar 2005)
/dev/sdb2: No such file or directory
```

FYI i can see the darn thing in BIOS but still nothing in Ubuntu or Windows XP :evil: ](*,)

On a side note i got into the diagnostic menu by holding back and the action button and all the tests seemed to check out just fine, so no problems with the hardware it appears

---

### Post by Whiffle on 2008-02-26
Hmm, maybe try disk mode?

> 
Cure 5: If the iPod still won't mount, reset it (see Cure 3) and then hold down Previous and Next on the first three generations of iPod (Play and the Select button on the mini and fourth-generation iPod) to place the iPod in Disk Mode -- a mode similar to the Mac's FireWire Target Disk mode that forces the iPod to mount. An iPod that mounts only when thrown into Disk Mode should be restored (see Restoring the iPod ).

[http://www.macworld.com/article/38851/2004/09/trubipod.html](http://www.macworld.com/article/38851/2004/09/trubipod.html)

---

### Post by mb184 on 2008-02-26
Still cant see it when it is put in disk mode while in linux...  ran several command i ran before "dmesg, fdsk, ect..."   im gonna try to run it later on my friends computer and see if i can get anywhere in windows, but I am doubtful but you never know.

---

