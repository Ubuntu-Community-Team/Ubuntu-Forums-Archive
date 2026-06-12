---
title: "Root drive: No more free space!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by hoboken on 2007-06-20
Hey guys. A message just popped up while I was doing some routine updates, saying that I had run out of space on my root drive. Here is how I'm partitioned:

Windows partition
Linux home
linux root
swap

So, the root is full...

..What do I do?!?

---

### Post by Skrynesaver on 2007-06-20
How much space have you given each partition?

How much space is available on the drive ?

You may need to copy your existing data somewhere safe and use gpartd from the live CD to either

1) shrink your home partition
2) add another partition to shift the load, I would recommend /usr

---

### Post by hoboken on 2007-06-20
5 gigs free in linux home, 7 gigs free in windows (I could take space from windows, which I use less and less)

Can't remember how much space I assigned to each, how can I check?

Thanks.

---

### Post by drivel on 2007-06-20
create a new partition and copy somen files to it.Mount the partition,it will be OK

---

### Post by drivel on 2007-06-20
> **hoboken said:**
> 5 gigs free in linux home, 7 gigs free in windows (I could take space from windows, which I use less and less)

Can't remember how much space I assigned to each, how can I check?

Thanks.

use command 'df'

---

### Post by hoboken on 2007-06-20
lluis@superubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              4806936   4607148         0 100% /
varrun                  376588       104    376484   1% /var/run
varlock                 376588         0    376588   0% /var/lock
procbususb              376588       100    376488   1% /proc/bus/usb
udev                    376588       100    376488   1% /dev
devshm                  376588         0    376588   0% /dev/shm
lrm                     376588     33900    342688  10% /lib/modules/2.6.20-15-realtime/volatile
/dev/sda3             11820088   6024732   5194928  54% /home
/dev/sda1             20908564  13532936   7375628  65% /windows
tmpfs                   376588     33968    342620  10% /lib/modules/2.6.20-16-realtime/volatile


Anyone interpret that for me?

Oh, and I was testing out some kernels and want to keep the realtime one... how can I remove the other kernels, from my computer and from grub? 

Would a viable solution be to use gparted to resize my windows partition and increase the size of my root partition?

---

### Post by Skrynesaver on 2007-06-20
You have:
 54% of your /home drive used
65% of your /windows drive used
100% of / used (but you knew that ;) )
incidentally df -h gives "human readable" output

Yup, shrinking the windows partition should give you enough space and the two partitions are contiguous /sda1 & sad2

Simply edit your /boot/grub/menu.lst and remove the kernels that didn't work out

---

### Post by hoboken on 2007-06-20
OK, news: I had to restart X after those updates I was doing, and when I tried to log in again, it said that /tmp couldn't be written to, or something like that. I assume this is a temp folder in the root directory, and the reason it can't write is because it has no space to do so. OK, time to boot into windows...

I have acronis disk director. I can resize the windows partition no problem. But then I go to increase the size of the root drive, and get this slightly worrying message:


[IMG]http://i53.photobucket.com/albums/g71/lluis01/error.jpg[/IMG]

Rather cute how it recognises it as a linux partition. But... Boot diskette? Is that my installation CD-R? I'm using grub, not lilo, what will I have to type? Will my linux be unbootable...FOREVER?  *ominous music plays*

---

### Post by hoboken on 2007-06-20
bump?

---

### Post by dannyboy79 on 2007-06-20
boot the live cd, chroot (please google or use ubuntu forum search if you don't know how to do this)  into your ubuntu installation, then do
sudo aptitude autoclean
sudo aptitude clean

this will remove unnessessary packages from your apt cache. according to the man pagaes for aptitude clean and autoclean:
clean
          Removes all previously downloaded .deb files from the package cache directory (usually /var/cache/apt/archives).

       autoclean
          Removes any cached packages which can no longer be downloaded. This allows you to prevent a cache from growing out
          of control over time without completely emptying it.

---

### Post by spivee69 on 2007-06-20
I agree, you'll have to clean out some space to allow you to boot the system or use an external boot image (CD, DVD or floppy).

Once you get online, you can use df -k to check the amount of space used on each of your mount points.  You can also use commands like

du -ks * - This will show you the amount of disk space used by each folder or file in your current path.  Helpful for finding out what is using up all your disk space.

du -ks <path> - this will tell you how much space (in kilobytes) is being used up by this specific path.

You can also try to find large files by using find commands like

find / -size +10240000c -ls 2> /dev/null

This will find files over 10mb in size

or if you want to get a little tricky...

find / -size +10240000c -ls 2> /dev/null | awk '{print $7,$11}' | sort -n

Though this may not report completely accurately if you have filenames with spaces in them..

---

### Post by dannyboy79 on 2007-06-20
won't this output those file to /dev/null, which I thought was the same as deleting them??

by the way, du is awesome!!! I am very new to linux (1.6 yrs) and I always used df -h to find out storage availability and as you probably already know, df -h is not very specific, like du is. Thanks for the great command. Would you happen to know a place where more commnds like this are all in 1 place? The basic's are all over the internet like, cd, cat, mv, cp, rm, and others but I think im ready to learn more. Thanks

PS (i'm not trying to hi-jack, just asking 1 question)

---

### Post by LunatikOwl on 2007-06-20
> **Skrynesaver said:**
> 
You may need to copy your existing data somewhere safe and use gpartd from the live CD to 

I've got bitten by gparted way too many times. next partitioning i'll use cfdisk on some other live cd like grml. 
last time i've used gparted, it crashed in the middle of the partitioning and left my /root partition currupted, although still usable(i've resized it from 12GB to 14GB and i still got 12GB although the partition  takes all the unpartitioned space i've assigned to it...).
btw, any ideas will be gladly excepted.

p.s. i've tried fsck -f :(

---

### Post by hoboken on 2007-06-20
Sorted it out, guys. I used acronis disk director on windows to resize the partition, it's a great program. Didn't even have to use the boot disk on it afterwards or anything, it just worked.

Thanks for your help!

---

