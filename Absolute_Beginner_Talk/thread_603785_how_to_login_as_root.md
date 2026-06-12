---
title: "how to login as root"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-11-05
hi guys 

i know u r not supposed to login as root in LINUX.
But i am [COLOR="Blue"]unable to UNMOUNT[/COLOR] my drives
when i try to unmount the drive by right clicking it does not unmount. it says [COLOR="Blue"]You are not privileged to unmount this volume.[/COLOR]
Cliking on DETAILS says that [COLOR="Blue"]only root can unmount[/COLOR]

i tried sudo command but it says that drive is not mounted though i can see the drive physically mounted on my desktop
sandy@sandy-desktop:~$ sudo umount /dev/sdb8
umount: /dev/sdb8: not mounted

please help

regards

---

### Post by kellemes on 2007-11-05
"gksudo nautilus" gives root privileges.

---

### Post by sandysandy on 2007-11-05
> **kellemes said:**
> "gksudo nautilus" gives root privileges.

thanx.

i have logged in as root using the above command, but am not able to unmount some disks on desktop.

1) how can i unmount them.

2) if i shut down computer without unmounting will it cause errors.


regards

---

### Post by aysiu on 2007-11-05
> **sandysandy said:**
> 
1) how can i unmount them. Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` > 2) if i shut down computer without unmounting will it cause errors. No, but physically removing the drive before unmounting it or shutting down the computer could.

---

### Post by kellemes on 2007-11-05
If these partitions are needed by the running system you cannot unmount them..
For this you will need to unmount them from a livecd or something like the GParted-Livecd.

---

### Post by sandysandy on 2007-11-05
> **aysiu said:**
> Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```  No, but physically removing the drive before unmounting it or shutting down the computer could.

thanx.
the outputs are as follows:-

sandy@sandy-desktop:~$ [COLOR="Red"]sudo fdisk -l[/COLOR]

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40634062

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe138e138

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3187    25599546    7  HPFS/NTFS
/dev/sdb2            3188       16581   107587305    f  W95 Ext'd (LBA)
/dev/sdb3   *       16582       19456    23093437+   7  HPFS/NTFS
/dev/sdb5            3188        8286    40957686    7  HPFS/NTFS
/dev/sdb6           13386       13777     3148708+   7  HPFS/NTFS
/dev/sdb7           16452       16581     1044193+   7  HPFS/NTFS
/dev/sdb8           13778       14286     4088511   82  Linux swap / Solaris
/dev/sdb9           14287       14823     4313421   83  Linux
/dev/sdb10          14824       15389     4546363+  83  Linux
/dev/sdb11          15390       16255     6956113+  83  Linux
/dev/sdb12          16256       16451     1574338+  82  Linux swap / Solaris
/dev/sdb13           8287        9738    11663158+  83  Linux
/dev/sdb14           9739       10346     4883728+  83  Linux
/dev/sdb15          10347       10954     4883728+  83  Linux

Partition table entries are not in disk order


sandy@sandy-desktop:~$ [COLOR="Red"]df -h[/COLOR]
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb14            4.6G  2.1G  2.4G  47% /
varrun                502M   88K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  136K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   34M  468M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb15            4.6G  155M  4.3G   4% /boot
/dev/sdb13             11G  173M   11G   2% /home
/dev/sdb11            6.6G  198M  6.1G   4% /media/sdb12
/dev/sdb3              23G  4.4G   18G  20% /media/sdb3
/dev/sdb5              40G   11G   29G  28% /media/sdb5
/dev/sdb6             3.1G   69M  3.0G   3% /media/sdb7
/dev/sdb7            1020M  7.7M 1013M   1% /media/sdb8
/dev/scd1             3.7M  3.7M     0 100% /media/cdrom0

sandy@sandy-desktop:~$ [COLOR="Red"]cat /etc/fstab[/COLOR]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb14
UUID=fee04ac8-860c-4ad0-9262-726d1f0ed7f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb15
UUID=e1353f76-89fe-4979-a736-96dbe998a2cb /boot           ext3    defaults        0       2
# /dev/sdb13
UUID=05de89e5-b7ed-4cb7-b3a9-0d4ee8a72a5c /home           ext3    defaults        0       2
# /dev/sda1
UUID=c4100247-3acf-4805-b7ba-dd694e3d2ef8 /media/sda1     ext3    defaults        0       2
# /dev/sda6
UUID=17bb6ddf-86ee-48b2-9a09-66b446317eda /media/sda6     ext3    defaults        0       2
# /dev/sdb1
UUID=36D883C1D8837DBD /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb9
UUID=177fc08e-8878-43cf-b1b6-ec0df41e18e7 /media/sdb10    ext3    defaults        0       2
# /dev/sdb10
UUID=e6f0ef26-e324-4071-8e3b-e82286e06682 /media/sdb11    ext3    defaults        0       2
# /dev/sdb11
UUID=4963681f-c753-44fb-a294-1bc4869c1a0e /media/sdb12    ext3    defaults        0       2
# /dev/sdb3
UUID=E6E0EB4AE0EB2013 /media/sdb3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=32D42A08D429CEC3 /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb6
UUID=968C32988C32733B /media/sdb7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb7
UUID=6C8804C288048CB0 /media/sdb8     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=3df8da9f-3a36-4e1f-b5e7-44aafbbb48a0 none            swap    sw              0       0
# /dev/sdb12
UUID=984e277e-4974-4596-a959-6466e76d6585 none            swap    sw              0       0
# /dev/sdb8
UUID=1d45da6a-4747-4cac-938b-50e0bc7848f6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
sandy@sandy-desktop:~$ 

regards

---

### Post by aysiu on 2007-11-05
/dev/sdb8 is your swap partition, and you're trying to unmount it?

---

### Post by sandysandy on 2007-11-05
> **aysiu said:**
> /dev/sdb8 is your swap partition, and you're trying to unmount it?

Ok. Thanks a lot.
there are also 3 windows partitions which are not getting unmounted.
is it ok to shut down computer with them still mounted.

regards

---

### Post by kellemes on 2007-11-05
Could it be there is a mix-up between sdb7 and sdb8?
/dev/sdb7 seems to be mounted at /media/sdb8..
just as.. /dev/sdb6 is mounted at /media/sdb7.. little confusing maybe?
Maybe you really want to unmount /dev/sdv7?
Just guessing here..

---

### Post by poudin on 2007-11-05
to log in root u must 1st set a root password

sudo passwd and establish password...then su - will switch to root user

u should check /etc/fstab is correct...then u should be able mount -av

mount -av should attempt to remount any items from /etc/fstab not currently mouted.

cheers abd good luck

---

### Post by sandysandy on 2007-11-05
> **kellemes said:**
> Could it be there is a mix-up between sdb7 and sdb8?
/dev/sdb7 seems to be mounted at /media/sdb8..
just as.. /dev/sdb6 is mounted at /media/sdb7.. little confusing maybe?
Maybe you really want to unmount /dev/sdv7?
Just guessing here..

Basically i can see some discs mounted on my desktop and i was worried that shutting down computer without unmounting may cause errors.
the discs are sdb 8 & 12 which as pointed out are SWAP so i guess i should leave them alone. however, there are 3 windows partitions also on the desktop which r not getting unmounted.

regards

---

### Post by poudin on 2007-11-05
so you must have dual booted the system?

windows partitions only get mounted when you attempt to access them.

---

### Post by ajgreeny on 2007-11-05
Have you tried using the "disk mounter" applet in the panel?  That may help you sort things out.  Right click in an empty part of the panel and chose "Add to Panel" then click on the disk mounter.  It will take up a lot of space because of all the different partitions you seem to have but may be worth it if it helps you out of your difficulty.  Incidentally, why so many partitions; are you multi booting different linux dastros or do you run separate /home, /usr and /tmp partitions?

>  windows partitions only get mounted when you attempt to access them.Are you sure this is so, poudin?  I'm sure that my windows partitions were mounted by the fstab at first when I installed ubuntu 7.10, but I commented out the lines in fstab to stop it happening as I don't want the disk mounted all the time.  The same goes for a second installed ubuntu partition, which I had to comment out.  I now use the disk mounter to do so when** I** want, not when the system wants.

---

### Post by sandysandy on 2007-11-05
> **poudin said:**
> to log in root u must 1st set a root password

sudo passwd and establish password...then su - will switch to root user

u should check /etc/fstab is correct...then u should be able mount -av

mount -av should attempt to remount any items from /etc/fstab not currently mouted.

cheers abd good luck

> **ajgreeny said:**
> Have you tried using the "disk mounter" applet in the panel?  That may help you sort things out.  Right click in an empty part of the panel and chose "Add to Panel" then click on the disk mounter.  It will take up a lot of space because of all the different partitions you seem to have but may be worth it if it helps you out of your difficulty.  Incidentally, why so many partitions; are you multi booting different linux dastros or do you run separate /home, /usr and /tmp partitions?

Are you sure this is so, poudin?  I'm sure that my windows partitions were mounted by the fstab at first when I installed ubuntu 7.10, but I commented out the lines in fstab to stop it happening as I don't want the disk mounted all the time.  The same goes for a second installed ubuntu partition, which I had to comment out.  I now use the disk mounter to do so when** I** want, not when the system wants.

i have multiple partitions as i am using mandriva, win xp, ubuntu. Which are the essential partitions and which partitions can be shared within different linux distros (maybe swap, /home. Are /usr and tmp essential.

how do i use fstab to have more control over what partitions mount at log in.

i have followed the instructions and have loaded the disk mounter on the panel.
but i am unable to unmount the partitions which mounted automatically during log in. however the other partitions which did not mount automatically can be mounted / unmounted. i even logged in as root but could not unmount the partitions. message was You are not privileged to unmount the volume 'HD1.

please advise

regards

---

### Post by ajgreeny on 2007-11-06
>  how do i use fstab to have more control over what partitions mount at log in.You need to work out which lines refer to which partitions in your machine.  As an example, here is my current fstab
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=538e8497-f53f-432d-a661-62b78b3cda2d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
#UUID=00947AAF947AA6B6 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
#UUID=f3d32782-21d6-4411-afb7-eaed46734958 /media/hdb1     ext3    defaults        0       2
# /dev/hda5
UUID=6c8a9e72-8154-48d8-a3c5-ab78e9f2ad2b none            swap    sw              0       0
# /dev/hdb5
#UUID=aa56d5cf-1142-3689-32f6-dd14a55517d1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```hda2 is my main ubuntu install and you will see that the line starting UUID=538e8497-f53f-432d-a661-62b78b3cda2d does not have # at the beginning, ie, is not commented out and will be acted upon.
hda1 is my winxp install and the line starting #UUID=00947AAF947AA6B6 does have the # at the start, put there by me to stop windows mounting at boot up.
hdb1 is my second ubuntu install that I use to test out things before I do it on my main ubuntu installation, just in case I mess things up completely (it's been jolly useful once or twice in my two year linux history.)  The line starts #UUID=f3d32782-21d6-4411-afb7-eaed46734958 and again has a # at the start put there by me.

The two swap partitions are there because I let ubuntu do the partitioning at installation, and neither of them are commented out with the #.  I know I could do away with one of them and use the same for both but it's easiest to let the default install do its thing and not worry about 1.6GB theoretically wasted in 200GB total.  So you see by adding a # to the start of a line in fstab you stop any action occurring on that line at boot time.

So if you want to stop other partitions mounting at boot up simply add a # to the appropriate line in fstab of the system that is running.  In ubuntu you can do it by command ```
gksudo gedit /etc/fstab
``` and then adding the # where needed.  Make a backup first with ```
sudo cp /etc/fstab /etc/fstab.bak
``` and then if you do have problems you can always go back to the original file.  Once the partitions are not mounted by fstab you should be able to use the disk mounter on them as you please; it will ask for your password but should work OK to both mount and unmount them.

Sorry if that is a bit long-winded, but I thought it might help you see what fstab is and does, and how to change that if you don't want things to happen as the system thinks they should.

As for partitions, the only essential partitions are really /, (root) and swap as I use, without a separate /home partition or anything else.  A separate home can be useful when you upgrade versions of linux but you would not be wise to use the same home partition for ubuntu and mandriva as there could well be conflict between configurations of software packages.  You could use the same swapthough, as could I have done.  Nevertheless you still have a lot of partitions, several ntfs ones which may well have been put there by the computer manufacturer and probably have a recovery partition included.

Good luck with any changes you make.  Hope they all work out for you.

---

### Post by sandysandy on 2007-11-06
Thanks for such a nice and detailed explanation.
i have put the # in front of couple of partitions that are at startup.
will log in/out and check.

regards

---

### Post by Arthur Archnix on 2007-11-06
This is confusing. Why would his swap partitions be mounted on his desktop? That doesn't make sense. Ok... I see...naming confusion... almost none of his mount points correspond to the actual dev name. Not really a problem, just confusing.

If you don't want these things on your desktop just change their mount point from /media to /mnt

For instance, say you didn't want that sdb8 on your desktop, and it had picture files in it. Create a folder for it in /mnt, then change the mountpoint in your fstab.
```
sudo mkdir /mnt/pictures
gksudo gedit /etc/fstab
```
Look for the line that says /media/sdb8 (is actually sdb7) and change "/media/sdb8" to "/mnt/pictures"

---

### Post by sandysandy on 2007-11-06
> **Arthur Archnix said:**
> This is confusing. Why would his swap partitions be mounted on his desktop? That doesn't make sense. Ok... I see...naming confusion... almost none of his mount points correspond to the actual dev name. Not really a problem, just confusing.

If you don't want these things on your desktop just change their mount point from /media to /mnt

For instance, say you didn't want that sdb8 on your desktop, and it had picture files in it. Create a folder for it in /mnt, then change the mountpoint in your fstab.
```
sudo mkdir /mnt/pictures
gksudo gedit /etc/fstab
```
Look for the line that says /media/sdb8 (is actually sdb7) and change "/media/sdb8" to "/mnt/pictures"

thanx Arthur Archnix & ajgreeny

both the methods worked

regards

---

### Post by ardchoille42 on 2007-11-06
> **poudin said:**
> to log in root u must 1st set a root password

sudo passwd and establish password...then su - will switch to root user

u should check /etc/fstab is correct...then u should be able mount -av

mount -av should attempt to remount any items from /etc/fstab not currently mouted.

cheers abd good luck

Please don't teach people how to log in as root.. it's neither supported nor recommended. I have been using Ubuntu since 2004 and I have never seen an instance when I needed to log in as root - and I have installed Ubuntu on over 200 machines that I also support. Logging is as root also makes your system less secure because you can't brute force a locked root account.

---

### Post by aysiu on 2007-11-06
I don't think it's really a security issue. It's just unnecessary and inefficient to log in as root. Almost everything can be done from the *admin* user with the use of *sudo*, *gksudo*, or *kdesu*.

---

### Post by kellemes on 2007-11-06
> **ardchoille42 said:**
> Please don't teach people how to log in as root.. it's neither supported nor recommended.

It may not be recommended.. this doesn't mean *we* may not answer peoples questions.
It's not recommended to install compiz/beryl, e17 or other beta-packages either, but people will and should be able to, this is the freedom they have.

---

### Post by aysiu on 2007-11-06
> **kellemes said:**
> It may not be recommended.. this doesn't mean *we* may not answer peoples questions.
It's not recommended to install compiz/beryl, e17 or other beta-packages either, but people will and should be able to, this is the freedom they have.
But there aren't comparable ways to get the same effects as Compiz/Beryl or E17 without using those or other beta software.

There *are*, however, comparable and, in fact, better ways to get the same root-level tasks done without logging in as root.

---

