---
title: "Installed Ubuntu Windows won't boot"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by bettabruce on 2007-06-04
windows is not listed as an OS in Grub,

and I have no idea how to make it detect.

Thanks in advance.

---

### Post by oilchangeguy on 2007-06-04
> **bettabruce said:**
> windows is not listed as an OS in Grub,

and I have no idea how to make it detect.

Thanks in advance.

when you installed ubuntu, did you perhaps allow it to use the entire hard drive?

---

### Post by bettabruce on 2007-06-04
I used the manual install option,

I deleted my c partition and made the free space into / and swap.

I have XP on my d partition and it shows on the ubuntu desktop.

None of my other partitions show on the desktop, but that is another issue.

---

### Post by Dougie187 on 2007-06-04
What does ```
df -h
``` return?

---

### Post by bettabruce on 2007-06-04
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9              16G  2.7G   13G  18% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  120K  506M   1% /proc/bus/usb
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hda5              23G  8.0G   15G  36% /media/sda5

---

### Post by Dougie187 on 2007-06-04
Can you post the contents of your /boot/grub/menu.lst file?

```
cat /boot/grub/menu.lst
```

---

### Post by bettabruce on 2007-06-04
I don't know how much of this is needed, but

here it is:

loko@TheMFShizit:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=65693135-2abd-498c-8cbc-988f42046546 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=65693135-2abd-498c-8cbc-988f42046546 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,8)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=65693135-2abd-498c-8cbc-988f42046546 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,8)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
loko@TheMFShizit:~$

---

### Post by bettabruce on 2007-06-04
sorry, I don't know where all the smilies are coming from

---

### Post by bettabruce on 2007-06-04
I think that 8's should be in the place of the smiles, sorry.

---

### Post by Dougie187 on 2007-06-04
can you post the contents from
```
cat /etc/fstab
```

---

### Post by k1001001 on 2007-06-04
It might help to use the CODE tags to prevent smilies next time as well. To do that, type this:
> <CODE></CODE>
except use [ ] instead of <>.

---

### Post by bettabruce on 2007-06-04
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=65693135-2abd-498c-8cbc-988f42046546 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=AE5C72B95C727C41 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda8       /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda10
UUID=79e991f4-a299-475e-ae37-acfd20790817 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Dougie187 on 2007-06-04
Ok. So it looks like your windows is still there. Now could you explain one more time how you have it all set up?
Do you have two seperate disks that are in your computer? Or one disk with 3 partitions (swap, ubuntu, and windows)?

---

### Post by Dougie187 on 2007-06-04
You are going to have to add something like this to your /boot/grub/menu.lst file but i just need to figure out the right settings
```
title Windows
root (hd1,0)
savedefault
makeactive
chainloader +1
```

---

### Post by bettabruce on 2007-06-04
I had a dual boot with windows me on c,

XP on D, and three other fat 32 partitions.

All five partitions are on the same 250GB hard drive.

When I installed ubuntu, I deleted c and partitioned the free 

space to a first partition (/) and a second partition (swap).

Thanks again.

---

### Post by Dougie187 on 2007-06-04
Ok then try adding this into your /boot/grub/menu.lst file and see what happens.

```
title Windows
root (hd0,3)
savedefault
makeactive
chainloader +1
```

The only part im not completely sure about is that (hd0,3) part. You will need to mess with the 3 (partition number) to find the right one for your windows.

---

### Post by bettabruce on 2007-06-04
I am not sure how to get to my /boot/grub/menu.lst 

i pasted that into the terminal but permission is denied

---

### Post by Dougie187 on 2007-06-04
you can hit alt+f2 and type
```
gksudo gedit /boot/grub/menu.lst
```

or if you like to use vim in command line it is
```
sudo vim /boot/grub/menu.lst
```

---

