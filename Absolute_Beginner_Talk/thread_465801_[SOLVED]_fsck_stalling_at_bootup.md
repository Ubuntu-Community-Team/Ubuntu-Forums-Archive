---
title: "[SOLVED] fsck stalling at bootup"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-06-06
Hi,

I'm having a few problems booting into Ubuntu FF.

The boot text gets to 'Checking File Systems'.

Then reads 'fsck 1.40-WIP'

Then stops.

A little bit of background as to what I was doing before this happened.

I was running the command 'sudo dd if=/dev/urandom of=/dev/sdb', where 'sdb' is an external HDD with 3 primary partitions; sdb1 sdb2 and sdb3.

After four days it was still running, so I assumed it had hung and rebooted Ubuntu, and then got the error described above.

I can still boot into XP, but it cannot see any linux partitions, nor can it see the external HDD

So, am I looking at a fresh Ubuntu install, and what on earth is going on with the external HDD.

Thanks in advance.

---

### Post by mozetti on 2007-06-06
I had the same thing happen to me when I had to hard-reset the system. Boot from the Ubuntu-FF Live-CD and run the fsck on the partitions from there. ```
e2fsck -f /dev/sdb1
```

The "-f" switch forces a check, even if e2fsck reports that the partition is clean. Check the other options for e2fsck also -- I usually use the "-y" switch to automatically answer "yes" to all the questions.```
man e2fsck
```

Dont' mount the partitions before running e2fsck -- it's best to run it on unmounted partitions. All that being said, it's possible that something is hosed. I haven't used the "dd" command, but since you were copying partitions there is always the chance things got hosed.

Good luck!

---

### Post by WorldTripping on 2007-06-06
Thanks for the quick reply.

I'm beginning to think that things are not well.

I booted from a live CD, ran fdisk -l, and got this for the laptop HDD

ubuntu@ubuntu:~$ sudo fdisk -l

   Disk /dev/sda: 20.0 GB, 20003880960 bytes
   255 heads, 63 sectors/track, 2432 cylinders

   Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
   /dev/sda1   *           1         535     4297356    7  HPFS/NTFS
   /dev/sda2            1953        2408     3662820   83  Linux
   /dev/sda3            2409        2432      192780    5  Extended
   /dev/sda4             536        1952    11382052+   c  W95 FAT32 (LBA)
   /dev/sda5            2409        2432      192748+  82  Linux swap / Solaris

   Partition tables are not in disk order

As far as I was aware the 'dd' command should fill all the sectors of a drive with random data.

And it was run on the external HDD (sdb).

Why would this affect the laptop HD (sda) ?

I'm at a loss here.

Why do 'sda3' and 'sda5' occupy the same blocks ?

Am I looking at a re-install here ?

I'm not too concerned about the external HDD at the moment, I'm concentrating on getting my Ubuntu installation to boot.

Cheers.

---

### Post by mozetti on 2007-06-06
> **WorldTripping said:**
> Why do 'sda3' and 'sda5' occupy the same blocks ?

I'm by no means an expert, but I don't think it's a problem. I'll assume you're not an expert either and I'll give pretty basic info.

You can only have 4 primary partitions on any hard drive. To get around that limitation, we use "Extended" partitions -- the extended partition basically acts like a primary partition, but you can have many more partitions within an "Extended" partition -- the partions within an "Extended" partion are called "Logical" partitions.

sda3 is an "Extended" partion. It appears that sda5 is just a "Logical" partition in the "Extended" partition, and looks like sda5 takes up all the space in the sda3 "Extended" partition (which is fine from a technical standpoint).

I'm not sure we're at the point of a re-install yet. Just run e2fsck on all your linux partitions, and the FAT32 equivalent (i think it's dosfsck?) on your FAT32 partition, and then see if you can boot and start up correctly.

---

### Post by WorldTripping on 2007-06-06
Ta for that.

I'm running it now, and I'll report back in an hour or so.

Cheers.

---

### Post by WorldTripping on 2007-06-06
Hmmm.

I didn't check sda1 or sda4, as they are the XP partition (C:) and my data partition (E:)  respectively.

I ran 'e2fsck -f /dev/sda2' and it completed fine.

The same command did not work on 'sda3' or 'sda5' with the reports that one was a zero length partition, and the other had errors in the superblock.

I rebooted into FF, and 'fsck' automatically ran a check on 'sda2'.

Then it said it failed to correct errors in the boot partition.

Then it restarted.

Now it's back to where it first was, stuck at ' *Checking file systems... '

Any clues anyone ?

Thanks in advance.

---

### Post by WorldTripping on 2007-06-06
{ BUMP }

[ Anyone any ideas ? ]

---

### Post by vanadium on 2007-06-06
On your external drive: as far as my experience goes, but I suspect that the dd command you used will have erased the three partitions on your hdb. You did just specify /dev/hdb as your output, rather than a file name on that device. You will need to repartion and reformat your external disk to use it again. Indeed, since you had to interrupt the proces, your external disk is not usefull even to reverse the dd proces (= copy the data back). Yet, that shouldn't be the reason why your system does not boot.  

Can you try booting with an older kernel? I suggest this because two days ago, I could not boot a desktop system anymore after a kernel update, and the system did hang on an fsck error very similar to what you describe.

---

### Post by WorldTripping on 2007-06-06
Hi, and thanks for the reply.

About the external drive; I'm not to concerned abou that being erased, as I was going to encrypt it using LUKS.

I'm more concerned about not being able to boot into Ubuntu.

How would I boot using an older kernal ?

I can boot from either a Dapper or a Feisty live CD.

But I can't boot from the Feisty installation on the laptop.

The more I get into this, the more a re-installation is looking likely.

Cheers.

---

### Post by vanadium on 2007-06-06
To boot a previous kernel, you need to display your grub menu. Yours probably is hidden (like mine). If you reboot your computer, you should see a brief message stating "Press esc to enter grub" or something similar. If you pres the key (I'm even not sure it is esc), then the boot menu will be presented, with the most recent (default) kernel on top. Scroll down to your previous kernel and press Enter to boot that kernel.

If that solves the issue, then it is indeed your kernel. I bet the only option is then not to use the newer kernel. To permanently boot with the older kernel (do this only if you indeed can boot with the previous kernel ): edit /boot/grub/menu.lst and comment out (= add # in front) the two blocks relating to your current kernel, for example:

```


#title		Ubuntu, kernel 2.6.20-16-generic
#root		(hd0,0)
...
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
....
#initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic

```

[/code]

---

### Post by mozetti on 2007-06-06
> **WorldTripping said:**
> I ran 'e2fsck -f /dev/sda2' and it completed fine.

The same command did not work on 'sda3' or 'sda5' with the reports that one was a zero length partition, and the other had errors in the superblock.

I rebooted into FF, and 'fsck' automatically ran a check on 'sda2'.

Then it said it failed to correct errors in the boot partition.

Then it restarted.

Now it's back to where it first was, stuck at ' *Checking file systems... '

Any clues anyone ?

Thanks in advance.

Ok, now we're getting somewhere. I believe it returned, "zero length partition" for sda3 because it's your Extended partition -- a placeholder. The message about errors in the superblock is the one that's important. The hard-reset seems to have screwed up the superblock with contains the info needed to recognize the partition. I've been through this before, too.

I can't recall off the top of my head, but there should be some info in "man e2fsck" about specifying the superblock to use -- something like 8193, 16"xxx", or 32"xxx". Check "man e2fsck" and use the switch to specify the superblock. I believe it's going to be 32"xxx", but try them all until you find the right one. I used "xxx" because I don't remember the actual numbers.

I don't think the kernel is the problem. On the bright side, I doubt the data on the partition is messed up. I think you just need to get the partition table fixed so the OS knows how to use it.

---

### Post by WorldTripping on 2007-06-06
Hi,

@ Vanadium - Sorry for being an idiot..I'm dual booting, so of course I can see the grub screen; and I don't have an option of going into an older kernal; nor does 'Recovery Mode' work. It stops at the same place.

@ Mozetti - I think you are right on the money. Unfortunately, I cannot run 'e2fsck' in any of it's guises. I get the message that it's mounted. I 'umount /dev/sda5' and get told that it isn't mounted. I can't specify a different superblock to use, (because it's mounted); and it can't use the backup superblocks, message 'Bad magic number in super-block while trying to open /dev/sda5'.

To be honest, I'm getting to the point where it would be a LOT simpler to reinstall Feisty.

I know it'll be a pain to put all my software back on, and I've done a bit of tweaking that'll need to be re-done, but I can't see a resolution to this.

Thanks in advance, and I am genuinely grateful to all the help people have helped.

---

### Post by mozetti on 2007-06-06
Alrighty. I'm surprised you're getting those "mounted" and "unmounted" errors when booting from the LiveCD. I didn't think the LiveCD mounted any partitions by default. Well, good luck with whataver solution you go with.

---

