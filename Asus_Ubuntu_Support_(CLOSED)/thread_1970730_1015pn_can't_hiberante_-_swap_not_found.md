---
title: "1015pn can't hiberante - swap not found"
date: 2012-05-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Forbees on 2012-05-01
i have 2gigs of ram, and to hibernate i've read that you need the same amount of swap as ram - some people say more

so i know it's overkill but i have the extra room and gave myself 4gigs of swap . .  just because . . i can?


when running ```
pm-hibernate
```
screen goes black and i get an error saying it can't try swap - try ```
swapon -a
```

so . . . . 
```
forbees@Kurisu:~$ swapon -a
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory
forbees@Kurisu:~$
```

so um . . . what now? i'd like to hibernate. the all powerful google has failed me in trying to find help for this. the closest i've gotten is a guy with an error message about the swap not being found during boot (which i had but went away on it's own)

---

### Post by Forbees on 2012-05-02
bump anyone?

---

### Post by mtron on 2012-05-14
```
sudo fdisk -l
sudo blkid
```

Make sure the entries in /etc/fstab match the UUIDs reported by blkid.

For hibernation (suspend to disk) check that the swap uuid in the '/etc/initramfs-tools/conf.d/resume' file is right.

If you update the uuid there run 
```
sudo update-initramfs -u
```

---

### Post by Forbees on 2012-05-22
```
forbees@Kurisu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d25a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   479604735   239801344   83  Linux
/dev/sda2       479604736   488396799     4396032   82  Linux swap / Solaris
forbees@Kurisu:~$ sudo blkid
/dev/sda1: UUID="33de1231-9a4f-4605-acd7-6d77ae2eacde" TYPE="ext4" 
/dev/sda2: UUID="30f80453-21bb-4d1d-bd89-a364d29a9d58" TYPE="swap" 
```


fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=33de1231-9a4f-4605-acd7-6d77ae2eacde /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=6517e7f6-3531-4a5b-bc3c-755162dc6f07 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```



so copypasta the UUID from blkid to the UUID for swap in fstab?

---

### Post by mtron on 2012-05-22
yes. that should do it. after your edit to fstab run 
```
sudo mount -a
``` 

to activate the new settings and check with the "free" command from the terminal that the swap space is in use

---

### Post by Forbees on 2012-05-22
```

forbees@Kurisu:~$ sudo fdisk -l
[sudo] password for forbees: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007d25a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   479604735   239801344   83  Linux
/dev/sda2       479604736   488396799     4396032   82  Linux swap / Solaris
```
```
forbees@Kurisu:~$ sudo blkid
/dev/sda1: UUID="33de1231-9a4f-4605-acd7-6d77ae2eacde" TYPE="ext4" 
/dev/sda2: UUID="30f80453-21bb-4d1d-bd89-a364d29a9d58" TYPE="swap" 
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=33de1231-9a4f-4605-acd7-6d77ae2eacde /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=30f80453-21bb-4d1d-bd89-a364d29a9d58 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```


running pm-hibernate made me think it hibernated - no errors. but on reboot still the error of swap not found and it didn't hibernate


do i need to do something at ```
/dev/mapper/cryptswap1 none swap sw 0 0
``` ??

---

### Post by mtron on 2012-05-23
as said above:
> 
For hibernation (suspend to disk) check that the swap uuid in the '/etc/initramfs-tools/conf.d/resume' file is right. and don't forget to run
```
sudo update-initramfs -u
```
after the change to the initramfs file.


```
sudo fdisk -l
...
/dev/sda7            3630        3826     1582080   82  Linux swap / Solaris
...
```


```
sudo blkid
...
/dev/sda7: LABEL="swap" UUID="d2df4336-5fe1-42d1-888c-3157aa4cd8c7" TYPE="swap" 
...
```


```
cat /etc/fstab
...
# swap was on /dev/sda7 during installation
UUID=d2df4336-5fe1-42d1-888c-3157aa4cd8c7 none            swap    sw              0       0
```

```
cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=d2df4336-5fe1-42d1-888c-3157aa4cd8c7
```

---

### Post by Forbees on 2012-05-23
ah see the resume file was still different so i fixed that
```
sudo gedit /etc/initramfs-tools/conf.d/resume

```

ran
```
sudo update-initramfs -u
```

everything seems fine

```
 sudo swapon -a
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory

```


still no swap?!

---

### Post by mtron on 2012-05-24
this seems to be a bug. See lp bug [#953875]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/953875"). You might want to login at launchpad and click on the "Does this bug affect you?" link to raise some awareness.

As a temporary workaround comment out the /dev/mapper/cryptswap1 line in /etc/fstab. 

This will leave your swap unencrypted but there seems to be no other fix currently available.

---

### Post by Forbees on 2012-05-25
:D


commenting out that last part see,s to be working. i no longer get the error at boot and ```
sudo pm-hibernate
``` actually hibernates! :D


but i see no options to hibernate other than through terminal

but the thing i don't get is i never told my swap to be encrypted

---

### Post by mtron on 2012-05-26
> **Forbees said:**
> but i see no options to hibernate other than through terminal

```
gksudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```


add the following to the file:

> [Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes


After the next Login, "Hibernate" should show up in the power menu.

---

### Post by Forbees on 2012-05-26
it still doesn't let me select hibernate in the power settings (grey'd out)

---

### Post by Forbees on 2012-05-29
> **mtron said:**
> ```
gksudo gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```


add the following to the file:




After the next Login, "Hibernate" should show up in the power menu.



that did it! :D

when i made that last post i apparently forgot to refresh the page. i didn't see your post until today


i was a little confused at first on that file you told me to edit being empty, but everything is fine now (hibernate wise)

---

### Post by Forbees on 2012-07-31
marked as unsolved due to a new problem >,<


i did a format of my system since my last install was half-assed and i'd get some random error messages


did all the steps as before but now i can't hibernate because the UUID on my swap changes every time i restart...


so why is my swap UUID changing and how do i get it to stay?

---

### Post by Forbees on 2012-08-01
found an old post from 7.04 saying to boot to a live disk, delete and remake the swap

so i did, and now my swap UUID is staying the same...


but when i try to resume from hibernate i get a black screen around the time when i should be prompted to enter my password

---

### Post by Forbees on 2012-08-01
just found out that i get the same black screen when trying to resume from "Sleep"


so . .  no mouse, no keyboard, just a black screen when trying to resume from Sleep and Hibernate

---

### Post by 510carl on 2012-08-04
I have the same problem on my 1015pn. It used to work, now won't wake from hibernate or suspend. I am almost certain this is because I upgraded the nvidea driver to the latest version, which is a beta version. I learned this after extensive google research, has something to with how the driver interacts with the the usb or something. I need to revert to the latest stable version: 295.59. I tried the sudo install thing, but it tells me that I already have the latest version. I have posted on this forum requesting help but no response. I need clear instructions on how to accomplish this, as I am not computer scientist, just a 5+ yrs ubuntu user. I have in the past managed to overcome all ubuntu obstacles, but this one not only ruins my netbook user experience, it has me seriously considering going back to Micro$oft or even using mac. I am getting older and at this point I just want an os that works. Sorry to rant. I hope this info is helpful to you.

---

### Post by Forbees on 2012-08-09
that makes sense... the last install i had didn't have the latest nvidea drivers where this install does


i'll look into reverting and hopefully get back with results in a week

---

### Post by Forbees on 2012-08-09
so work has been slow and i tried a few things.

the idea of it being the drivers seemed like a good culprit . . . but i tried completely removing the Nvidia drivers and still the same thing . .  also tried the "recommended" drivers and the post release ones


the only thing i did different this install vs. the last one was "tips" from [here]("https://sites.google.com/site/mtrons/howtos/eeepc-1015pn")

so something in there i think has to be doing it . .  when i get bored sometime i'll try another reinstall without the tips on that site . . then add them in one by one till i know what's messing it up

---

