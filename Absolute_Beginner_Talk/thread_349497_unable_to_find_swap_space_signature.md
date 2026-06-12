---
title: "unable to find swap space signature"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by vroy on 2007-01-30
Hi,
     I upgraded my laptop from dapper to edgy the other day. It was working fine. But, I think I kept it in hibernating mode 2 days ago. Since then, I'm getting the following message while booting the machine.
unable to find swap space signature [failed]
I searched previous posts and realized some of you have already faced this problem and fixed it. Pl let me know what should I do.
This is my  /etc/fstab file
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=6163b164-59d6-45d5-aa93-edbd39fe3610 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=F2CC83DCCC83998D /media/hda1 ntfs defaults 0 0
# /dev/hda4 -- converted during upgrade to edgy
UUID=4C03-CD2E /osshare vfat defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=0092c168-5f06-415b-a746-8936ed80ac94 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---------------------------------------------------------
free -m
             total       used       free     shared    buffers     cached
Mem:           503        458         44          0         66        225
-/+ buffers/cache:        166        337
Swap:            0          0          0
-----------------------------------------------------------
sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/hda2            3316        3497     1461915   82  Linux swap / Solaris
/dev/hda3            3498        6074    20699752+  83  Linux
/dev/hda4            6075        7296     9815715    b  W95 FAT32



Regards

---

### Post by taurus on 2007-01-30
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=0092c168-5f06-415b-a746-8936ed80ac94 none swap sw 0 0
```
with this line.

```
/dev/hda2   none   swap   sw   0   0
```
Save it and reboot.  Then, see if your swap is on.

```
free
```

---

### Post by vroy on 2007-01-30
Hi taurus,
                 I just did what you asked me to do. but, while booting I still got the message
unable to find swap space signature [fail]
This is what I got now. swap is not on yet
free
             total       used       free     shared    buffers     cached
Mem:        515788     263564     252224          0       8520     148960
-/+ buffers/cache:     106084     409704
Swap:            0          0          0
by the way my new fstab file
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=6163b164-59d6-45d5-aa93-edbd39fe3610 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=F2CC83DCCC83998D /media/hda1 ntfs defaults 0 0
# /dev/hda4 -- converted during upgrade to edgy
UUID=4C03-CD2E /osshare vfat defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
/dev/hda2   none   swap   sw   0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-01-30
Try these from a terminal.

```
sudo mkswap /dev/hda2
sudo swapon /dev/hda2
free
```

If it works (from the output of the last command), reboot and see if your swap mounted automatically.

---

### Post by vroy on 2007-01-30
Hi taurus,
                  Thanks a lot. It's working now.
Regards

---

### Post by taurus on 2007-01-30
Great.

---

### Post by vroy on 2007-01-30
Hi,
    I kept my laptop in hibernating mode and now while I'm rebooting, I'm getting the same error message:
unable to find swap space signature [failed]

so then do I have to run these two commands mkswap and swapon each time I hibernate the machine?

---

### Post by taurus on 2007-01-30
> **vroy said:**
> Hi,
    I kept my laptop in hibernating mode and now while I'm rebooting, I'm getting the same error message:
unable to find swap space signature [failed]

so then do I have to run these two commands mkswap and swapon each time I hibernate the machine?

Yip.  Looks like hibernation kills your swap.  ](*,)

---

### Post by vroy on 2007-01-30
that's really irritating. Is there any way I can fix it.

---

### Post by shareMenaPeace on 2007-01-30
Same problem (switched to hibernate).

---

### Post by shareMenaPeace on 2007-01-30
Fixed it with help of this topic:
[http://ubuntuforums.org/showthread.php?t=346157&highlight=unable+swap+space+signature](http://ubuntuforums.org/showthread.php?t=346157&highlight=unable+swap+space+signature)

What i did was 

Getting the exact device (swap)
```
sudo fdisk - l
```

Than i formated the swap 
```
sudo mkswap /dev/YOUR_SWAP_DEVICENAME
```

Restarted and error is gone.

---

### Post by vroy on 2007-01-30
exactly that's what I was suggested to do and it's working. but, once I hibernate the machine, it's showing the error again.

---

### Post by kapayama on 2007-02-05
I experienced the same problem. The solution from 
[https://launchpad.net/ubuntu/+bug/66637](https://launchpad.net/ubuntu/+bug/66637)
worked for me.

---

### Post by Ksks on 2007-02-05
> **taurus said:**
> Try these from a terminal.

```
sudo mkswap /dev/hda2
sudo swapon /dev/hda2
free
```

If it works (from the output of the last command), reboot and see if your swap mounted automatically.

I had exactly the same problem as vroy. Your solution works for me, except that swap is never mounted automatically, and I have to do this manually each time. Do you have any idea about solving this ?

---

### Post by maxlive on 2007-02-25
ive made a terrible mistake: i give the command sudo mkswap on the boot partition instead of swap one. now my pc dont work. someone could help me.
 with a live distribution i can see my hard disk and /dev/hda1 is swap instead of ext3
ive tried with fsck -b 32768 /dev/hda1
but ive this error :
fsck.swap not found
thanks

---

