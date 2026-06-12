---
title: "boot issue - File System Check Failed"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by ykaeric on 2007-06-05
When I boot into Xubuntu - after a clean install and after my first Auto-Update, I receive this set of message when I'm booting up.  I receive the Xubuntu graphic boot up screen, then go back into command line mode and get this (I can't scroll up so this is all I can see):

is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck &#8211;b 8193 <device>

/dev/hda6: clean, 115282/973440 files, 610695/1945865 blocks
/dev/hda7: clean, 94383/973340 files, 565285/1945865 blocks

* File system check failed  							[fail]
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
Control-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program &#8216;apt-get&#8217; is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program &#8216;apt-get&#8217; is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@eric-desktop:~# 

I hit enter once, then hit Control-D and log in as usual and the system operates as usual.

My PC setup.  Pentium 4 2.8Ghz, 4 GB Ram, 75 GB hard drive (first) and 500GB hard drive (second).

I have 3 primary partitions on hard drive /dev/sda
/dev/sda3:  boot partition
/dev/sda1:  windows XP partition (NTFS) and an extended partition.  Within the extended partition are 5 logical partitions.  
/dev/sda5 - Logical Partition 1: 2 GB SWAP
/dev/sda6 - Logical Partition 2:  Ubuntu
/dev/sda7 - Logical Partition 3: Mepis
/dev/sda8 - Logical Partition 4: Xubuntu
/dev/sda9 - Logical Partition 5: empty (but has been formatted using Partition Magic using eft3 file system

I can boot into all OSs - have not run update managers yet on Ubuntu or Mepis.

The output from /var/log/fsck/checkfs is in the next post down.

Thanks for the help.

Eric

---

### Post by ykaeric on 2007-06-05
This is the output from /var/log/fsck/checkfs    checkfslog file:

Log of fsck -C -R -A -a 
Tue Jun  5 06:11:06 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sda9

/dev/sda9: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/hda6: clean, 115282/973440 files, 610695/1945865 blocks
/dev/hda7: clean, 94383/973440 files, 565285/1945865 blocks
fsck died with exit status 8

Tue Jun  5 06:11:06 2007
----------------

---

### Post by ykaeric on 2007-06-05
I seem to have a similar problem when i load Ubuntu - after doing a clean install and then a full auto-update.  Ubuntu is the first Linux OS in my extended partition.  It sees all the partitions after it as being bad.  Here's the checkfs log file:

As you can see it has the same issues as above - only this time it starts at /dev/sda7 - which is the first partition after Ubuntu.  On my Xubuntu startup, it finds the error after the Xubuntu partition (which is /dev/sda8) so it only sees a problem with /dev/sda9.  I can still boot into Ubuntu after it gives me those errors - I just enter control-D. 

Log of fsck -C -R -A -a 
Tue Jun  5 06:59:46 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sda7

/dev/sda7: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sda8

/dev/sda8: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sda9

/dev/sda9: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Tue Jun  5 06:59:46 2007
----------------

I am going to check and see if this happens when I boot into MEPIS.

---

### Post by ykaeric on 2007-06-05
I do not encounter this problem after updating MEPIS 6.5.02.  I believe this is because MEPIS is not performing a Kernel update whereas both Ubuntu and Xubuntu performed Kernel updates and allowed me to boot into the original Kernel for 7.04 or into the updated Kernel.

Apologies for posting this info in four posts - I've been logging in and out of the different OSs to see what would happen and have been posting from each.

Thanks for all help and advice - I'm really enjoying learning about these different Linux OSs.  Right now I'm loving Ubuntu and Xubuntu.  Just trying to evaluate which version I want to migrate the family too.

---

### Post by steve.horsley on 2007-06-05
Feisty recently changed from calling IDE devices /dev/sda? to calling them /dev/hda?. This fundamental change was in an update! 

Have a look in /dev and find out whether your disks are called sda or hda this week, and then check both /etc/fstab and /boot/gub/menu.lst to make sure they all use the same name. At least, that was the cause (and fix) of my getting this problem last week.

---

### Post by ykaeric on 2007-06-05
the file system shows them mounted as /dev/sda#
fstab shows them as /dev/sda#
menu.lst shows them as /dev/sda#

I don't see any discrepancies between the three.

---

### Post by markoloka on 2007-06-12
Same thing happened to me today and now my kubuntu: "read-only file system". 
It won't boot or so...  my hdds are sata2 and only hda is my dvdr. 
Anybody, any ideas??? I'm stuck now on xp as feisty won't work. 
Here's my topic about my problem  before i rebooted and voila...read-only.
 [http://ubuntuforums.org/showthread.php?t=471853](http://ubuntuforums.org/showthread.php?t=471853)

---

### Post by moshuptrail on 2007-06-13
Although the topic here seems to be morphing, let me return to the original post topic:
"fsck unable to read superblock"  followed by a message indicating your superblock might be corrupt.

If this is happening right after taking a recent upgrade - Linux 2.6.20-16
then do not worry - it's probably NOT the superblock,

Try selecting an older Linux kernel from your grub menu.  This worked for me,

What I don't know, is how to recover:  That is, how can I take the next update?
And, is there anything you can do before the next update?

---

### Post by waltea on 2007-06-15
I have exactly the same issue as Eric in the original post with Kubuntu at start-up. I am running Feisty which I installed off a DVD and have not upgraded., Once I quit the command prompt it resumes booting but the errors worry me. 

Any and all advice much appreciated.

Andrew

---

### Post by klisics on 2007-06-17
same here.
once I type exit the boot continues normal.

---

### Post by TNBY963 on 2007-06-20
I'm also having the same problem.
I installed ubuntu 32 bit, did all the updates and then I thought I'd try out 64 bit (I have an AMD64). It installed great, and when I started it everything went fine.
The problems began when I booted into the 32-bit ubuntu. I had the exact same output as the first poster. 
I exited and could log in again. 
In this thread: [http://ubuntuforums.org/showthread.php?t=474250&highlight=the+program+%27apt-get%27+is+currently](http://ubuntuforums.org/showthread.php?t=474250&highlight=the+program+%27apt-get%27+is+currently) they adviced to run "blkid" and compare the output in the menu.lst. There was nothing different.

I noticed something else. I have three drives: one 80GB meant for OSes, 2*500 GB for data (i plan to use this for audio). Now, the 2 500GB drives still are in my fstab but they didn't show up in nautilus. Nor did the other partitions on my 80GB drive. This didn't happen in ubuntu 64-bit, and they used to show up fine when ubuntu 32-bit was the only os installed.

My drives are all marked as sda, sdb or sdc (not hda,...)

Hope someone can help

Greetz

Gert

---

### Post by TNBY963 on 2007-06-20
Ok, I solved my own problem. Hope it helps someone.

So I decided to open fstab again on my 32-bit ubuntu (the one I installed first). Then I did the command "blkid" and compared every drive very tediously (and not only the drive on wich the system was installed). Turns out that the drive where I installed 64bit ubuntu (the second install) had changed it's UUID. So I did sudo gedit /etc/fstab copied and pasted the right line from the terminal (blkid) saved the new fstab, rebooted and voila. No problems whatsoever. Even all my partitions and other drives are back online now.

Wow, I'm so proud of myself now. I was this close to doing a reïnstall, but thanks to this forum and it's wonderfull community I didn't have to.

Thanks!

Gert

---

### Post by dnjuls on 2008-07-11
same here when upgrading from Edgy to Hardy (amazing that everything else worked).

As noted above, all I had to do was edit /etc/fstab and change to mounts from /dev/hdaX to /dev/sdaX.

---

