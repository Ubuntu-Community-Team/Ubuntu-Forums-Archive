---
title: "How to make partion writable"
date: 2007-04-22
forum: Apple Intel Users
---

### Post by tuna74 on 2007-04-22
Hi, I have an iMac with a 500 GB HDD. On that HDD I have a 350 GB partion that I was planning to use as a shared partion for all users. Here is the fstab info:

# /dev/sda4
UUID=aeb71828-eaa2-4285-a5a1-440af883adc3 /media/shared   ext3    rw,user        0       2

The problem is that I can't write anything to the partition. What should I write in the fstab?

---

### Post by davidgarcin on 2007-04-22
According to that entry, the drive isn't being automatically mounted at start-up.  Before the 'rw' option, add 'auto'.   You're actually already allowing write access with the rw option (read/write).  Alternately, just replace "rw,user" with "defaults".

For more fstab options and examples, see [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html).

-Dave

---

### Post by tuna74 on 2007-04-23
This is my fstab:

tuna@tuna-no-imac:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b4cd62bb-03c0-40d3-9f41-c12ce0267655 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=aeb71828-eaa2-4285-a5a1-440af883adc3 /media/shared   ext3    auto, user, rw        0       2
# /dev/sda5
UUID=82347368-dcaa-4bde-8269-252dbe2c57da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

But I still can't write to the sda4 partion and it is not mounted at /media/shared. Any ideas?

---

### Post by tuna74 on 2007-04-23
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b4cd62bb-03c0-40d3-9f41-c12ce0267655 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
/dev/sda4	/media/shared   ext3    auto,user, rw        0       2
# /dev/sda5
UUID=82347368-dcaa-4bde-8269-252dbe2c57da none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

If I change the fstab to this I can't even mount the partition....any ideas what to do?

---

### Post by davidgarcin on 2007-04-23
so when you have fstab in the first configuration, does it automount at all?  after you log on, type 'mount' at the console and see if /dev/sda4 shows up in the list.

if it doesn't show up, try replacing 'auto, user, rw' to 'defaults'

---

### Post by tuna74 on 2007-04-24
I think I have messed up the fstab, because when I only have /dev/sda4 the system will not mount that partition at all. And if I comment sda4 out, only root can mount the partition.....pretty sad, eh?

---

### Post by davidgarcin on 2007-04-26
under Edgy and Feisty, I think you need the UID bit in the fstab for a partition to mount, so only putting /dev/sda4 won't work.

If you comment the line out in fstab, then it's normal that only root can mount the partition.  How are you mounting it then?  Are you running: sudo mount -t ext3 /media/shared?  What output does it give?  If you run that command and then mount, what output does it give then?

You didn't tell me what the mount command gave you when you used the first fstab configuration, ie:

UUID=aeb71828-eaa2-4285-a5a1-440af883adc3 /media/shared ext3 auto, user, rw 0 2

Copy paste the output so I can see what's going on.  Also replace "auto,user,rw" with "defaults" and post the output of mount under that config as well.

---

### Post by davidgarcin on 2007-04-26
also, try taking out the spaces in the options... ie. auto,user,rw instead of auto, user, rw.

I have no idea if that makes a difference, but you usually don't see spaces like that.

---

### Post by psusi on 2007-04-26
Yes, you can not have spaces in the options filed.  Spaces separate the fields, so having a space there means the stuff that follows it is in the next filed, not the options field.

---

### Post by tuna74 on 2007-04-29
For some reason Ubuntu wants to mount the partition to /media/disk-1, so I use this in my fstab:

# /dev/sda4
UUID=aeb71828-eaa2-4285-a5a1-440af883adc3       /media/disk-1    ext3 auto,user,rw      0       2


It seems to work....thanks for all your help!

---

### Post by tuna74 on 2007-04-30
Actually, the fstab does not work at all, I can't even boot into Ubuntu when I have it like that. It drops me right into a shell and I have to enter my root password (which I have set) and then I write "exit" and then everything works.....pretty weird.....

---

### Post by davidgarcin on 2007-04-30
You've confused the heck out of me.  I thought you said it was working?  Post your fstab in its entirety.

---

