---
title: "MDADM RAID disappears on startup"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-02-06
Hey all,

Finally got my Software RAID5 up and running using a MDADM create command, copied files to it and have shared them to my network and the network is happily running files from it!

However when I restart the computer i lose the md0 device! Then I have to go to terminal and MDADM create again and mount -a it etc - I don't lose any data thankfully. I don't have anything in my /etc/mdadm.conf file. I am assuming this is what i need to change? Put the devices in and setup the raid? So that when the system loads it opens the RAID?

Also, Since the last reboot (power blackout) none of the windows network can access the server with its name (//ubuntuserver), so I have had to set them all up to access it via IP address, which makes it difficult to setup username auto login profiles. Is there anything that could cause this other than not restarting?

Thanks guys for any help!

---

### Post by rojasd on 2007-02-11
Sounds like all you need to do is set up a mount point for it in your /etc/fstab file, something like:

/dev/md0      /mnt/raid      reiserfs    defaults        1   1

Of course, that's just an example.  I don't know what your filesystem is, but from your description, it sounds like the raid setup was fine - it just isn't mounting automatically.

---

### Post by mattdwilnew on 2007-02-12
I have the following line in my /etc/fstab:

/dev/md0  /data ext3 defaults 0 0

But it won't mount because when i restart the md0 device is not created, I have got the mdo in the MDADM.conf file and it doesn't do anything. I have also got the RAID tools thing in the linux services menu on startup as well!

Anyone who can help me?

---

### Post by rojasd on 2007-02-13
Your fstab looks fine.  When you created the raid partitions did you set the type to fd (Linux RAID partition with persistent superblock)?

---

### Post by mattdwilnew on 2007-02-13
> **rojasd said:**
> Your fstab looks fine.  When you created the raid partitions did you set the type to fd (Linux RAID partition with persistent superblock)?


ermm, I am pretty sure i did, i tried so many different guides that it has become a bit jumbled. Opening Gparted the file system for each drive is unknown. I know i used a command to format it rather than gparted. 

Does this mean i have to reformat the whole lot? :(

---

### Post by Medieval_Creations on 2007-02-16
I'm having this exact same problem.  I can setup the raid and mount it no problems, but as soon as I reboot /dev/md0 is gone.

Here's how I setup the raid.
```

# sudo mknod /dev/md0 b 9 0
# sudo mdadm --create --verbose /dev/md0 --level=raid0 --raiddevices=2 /dev/sda1 /dev/sdb1
# sudo mkfs.ext3 /dev/md0
# sudo mount /dev/md0 /mnt/Mp3s
```

fstab has this line
```
/dev/md0  /mnt/Mp3s  ext3  defaults 0 0
```

Any thoughts as to why /dev/md0 dissapears or does not restart with the PC?

---

### Post by mattdwilnew on 2007-02-19
Noone can help us out? *cry*

> **Medieval_Creations said:**
> I'm having this exact same problem.  I can setup the raid and mount it no problems, but as soon as I reboot /dev/md0 is gone.

Here's how I setup the raid.
```

# sudo mknod /dev/md0 b 9 0
# sudo mdadm --create --verbose /dev/md0 --level=raid0 --raiddevices=2 /dev/sda1 /dev/sdb1
# sudo mkfs.ext3 /dev/md0
# sudo mount /dev/md0 /mnt/Mp3s
```

fstab has this line
```
/dev/md0  /mnt/Mp3s  ext3  defaults 0 0
```

Any thoughts as to why /dev/md0 dissapears or does not restart with the PC?

---

### Post by Medieval_Creations on 2007-02-19
I was able to get my working *(eventually)*.

I was having this problem with Feisty. They changed the install, there are 2 questions that it asks now when mdadm is installed.  1st, which raids need to be started at boot to mount as /.  2nd, Is if you want to have the raids started at boot.

Once I read the menus completely, not just going with the defaults it started fine.

Under Edgy, I haven't had any problems with it starting automatically.


Which version of Ubuntu are you running and is mdadm checked under services?

---

### Post by mattdwilnew on 2007-02-20
Im using 6.10

And it is already installed!
Found a few guides on how to install it etc, and it worked until i reset! I thought it may be because I installed DMraid and it was clashing, so I uninstalled that - which resulted in it wiping one of the superblocks of the drives. Which caused me 3-4 hours of headaches before I accessed it and got the data onto a normal IDE hard drive. While looking for solutions I found a few threads with our problem, just not with the same wording as mine. I am going to reinstall/reformat the drives again and see how that goes :)

---

### Post by rojasd on 2007-02-20
> **mattdwilnew said:**
> ermm, I am pretty sure i did, i tried so many different guides that it has become a bit jumbled. Opening Gparted the file system for each drive is unknown. I know i used a command to format it rather than gparted. 

Does this mean i have to reformat the whole lot? :(

What is the output of:

sudo fdisk -l /dev/sda

You need to replace the sda (or sdb, sdb, etc.) with hda (hdb, hdc etc.) if you have pata drives on your raid, but you should get something like the following:

Disk /dev/hde: 4311 MB, 4311982080 bytes
16 heads, 63 sectors/track, 8355 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
 
   Device Boot    Start       End    Blocks   Id  System
/dev/hde1             1      4088   2060320+  fd  Linux raid autodetect
/dev/hde2          4089      5713    819000   83  Linux
/dev/hde3          5714      6607    450576   83  Linux
/dev/hde4          6608      8355    880992    5  Extended
/dev/hde5          6608      7500    450040+  83  Linux

Notice for the first partition, /dev/hde1, the Id is listed as fd.  That's what you want for the partitions (do this for all partitions you put together to make md0) on your system that comprise the raid.  As to whether you'd have to redo this if it didn't show what you wanted, then I'd say "yes", but a more seasoned raid vet might have more to say about that.

Don

---

### Post by diesel1 on 2007-05-20
Hi all,

I am sorry to hijack a thread but I think my RAID1 woes sound similar to those in this thread.

I installed kubuntu and created a new raid1 setup.

/dev/hda2
/dev/sdb1

Both are flagged as fd(autoraid)

Created the array, formatted as reiserfs, transferred data to /media/Data mounted to /dev/md0 as reiserfs.

All seemed fine until I booted next session and ran cat /proc/mdstat and was given this..

diesel1:~$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 hda2[0]
      80035712 blocks [2/1] [U_]

unused devices: <none>


My raid setup is missing a  partition, /dev/sdb1.

I have this same problem with X/K/Ubuntu and a mix of sata and ide drives of varying brands.



Any help would be appreciated.

Diesel1.

---

### Post by mgrusin on 2007-05-26
I have the same problem; when I reboot my RAID5 array is almost always missing a disk, which has to be added back in manually.

One thing which is unclear to me:

A previous poster said that raided drives need to have a partition which is type FD.

I carefully did that to all my drives when creating the array.

Now when I check my drives, they all say e.g. "disk /dev/sdd doesn't have a valid partition table". (?)

I wanted to see whether this was a problem, so the last time I rebooted (and the RAID kicked out SDD), I went into fdisk and gave it a single partition with type FD.  This was verified when I went back to the command line and queried the disk.

But then when I added the disk back to the RAID array and it started rebuilding, when I check the disk again it says "disk /dev/sdd doesn't have a valid partition table".

?

Should building an array erase partition tables and types on the drives used?  (I'm using four entire drives for this array).

Thanks for advice, -MG.

---

### Post by psusi on 2007-05-26
You should be adding a partition on sdd to the array, not the entire disk.  If you add the entire disk, then you overwrite the partition table with whatever data gets written there in the raid.

---

### Post by mgrusin on 2007-05-26
Hmmm.  I see what you're saying.  Unfortunately I now seem to have a working (except on reboot) RAID5 array built out of disks not partitions.

To fix this I got the bright idea of failing the disks one at a time and adding them back as partitions.  I tried failing and removing /dev/sdd, creating an FD partition on it, and adding it back in as /dev/sdd1.  But I get: 

> [FONT="Fixedsys"]mgrusin@Aurora:~$ sudo fdisk -l /dev/sdd

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect

mgrusin@Aurora:~$ sudo mdadm /dev/md0 --add /dev/sdd1

mdadm: add new device failed for /dev/sdd1 as 4: Invalid argument[/FONT]

If I add it as /dev/sdd it goes right in.  Is this because the partition is slightly smaller than the disk so it doesn't match the other RAID sections?

Thoughts? Thanks for the help! -MG.

---

### Post by psusi on 2007-05-26
Possibly yes... I'd say you need to recreate the raid from scratch.

---

### Post by diesel1 on 2007-05-27
Hi all, I tried again to set up my raid1 and it seems to have worked.

I removed mdadm, deleted the partitions and swapped some partitions around, rebooted then installed mdadm and created the array again.

Everything is fine after a data restoration and a test reboot.

I think mdadm was trying to reinitialize the old raid partitions even though they had been reformatted.

Diesel1.

---

### Post by mgrusin on 2007-06-02
@psusi:

Re a few messages up, where I had created my RAID on whole disks rather than partitions (an easy mistake to make IMO), I recreated it using partitions and things seem to be working much better now on startup.  Thanks very much for the advice!

Another thing I am doing is manually unmounting and stopping the RAID before shutdown in case there are deficiencies in the shutdown scripts.  Don't know if this is helping but it seems to be working well so far.

I'd recommend anyone having problems losing RAID members on startup is double-checking whether they made their RAID on disks rather than partitions.  Making it on disks seemed to work fine as far as the RAID was concerned, but I don't think the startup/shutdown scripts liked it.  (if "cat /proc/mdstat" shows something like "sda1[0] sdb1[1]" etc. you're fine, if it shows "sda[0] sdb[1]" you might think about rebuilding it).  If that's not the problem, try unmounting / stopping before shutting down and see if that helps.

Hope this helps someone, thanks again. -Mike G.

---

