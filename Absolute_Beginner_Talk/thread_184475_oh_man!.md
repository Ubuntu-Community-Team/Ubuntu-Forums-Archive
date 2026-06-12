---
title: "oh man!"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-30
As I have said before I am running out of space on /var.  Well I found a solution that freed up nearly 700mb and I am fine now.

Now I have another issue.  My / partition is too small.  I have two separate swap partitions.  I want to destroy one and give that space to /.  But whenever I use a LIVE CD it takes all my swap space on my harddrive without asking me.  And I don't know how to get it to leave it alone so I can repartition things.

Is there any cached files on / that I can delete?  How do I run a LIVE cd that won't touch HD swap?

Thanks

---

### Post by aysiu on 2006-05-30
Can you give more information on what your partitioning scheme is currently? Can you post the output of these commands? ```
sudo fdisk -l
df -h
```

---

### Post by morequarky on 2006-05-30
Sure, no problem.

> 
Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         765     6144831    7  HPFS/NTFS
/dev/hda2             766         826      489982+  83  Linux
/dev/hda4             827        9733    71545477+   5  Extended
/dev/hda5             889        1010      979933+  83  Linux
/dev/hda6            1011        1059      393561   83  Linux
/dev/hda7             827         888      497952   82  Linux swap / Solaris
/dev/hda8            1060        1424     2931831   83  Linux
/dev/hda9            1425        8475    56637126   83  Linux
/dev/hda10           8476        9606     9084726    b  W95 FAT32
/dev/hda11           9607        9733     1020096   83  Linux

Partition table entries are not in disk order


AND

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             449M  190M  235M  45% /
tmpfs                 237M     0  237M   0% /dev/shm
tmpfs                 237M   13M  225M   6% /lib/modules/2.6.12-10-386/volatile
/dev/hda9              54G  7.6G   43G  16% /home
/dev/hda1             5.9G  5.7G  174M  98% /media/hda1
/dev/hda6             361M  8.1M  334M   3% /srv
/dev/hda8             2.8G  2.1G  566M  79% /usr
/dev/hda5             897M  165M  685M  20% /var
/dev/hda10            8.7G  679M  8.0G   8% /media/fat32


I was running "simple backup config" and it was taking up a large part of my /var.  I shut it down and deleted the backup files.  I now save "tar" to /home so I have much more /var space then before.   I also created a /home/<username>/http-pubic directory and am now using /home to host my large images.  So I hope to keep /var small from now on.

I backed up my system with a "tar" command and it completed with no errors.  I hope it will work if I ever need it.  I then was going to try to upgrade to Dapper hoping my internet and LAMP wouldn't fail.  But after running "sudo dist-upgrade -d" or something like it, it said I was out of space and needed like 48MB to upgrade.  That is why I posted.  I have now reboot the computer hoping that might clear up something.   I had been running for a week+ probably without rebooting.

Looking at the image below I see that I am going to have a very hard time adding space to '/'. 

I also notice hdc.  I have no idea what hdc is.   I have a printer connected.  Maybe that's it.

---

### Post by morequarky on 2006-05-30
Partitions:

---

### Post by aysiu on 2006-05-30
[Apparently, there's some kind of *swapoff* command](http://www.linuxforums.org/forum/debian-linux-help/57844-how-can-i-unmount-swap-extended-ubuntu-5-10-live-cd.html), but I don't know how to use it.

You know, honestly, you're fighting a losing battle. You'll constantly have your partitions filling up and then trying to find ways to cut them back again.

If I were you--since you have a separate /home partition, I'd use a live CD to delete the /, /var, /usr, and /srv partitions, and then reinstall Ubuntu, mounting /home as it is. If you want, you can back up your /usr data as a .tar.gz on your FAT partition until after you reinstall.

This would be especially appropriate, since Dapper comes out on Thursday, and you appear to still be using Breezy. You could do a clean installation of Dapper after you combine those partitions.

I'm not sure what else to do, as /var and /usr are usually the ones that have too much stuff in them.

**Edit**: *man* pages make no sense to me, but maybe this will help you... ```
SWAPON(8)                                              Linux Programmer&#8217;s Manual                                              SWAPON(8)

NAME
       swapon, swapoff - enable/disable devices and files for paging and swapping

SYNOPSIS
       /sbin/swapon [-h -V]
       /sbin/swapon -a [-v] [-e]
       /sbin/swapon [-v] [-p priority]  specialfile ...
       /sbin/swapon [-s]
       /sbin/swapoff [-h -V]
       /sbin/swapoff -a
       /sbin/swapoff specialfile ...

DESCRIPTION
       Swapon is used to specify devices on which paging and swapping are to take place.

       The device or file used is given by the specialfile parameter. It may be of the form -L label or -U uuid to indicate a device by
       label or uuid.

       Calls to swapon normally occur in the system multi-user initialization file /etc/rc making all swap devices available,  so  that
       the paging and swapping activity is interleaved across several devices and files.

       Normally, the first form is used:

       -a     All  devices  marked  as  &#8216;&#8216;swap&#8217;&#8217;  swap  devices  in /etc/fstab are made available, except for those with the &#8216;&#8216;noauto&#8217;&#8217;
              option.  Devices that are already running as swap are silently skipped.

       -e     When -a is used with swapon, -e makes swapon silently skip devices that do not exist.

       -h     Provide help

       -L label
              Use the partition that has the specified label.  (For this, access to /proc/partitions is needed.)

       -p priority
              Specify priority for swapon.  This option is only available if swapon was compiled under and is used  under  a  1.3.2  or
              later kernel.  priority is a value between 0 and 32767. Higher numbers indicate higher priority. See swapon(2) for a full
              description of swap priorities. Add pri=value to the option field of /etc/fstab for use with swapon -a.

       -s     Display swap usage summary by device. Equivalent to "cat /proc/swaps".  Not available before Linux 2.1.25.

       -U uuid
              Use the partition that has the specified uuid.  (For this, access to /proc/partitions is needed.)

       -v     Be verbose.

       -V     Display version
       Swapoff disables swapping on the specified devices and files.  When the -a flag is given, swapping is disabled on all known swap
       devices and files (as found in /proc/swaps or /etc/fstab).

NOTE
       You should not use swapon on a file with holes.  Swap over NFS may not work.

SEE ALSO
       swapon(2), swapoff(2), fstab(5), init(8), mkswap(8), rc(8), mount(8)

FILES
       /dev/hd??  standard paging devices
       /dev/sd??  standard (SCSI) paging devices
       /etc/fstab ascii filesystem description table

HISTORY
       The swapon command appeared in 4.0BSD.

Linux 1.x                                                  25 September 1995                                                  SWAPON(8)
```

---

### Post by morequarky on 2006-05-30
thanks.

I don't understand man pages very well either.

I wish I could just delete the NTFS partition.  :)

Thanks.

---

### Post by aysiu on 2006-05-30
[QUOTE=morequarky]thanks.

I don't understand man pages very well either.

I wish I could just delete the NTFS partition.  :)

Thanks.[/QUOTE] Why can't you delete the NTFS partition? Need Windows?

---

### Post by morequarky on 2006-05-30
Me?  Heck no.  I don't need windows.  My wife wants it.  I think she should just use her laptop and let this whole computer be Ubuntu.

This computer is installed with XP64 Pro.  Which is sweet if ya are a windows lover, which I aint.

I have fallen in love with "choice".  I don't use windows at all.

---

### Post by dmizer on 2006-05-30
i assume you are using the ubuntu live cd?  i know that with knoppix when you see the boot prompt, you can type knoppix noswap.

with the ubuntu live cd, you should be able to hit f1 at the boot prompt and get a list of all the boot parameters available to you ... one of which is to turn off swap.

so it looks like in this case, when you see "boot:" for your live cd, type in:
```
linux swapoff
```
and then boot.

your hdd should be free for you to resize now.

---

### Post by Gustav on 2006-05-30
Or, when using the live-CD just type 'sudo swapoff' in a terminal :)

---

### Post by paradj on 2006-09-12
is there way to turn off the swap in ubuntu if its already installed..?

..i realize this would/should make ubuntu slower..
but would ubuntu still load (256MB real ram)?
or are the "journals" written there?

of course this maybe me just being dumber than usual:roll:

---

### Post by paradj on 2006-09-13
DOH! :oops: 
just re-read this thread
sometimes i am stupider than i think....

---

