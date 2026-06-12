---
title: "[SOLVED] Separate partition for /home"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-03-21
I'm ready to "take the plunge" and make a partiton for my (now folder) /home.

I've read Psychocats and the Ubuntu Blog

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

and

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I fired up my gutsy LiveCD, opened GParted, and got as far as resize when I couldn't understand what to do.

According to Disk Usage Analyzer: about 291 gig is Total Capacity, 30.7 gig in use and 260.8 gig available. 

Following Psycho's idea, once I get it done, I will have about 260 /home and the rest is OS files, but, for the approx. 25 gig that is currently the size of /home, what about that space? Since it's sitting in the OS . . . well let me show you:

mark@Lexington-19:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

I'm not good with the above. I know that /dev/sda1 is the big area, but am unsure about /dev/sda2 and DON'T, repeat, DON'T want to screw this up.

So my question is: once the /home is it own partition, should I resize the other partition to reflect the space gained in the OS partition space, or is it better to leave well enough alone?

---

### Post by Oldsoldier2003 on 2008-03-21
> **Mark_in_Hollywood said:**
> I'm ready to "take the plunge" and make a partiton for my (now folder) /home.

I've read Psychocats and the Ubuntu Blog

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

and

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

I fired up my gutsy LiveCD, opened GParted, and got as far as resize when I couldn't understand what to do.

According to Disk Usage Analyzer: about 291 gig is Total Capacity, 30.7 gig in use and 260.8 gig available. 

Following Psycho's idea, once I get it done, I will have about 260 /home and the rest is OS files, but, for the approx. 25 gig that is currently the size of /home, what about that space? Since it's sitting in the OS . . . well let me show you:

mark@Lexington-19:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

I'm not good with the above. I know that /dev/sda1 is the big area, but am unsure about /dev/sda2 and DON'T, repeat, DON'T want to screw this up.

So my question is: once the /home is it own partition, should I resize the other partition to reflect the space gained in the OS partition space, or is it better to leave well enough alone?

post the output of```
 cat /etc/fstab
``` and we can tell you a little more.

---

### Post by Mark_in_Hollywood on 2008-03-21
mark@Lexington-19:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f75a181-c417-4e11-9073-6d27c34db623 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0

(Sorry I can't get the foregoing into neat columns)

---

### Post by herbster on 2008-03-21
What you have with /dev/sda5 is what's known as a swap partition. How much system RAM do you have? You can quite safely and simply follow the guideline of having a swap partition that is roughly 1-2x the size of your system RAM. AFAIK, this swap partition is used when your system RAM is exhausted and/or to store a system image when you hibernate your computer.

You want to make 3 partitions: a root (/), home (/home) and a swap. You can make 3 partitions as follows:

root (/) = 10gb (you would hardly need more than this, but you can make it 15 if you will be installing some games that may have their data installed to root)
home (/home) = 275gb
swap = 4gb

This is roughly the numbers that would make sense. You can also make the /home something like 20-30gb and take the remaining space and just make a new partition that doesn't have any important data files on it, so you can back up to it or something, should your /home get corrupted or what have you.

Remember, doing this will format your drive, which is what I'm assuming you want to do anyhow.

---

### Post by Oldsoldier2003 on 2008-03-21
I think i would go along the lines of herbster's suggestion but would prune back size of /home to 30-50MB and create a data partition with the examining space.

Then you could just link the data partition

---

### Post by Mark_in_Hollywood on 2008-03-21
> **herbster said:**
> What you have with /dev/sda5 is what's known as a swap partition. How much system RAM do you have?

I have 1 gig. As for the rest of your response, I'm not understanding it. 

I'll try again. I know I can change partition sizes. I know I can make a new partition in the 260 odd gig of space I have. As I intended as much when gutsy was installed, I now want a separate partition for the directory that is now part of sda1 and known as /home. I also don't understand how the OS will work when the "/home" is a partition. How do files get saved/read across this partition? Please excuse my ignorance here, but I really cannot harm my current /home.

---

### Post by Oldsoldier2003 on 2008-03-21
> **Mark_in_Hollywood said:**
> I have 1 gig. As for the rest of your response, I'm not understanding it. 

I'll try again. I know I can change partition sizes. I know I can make a new partition in the 260 odd gig of space I have. As I intended as much when gutsy was installed, I now want a separate partition for the directory that is now part of sda1 and known as /home. I also don't understand how the OS will work when the "/home" is a partition. How do files get saved/read across this partition? Please excuse my ignorance here, but I really cannot harm my current /home.

when home is on a separate partition ubuntu will mount it as part of the file system just as if it were in the / (root) thats why you add it to the fstab

example
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1[COLOR="Red"](root or main partition)[/COLOR]
UUID=7f6e3501-e52e-4e9f-8503-55cae5e41e01 /               ext3    defaults,errors=remount-ro,noatime,data=writeback 0 1
# /dev/sdb5 [COLOR="Red"](swap partition)[/COLOR]
UUID=65b2560d-6ff9-41e8-b835-726e204d4039 none            swap    sw              0       0
# [COLOR="Red"]home partition is sda3![/COLOR]
/dev/sda3       /home	        ext3	 nodev,nosuid 0 2

[COLOR="Red"]# a separate data partion on sda4[/COLOR]
/dev/sda4 	/mnt/data	ext3     defaults 0 0

<snip>

```

---

### Post by herbster on 2008-03-21
> **Mark_in_Hollywood said:**
> I also don't understand how the OS will work when the "/home" is a partition. How do files get saved/read across this partition? Please excuse my ignorance here, but I really cannot harm my current /home.

Okay, let's just clarify then, you are going to reinstall Ubuntu and want to keep the data you have on your home partition, right?

---

### Post by tad1073 on 2008-03-21
Here is my fstab file. I have 3 seperate hdd's, one for root, 1 for home and 1 for storage.

```
~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a1f7cbcb-aad7-445a-8195-ecb2e8e1c695 /               ext3    defaults,errors=remount-ro,noatime,nodiratime 0       1
# /dev/sdb1
UUID=23f4a9e8-f4d6-4eed-88af-74033e8f929e /home           ext3    defaults,noatime,nodiratime        0       2
# /dev/sdc1
UUID=5ef6b6d8-42a3-4c8c-adcb-436305af6c70 /media/sdc1     ext3    defaults        0       2
# /dev/sda2
UUID=8c41466d-e2bc-4563-bca1-75d8679685c0 none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

>  I also don't understand how the OS will work when the "/home" is a partition. How do files get saved/read across this partition? Please excuse my ignorance here, but I really cannot harm my current /home.
I just works, trust these guys, they know what they're doing.

I partitioned my drive's when I installed but the way your doing it will work just fine.

---

