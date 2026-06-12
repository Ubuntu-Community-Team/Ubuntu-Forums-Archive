---
title: "help with fdisk on new HD"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-13
I know how to install a new HD in Windows but I can't do it in Linux.
I've got 2 windows drives on my system that I don't want touched (sda &  hda.)
My third new HD is for Linux only (Feisty & eventually Ubuntu Studio). 
Booting from a live CD & running fdisk  can someone give me step by step instructions how to 
partition & format this new drive for ext3 (/dev/hdb). 

I've tried Gparted & it won't work.
I've been messing with this for two days & am getting a little frustrated.

---

### Post by SpaceTeddy on 2008-03-13
first off, i must warn you. the commands i am about to use here can be quite desastrous if used wrongly or without understand what they acctually do. So make sure you understand what is happening before you use any of these on anything !

that said, i will first go into explaining briefly how partitons and additional drives are handled in ubuntu. in Windows, each partiton get it's own drive letter (starting with C:, then D: and so on) - in linux, there is only one root partiton, wich is called / this partition will hold your entire file-structure. any addition drive or partition is hooked into a sub-directory of /. as an example, here is my partiton table (i've remove the non imporant lines

```
$ mount
**/dev/sda3 on / type ext3 (rw,errors=remount-ro)**
*/dev/sda2 on /home type ext3 (rw)*
*/dev/sda1 on /media/sda1 type fuseblk*

```

as you can see, /dev/sda3 is my / - my main partiton that holds the entire structure - while the partitons /dev/sd2 is mounted in the directory /home - so anything that is saved somewhere under /home will NOT acctually go onto /dev/sda3, but rather on /dev/sda2
furthermode - /dev/sda1 is a windows drive, mounted in the directory /media/sda1

make sure you understand this, as it is important on using the new drive later on. essentially, there are no drive letters in linux - just directory that belong to different drives.

now, to setup the new drive - first off, you will need to partition the drive. before you do that, check if there are already some existing partition on the drive already. this can be done via 
```
sudo fdisk  -l **device**
```
where you replace the **device** by the acctual drive name - for example /dev/hdb in your case.

this should list some information about the drive itself and it's partitions. mine looks like this:
```
~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 92.3 GB, 92399714304 bytes
255 heads, 63 sectors/track, 11233 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x214fc249

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9371    54789682+  83  Linux
/dev/sda3            9372       11113    13992615   83  Linux
/dev/sda4           11114       11233      963900   82  Linux swap / Solaris

```

if you already have a partiton on there that says "linux" all you need to do is create the filesystem, and then mount it. if there is nothing on it, use
```
sudo fdisk **device**
```
to acctiually partiton it. How exactly that works i cannot say, since it has been a very long time i did this... if i doubt, use the full drive for one primary partition - that should suffice for the start.

after you have create the partiton (and verified it is acctually there with the previous commands) comes the most delicate part. if you do this wrong, you can destroy any data on your computer. so make sure you use the right device for this.
Now it is time to create the filesystem. this is (for a linux drive) done via the command 
mkfs.ext3 - so as an example you would use
```
mkfs.ext3 **partition**
```
where you replace **partition** with the newly create partition on the new drive - if you only have one primary partiton on the new drive it will most likely be /dev/hdb1 (**CHECK THIS TO BE RIGHT !**)

after being done with this, it is time to mount the new drive somewhere. essentially you can put it anywhere you want, but if you put it in a directory that already contains stuff, these files/directories will be overlapped by the drive and not be visible anymore (they are not gone !)
i would suggest you create a new directiry in /media where you can mount the drive
do this with 
```
sudo mkdir /media/**partition**
```
where you replace the **partition** again with the appropriate value (i.e. hdb1)
then you need to mount the drive - this can be done one time via
> sudo mount **device** **mountpoint**
where **device** would be /dev/hdb1 or something like this, and the **mountpoint** would be your newly created directory - i.e. /media/hdb1

check via ```
mount
``` if your drive got mounted !
check via ```
df -h
``` if the space on the drive looks right !

that should make your disk usable - but there is no auto-mounting (i.e. you wil need to mount it manually every time you booted). if you want, i can tell you how to automount it aswell...

---

### Post by garyed on 2008-03-13
Thanks for the in-depth help.
My main concern is what to do after I execute the - sudo fdisk /dev/hdb - command.
That is what scares me the most & also once I do that will it mess up my windows partition table
where my system will be unbootable until I install Ubuntu & Grub? Since it won't install now I'm a little nervous about everything since this is my DAW computer with all my music programs & data.

---

### Post by SpaceTeddy on 2008-03-13
the drive (hdb) is freshly bought and there is nothing on it at the moment.
Under that assumption. anything you do with the command
> fdisk /dev/hdb
(**NOTE:**i left the sudo out on purpose - if you want to use that command, add the sudo infront. this command can only be run as superuser)
will purely stay on that drive and no other will be touched or altered. Also, if you purely stay on that new drive (which, since it is new has not been integrated into your system) will not mess anything up in your current system. Windows will detect it as new hardware and then ignore it. Ubuntu will do nothing to it until you tell it to. 

Again, under the assumption that this is a NEW drive, there is nothing to be afraid of. the drive is not used for anything, so nothing can break.

as for what you do in fdisk yourself... 
you should first create a new partiton table (if that is not created yet) with the button o.
then create a new partition with n
choose a primary partition with p
choose 1 as the you want the first primary (so it will be hdb1)
just press enter on the size - then it will default to maximum size (twice i think)
after you are back at the normal fdisk prompt, press p to display the new partiton table. it should look like this now (this is hdd drive, yours should be hdb - sizes can also differ :) )
> Command (m for help): p

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321   83  Linux


all you need to do now is press w apply the changed (anything up to now was purely setup - nothing has been changed yet). after that, you can proceed with my earlier ramblings. AGAIN: it is only that simple if hdb is a new drive !!!

is that more what you were looking for ?

---

### Post by garyed on 2008-03-14
> **SpaceTeddy said:**
> the drive (hdb) is freshly bought and there is nothing on it at the moment.
Under that assumption. anything you do with the command
...........
......
 
is that more what you were looking for ?

Thanks a lot,
Thats exactly what I was looking for. I'm copying this post & saving it for furue reference.
I ended up downloading the Gusty live CD & it recognized the new drive & allowed me to partition & format so I ended up doing it without fdisk. If it was any other computer I would have probably gone ahead with fdisk & taken my chances but  I felt it was too risky because I never used it before in Linux. I've used it plenty of times in MSDOS & always felt comfortable. 
The Feisty live CD would lock up when it got to the partition phase of the installation.
I had a little trouble with Grub getting the drive numbers mixed up but finally got everything working. 
Thanks again, very good info.

---

