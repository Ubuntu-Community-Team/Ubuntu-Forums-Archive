---
title: "where did it go"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-27
Can anyone tell me where to get diskmounter.   It was available a couple days ago but has gone poof.

Thank You

---

### Post by Perfect Storm on 2006-12-27
Disk mounter that you can get to the panel? Just right click the panel and click add to panel. You'll find disk mounter there.

---

### Post by squrl on 2006-12-27
That might work but what I was referring to was called diskmounter and it would mount all the available disks when you boot up.   

wget [http://www.ubuntulinux.nl/files/diskmounter](http://www.ubuntulinux.nl/files/diskmounter)

Don't think it is the same thing but will give it a try

Thanks

---

### Post by taurus on 2006-12-27
If you want to mount all the disks when you boot up, then add them to your /etc/fstab.  No need to add anything else to the system...

---

### Post by squrl on 2006-12-27
Sounds like a good idea.  I think you might just want to see my ignorance. lol   I tied that once and ended up having to reload the whole system. I haven't been able to identify them so can't add.

Please. a small bone for this dumb dog. 

Thanks. I been at this since six this morning and am so tired I'm getting even more stupid.

---

### Post by taurus on 2006-12-27
Okay, let's walk through this whole thing together.  I first need to see the partitions of your harddrive (and would be nice if you can tell me which partitions you want to mount) so open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here...

```
sudo fdisk -l
(use the same password that you log in with...)
```

---

### Post by squrl on 2006-12-27
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7240    58155268+  83  Linux
/dev/sda2           13926       14589     5333580    5  Extended
/dev/sda3   *        7241       13925    53697262+  83  Linux
/dev/sda5           14213       14589     3028221   82  Linux swap / Solaris
/dev/sda6           13926       14212     2305264+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


I can't tell you which to mount because I cant get to them to see which has what I am trying to get to.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9772    78493558+  83  Linux
/dev/sdb2           18703       19457     6064537+   5  Extended
/dev/sdb3   *        9773       18702    71730225   83  Linux
/dev/sdb5           19081       19457     3028221   82  Linux swap / Solaris
/dev/sdb6           18703       19080     3036222   82  Linux swap / Solaris

Partition table entries are not in disk order
squrl@squrl-desktop:~$

---

### Post by taurus on 2006-12-27
Do you have multi Linux distros running on your machine?  Just do you know, you don't have to create a separate swap partition each time install a Linux distro.  They all can share the same swap...

Anyway, what does your /etc/fstab look like then (means paste it here)?

```
cat /etc/fstab
```

---

### Post by squrl on 2006-12-27
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fd3da2f4-3146-41ac-9d45-9eda07c0390d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=52685fc4-0daa-478f-b3d6-d87e0573779b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


Yes to multi ubuntu's on that drive . When I learn enough I want to wipe everything clean and make a single app. but don't want to do that till I get the info off the drive I think I need.

---

### Post by taurus on 2006-12-27
So, you are using Ubuntu on /dev/sda3 with swap on /dev/sda6.

From a terminal, edit your /etc/fstab this command.

```
gksudo gedit /etc/fstab
```
Scroll all the way down to the end of the file and add the following lines to it.

```

/dev/sda1   /media/sda1   ext3   defaults   0   1
/dev/sdb1   /media/sdb1   ext3   defaults   0   1
/dev/sdb3   /media/sdb3   ext3   defaults   0   1
/dev/sda5   none   swap   sw   0   0
/dev/sdb5   none   swap   sw   0   0
/dev/sdb6   none   swap   sw   0   0

```
Save it (be real careful with your typing or just cut 'n paste those lines to your /etc/fstab then...), create a new mount points for those partitions, and mount them...

```
sudo mkdir /media/sda1  /media/sdb1  /media/sdb3
sudo mount -a
df -h  <-- you will see all your partitions from here...
free   <-- you will see the large amount of swap space here...
```

---

### Post by squrl on 2006-12-27
Done.

I still don't see the other directories.

---

### Post by taurus on 2006-12-27
Maybe a reboot!!!

---

### Post by squrl on 2006-12-27
df -h


squrl@squrl-desktop:~$ df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              51G  1.9G   47G   4% /
varrun                506M  128K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  489M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              55G  2.2G   50G   5% /media/sda1
/dev/sdb1              74G  2.5G   68G   4% /media/sdb1
/dev/sdb3              68G  1.9G   63G   3% /media/sdb3
squrl@squrl-desktop:~$

---

### Post by taurus on 2006-12-27
Well, there they are...

```

Filesystem Size Used Avail Use% Mounted on
/dev/sda3 51G 1.9G 47G 4% /
varrun 506M 128K 506M 1% /var/run
varlock 506M 0 506M 0% /var/lock
procbususb 10M 144K 9.9M 2% /proc/bus/usb
udev 10M 144K 9.9M 2% /dev
devshm 506M 0 506M 0% /dev/shm
lrm 506M 18M 489M 4% /lib/modules/2.6.17-10-generic/volatile
[B][COLOR="Red"]/dev/sda1 55G 2.2G 50G 5% /media/sda1
/dev/sdb1 74G 2.5G 68G 4% /media/sdb1
/dev/sdb3 68G 1.9G 63G 3% /media/sdb3[/COLOR][/B]

```

---

### Post by squrl on 2006-12-27
Rebooted and got all three.  Something is missing. There should be a part of that drive with other files. I think it was saved as etc3. Not sure about that but thats what I was trying to get to.

---

### Post by taurus on 2006-12-27
You can use nautilus to browse those directories or you can run this from a command line...

```
ls -la /media/sda1
```

p.s.  Maybe next time you can send me that $100 bucks and I can be your manual until you hit 75...  :mrgreen:

---

### Post by squrl on 2006-12-27
xxx

---

### Post by taurus on 2006-12-27
> **squrl said:**
> Be careful what you wish for. A hundred bucks would be a bargain.

#-o

---

### Post by squrl on 2006-12-27
Challenge ....

---

### Post by taurus on 2006-12-27
> **squrl said:**
> Challenge ....

You start a class on this stuff on the web I'll provide the web site and pay you to boot. 

I'll even put up phpbb 

I didn't hear youuuuu.
Maybe I should do that since I am looking for another part-time job right now!!!  :-k

---

### Post by squrl on 2006-12-27
xxx

---

