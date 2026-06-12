---
title: "grub setup"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-08-16
thanks for any help.

ive got things setup now but my grub is messed up. or its not on the computer.

heres what i have.
2 HD
3 OS

hda has windows
hdb has kubuntu and vector

I am able to boot all 3 from lilo grub.

but its on a floppy using super grub i dont see how to get the lilo into the mbr on the hard drive so i dont have to go thru all the steps to boot by floppy.
if i remove floppy i boot right into windows at start up

any ideas thanks

---

### Post by jspangler on 2007-08-16
Here's a pretty good grub installation overview. I used these instructions to install grub on my MBR:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by trucker33377 on 2007-08-16
well i gave it a shot didnt work  for me. sudo  commands ended with files not found. super grub setup  is what i used to get on here. in looking at the page you sent me thats how i set it up but it only work from floppy.

---

### Post by jspangler on 2007-08-16
Could you post the output of each of the following:

```
df
sudo fdisk -l
```

from kubuntu?

---

### Post by jspangler on 2007-08-16
Also, do you mean that after you booted into the live cd, you ran "sudo grub' and it said files not found?

---

### Post by trucker33377 on 2007-08-16
kubuntu is installed on the HD thats where i ran it from not the live cd. does that matter?

im thinking i may have messed up on install of these OS.

this is a 120 gig HD ive not used hardly any of it but when i put in the last partition it makes the rest of the HD unuseable. i will run from live cd and post in the morning thxs.

how i did set is like this
1 run dban
2 make 512 MB dos
2 make 512 MB SWAP
3 MAKE KUBUNTU PARTITION 4 GIGS
4 MAKE vector partition.

when i formatted dos it showed 512 formatted if that matters

---

### Post by alienexplorers on 2007-08-17
Boot your live-cd.  start it up.  Enter Terminal.  Enter sudo grub.
Enter find /boot/grub/stage1
Enter root(hd#,#)    #,# is your drive and partition numbers
Enter setup (hd#)   # is your drive number
quit grub
reboot

---

### Post by trucker33377 on 2007-08-17
> **alienexplorers said:**
> Boot your live-cd.  start it up.  Enter Terminal.  Enter sudo grub.
Enter find /boot/grub/stage1
Enter root(hd#,#)    #,# is your drive and partition numbers
Enter setup (hd#)   # is your drive number
quit grub
reboot

thanks but i get error 15 file not found for find stage 1

---

### Post by jspangler on 2007-08-17
Yes, I believe this is because you never installed grub on your kubuntu device. Try booting the live-cd and following the instructions from the first page I sent you. I think that might work better. The problem here is that it can't find the boot directory because there is none. So give it another try with the live cd, but without the find instructions.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Also, what was the last operating system you installed? Windows, kubuntu, or vector?

If this doesn't work, please go to the terminal and give us the output of the following commands (after booting to Kubuntu):

```
df
sudo fdisk -l
```

---

### Post by trucker33377 on 2007-08-17
vector this time ive done done it both ways

---

### Post by trucker33377 on 2007-08-17
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
43 heads, 41 sectors/track, 277026 cylinders
Units = cylinders of 1763 * 512 = 902656 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2      277025   244196352    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          66      530113+   7  HPFS/NTFS
/dev/sdb2              67         128      498015   82  Linux swap / Solaris
/dev/sdb3           14229       14593     2931862+  83  Linux
/dev/sdb4   *         129         614     3903795   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 129 MB, 129990656 bytes
16 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         990      126703+   6  FAT16
ubuntu@ubuntu:~$

---

### Post by jspangler on 2007-08-17
Could you also run the command:

```
df
```

This will tell us which partition kubuntu is on. We need this information to install grub correctly.

ADDITION:

Could you also run the following commands and show the output:

```
ls /
```

---

### Post by trucker33377 on 2007-08-17
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   517540     33788    483752   7% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   517540     33788    483752   7% /lib/modules/2.6.20-15-generic/volatile
varrun                  517540        96    517444   1% /var/run
varlock                 517540         0    517540   0% /var/lock
udev                    517540       168    517372   1% /dev
devshm                  517540         0    517540   0% /dev/shm
tmpfs                   517540      3300    514240   1% /tmp
/dev/sdd1               126656     50720     75936  41% /media/disk
ubuntu@ubuntu:~$

---

### Post by trucker33377 on 2007-08-17
when i try to run vector's auto reinstall for grub it does not see ubuntu.

---

### Post by jspangler on 2007-08-18
First, did you run that command from Kubuntu or from the live cd? Second, if you have Vector working with grub, you can probably manually add Kubuntu to grub. That shouldn't be too difficult.  Also, I think I've figured out how to install grub from the live cd for kubuntu.

DO THIS ONLY IF /dev/sdb3 is your kubuntu drive!!!!

Open the live cd. Go to System > Administration > Gnome Partition Editor.

Choose /dev/sdb (or possible /dev/hdb). Right click on /dev/sdb3 (or /dev/hdb3). Click "Manage Flags". Mark as "boot".

Then install grub.

Here's how.

WARNING: This will get rid of any other bootloader or windows loader. I don't think there will be any problems, but Vista occasionally gets pissy about such things.

```

sudo grub
root(hd1,2) 
setup (hd0)
quit
```

Reboot. See if that works.

---

### Post by trucker33377 on 2007-08-19
thanks i used dban and started all over. tis time ive gone with ubuntu not kubuntu. when i tried to setup vector it showed an error part way thru so i aborted. 

this is the frist time ive been able to bring all my windows files over to ubuntu, I liked that alot,

the only reason i want vector is so i can figure it out some im installing it on some older laptops. ive not been able to use any ubuntu for them or i would. my fisrt thought was to use puppy on them but i cant open any web pages with it

there alot i dont know about linux

so i just keep trying

---

### Post by jspangler on 2007-08-20
Learning linux is a fun process (to me anyway)! Enjoy!

---

### Post by trucker33377 on 2007-08-28
im learning all right keeps me on my toes

---

