---
title: "[SOLVED] Windows partition disappeared in 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by FreewheelinFrank on 2007-10-22
In Ubuntu 7.04 I could see my Windows partition no probs.

In 7.10 I can't.

What gives?

---

### Post by SOULRiDER on 2007-10-22
Did you upgrade or did you make a fresh install? Try mounting it manually.

---

### Post by FreewheelinFrank on 2007-10-22
> Did you upgrade or did you make a fresh install? Try mounting it manually.

Upgrade. How do I do that?

Kubuntu wouldn't see the partition without mounting it manually, but I can't see how to do it in Ubuntu: obviously I'm being particularly thick today. 

Help appreciated, thanks.

---

### Post by bumanie on 2007-10-22
I am not in front of my ubuntu computer, however, if my memory serves me correctly, you can click on system (which should be accessible from your home folder). This should show up all your drives and partitions. If system is not listed in your home folder, investigate preferences or administration. 
Does GRUB list your windows OS at start up?

---

### Post by travis31 on 2007-10-22
@FreewheelinFrank
For me, after upgrading to 7.10, the Windows entry on the GRUB list went away. On checking in /boot/grub/menu.lst, I found that the Windows entry was commented (had a # at the start of the line). If this is the same case for you, you can just remove the # from the the 4 lines starting at where it lists your Windows entry in menu.lst and you should be all set.

---

### Post by move2linux on 2007-10-22
i have the same problem with my gutsy :( when i have the last update my win part has gone and i don't know what to do :(

---

### Post by FreewheelinFrank on 2007-10-22
The partition is there and bootable in GRUB, just not readable in Ubuntu. All my music tracks are on the Windows partition and Amarok can't see them anymore. :(

> investigate preferences or administration. 

I can't see where. Any ideas?

---

### Post by FreewheelinFrank on 2007-10-23
/boot/grub/menu.lst

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Any problems here?

---

### Post by FreewheelinFrank on 2007-10-24
Bump.

Do I need to do a fresh install to get Ubuntu to see the Windows partition, I wonder?

---

### Post by travis31 on 2007-10-24
Are you saying that you are able to boot into Windows but cannot access the Windows partition from Ubuntu?

---

### Post by hyper_ch on 2007-10-24
pls post the output of:

```

sudo fdisk -l

```

and

```

df -l

```

---

### Post by Charkel on 2007-10-24
> **hyper_ch said:**
> pls post the output of:

```

sudo fdisk -l

```

and

```

df -l

```
I hade the same problem :( so:

sudo fdisk -l:

> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27f327f3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b71375e

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1275    10241406    7  HPFS/NTFS
/dev/hdb2            1276        7294    48347617+   f  W95 Ext'd (LBA)
/dev/hdb5            1276        4335    24579418+   7  HPFS/NTFS
/dev/hdb6            4336        4397      497983+  82  Linux swap / Solaris
/dev/hdb7            4398        7294    23270121   83  Linux


df -l :
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb7             22904732   5997700  15743528  28% /
varrun                  517816        88    517728   1% /var/run
varlock                 517816         0    517816   0% /var/lock
udev                    517816        88    517728   1% /dev
devshm                  517816         0    517816   0% /dev/shm
lrm                     517816     34696    483120   7% /lib/modules/2.6.22-14-generic/volatile
/dev/hdd                605424    605424         0 100% /media/cdrom1


---

### Post by MegaJim on 2007-10-24
can you please post the output from

```
cat /etc/fstab
```

it would help if you could wrap the output in code tags to make it easier for us to read, thanks, e.g.

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27f327f3

Device Boot Start End Blocks Id System
/dev/hda1 * 1 14593 117218241 7 HPFS/NTFS

Disk /dev/hdb: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b71375e

Device Boot Start End Blocks Id System
/dev/hdb1 1 1275 10241406 7 HPFS/NTFS
/dev/hdb2 1276 7294 48347617+ f W95 Ext'd (LBA)
/dev/hdb5 1276 4335 24579418+ 7 HPFS/NTFS
/dev/hdb6 4336 4397 497983+ 82 Linux swap / Solaris
/dev/hdb7 4398 7294 23270121 83 Linux 
```

---

### Post by FreewheelinFrank on 2007-10-24
> **travis31 said:**
> Are you saying that you are able to boot into Windows but cannot access the Windows partition from Ubuntu?

Exactly. Just so. Precisely. And a bit of a pain it is too: I don't want to duplicate 7GB of music files on my Ubuntu partition, plus it's useful to be able to access other files too.

---

### Post by FreewheelinFrank on 2007-10-24
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47594758

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS
/dev/sda2            7296        9729    19551105    5  Extended
/dev/sda5            7296        8314     8185086   83  Linux
/dev/sda6            8315        8664     2811343+  82  Linux swap / Solaris
/dev/sda7            8665        9729     8554581   83  Linux
```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              8056492   3392056   4255184  45% /
varrun                  517056       104    516952   1% /var/run
varlock                 517056         0    517056   0% /var/lock
udev                    517056        92    516964   1% /dev
devshm                  517056        16    517040   1% /dev/shm
lrm                     517056     34696    482360   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda7              8420132    297764   7694640   4% /home
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=50d30fca-86ee-417a-a8a0-5a2a1592c3ad /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=40c15114-6056-4d47-8952-2279a3f85694 /home           ext3    defaults        0       2
# /dev/sda1
UUID=F45CA7925CA74DE4 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=b444f6e4-bb8e-4841-a2cd-b4662f93bfb8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by FreewheelinFrank on 2007-10-25
> **hyper_ch said:**
> pls post the output of:

```

sudo fdisk -l

```

and

```

df -l

```

Done that. What does it mean? :(

---

### Post by speed145a on 2007-10-25
> **FreewheelinFrank said:**
> /boot/grub/menu.lst



Any problems here?

If you are able to boot into your windows partition then this is not where the problem is.

---

### Post by speed145a on 2007-10-25
install gparted via synaptic package manager.  then start it up and see if you can see your windows partition.

if you can see it there, note the device name (/dev/sda2 etc...) try mounting the disk manually by opening a terminal and typing:

```
sudo mount (/dev/yourdevice)
```

see if it will mount this way

edit:  it looks like you windows partition is /dev/sda1 so you could skip the gparted and just try the```
 sudo mount /dev/sda1
```

---

### Post by FreewheelinFrank on 2007-10-25
Ah ha!

> Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, so mounting could be done safely.

I most often hibernate Windows rather than close it, but this didn't seem to be a problem in 7.04. If I shutdown Windows, boot Ubuntu and mount the Windows partition will, Ubuntu subsequently be able to see it even when hibernated, or will I have to shut down Windows everytime?

Obviously I will check this out empirically later, but in theory?

Thanks very much for the help, by the way!

---

### Post by MegaJim on 2007-10-25
I believe theres a way to force it, but when you do that you can cause several problems, the most important of which is the RAM data saved to the disk to enable hibernation could be removed/corrupted, which would cause windows to fail to resume and boot from scratch... Nothing would be harmed by this.. except for any unsaved work you had open before hibernating.

---

### Post by FreewheelinFrank on 2007-10-25
This is because Ubuntu 7.10 can now write to the Windows partition as well as read, isn't it?

If Ubuntu wrote to the Windows partition and Windows as hibernated found the system different after waking up, it would have a hissy fit, throw a wobbly and generally go off into a corner and sulk, I imagine.

Perhaps somebody could confirm this in more technical term, but I guess we can mark this as 'solved'.

Thanks all for the help!

---

### Post by FreewheelinFrank on 2007-10-25
Now I just need to work out how to mark a thread as solved! :???:

---

### Post by Akis on 2007-10-27
I was experiencing the same problem, because I forced vista to shutdown.

That doesn't apply only to hibernation.

---

### Post by Maestro23 on 2007-10-27
> **FreewheelinFrank said:**
> Now I just need to work out how to mark a thread as solved! :???:

If you are in either OS, and don't shut down properly, then when you boot up in the other OS... you will have problems reading/writing to the other OS's drive(s) or partitons.   Have done it from both sides on my machine before.:)

Too mark this thread SOLVED, you need to use the Thread Tools.

---

### Post by sneezymelon on 2007-10-27
hmm, Maestro's right. You need to shut down windows properly

---

### Post by FreewheelinFrank on 2007-10-27
> **Maestro23 said:**
> If you are in either OS, and don't shut down properly, then when you boot up in the other OS... you will have problems reading/writing to the other OS's drive(s) or partitons.   Have done it from both sides on my machine before.:)

Too mark this thread SOLVED, you need to use the Thread Tools.

Gotcha. Ta!

I'm pretty sure this is new in 7.10, because I always used to hibernate Windows (apart from the inevitable update or BSOD of course) and never had this problem in 7.04.

---

### Post by Jaydude765 on 2007-10-30
> **FreewheelinFrank said:**
> Gotcha. Ta!

I'm pretty sure this is new in 7.10, because I always used to hibernate Windows (apart from the inevitable update or BSOD of course) and never had this problem in 7.04.

It is new as far as I can see. I never had this issue for hibernated windows partitions before and never had any problems using them either. As long as you don't delete the hibernation file your good to go.

It is annoying as I prefer to hibernate with the occasional reboot for windows to save time.

Jason

---

