---
title: "using my NTFS partition? NOOOB"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by SoundFlame on 2008-03-06
first of all Hi all! this is my first post here.. hope there is anyone who can help.

**The Problem:** I can't see and use my NTFS drive (yeah i know that ubuntu can't do that by deffult)
i've installed ntfs-configuration tool and partition editor... 
i can see the drive from partition editor... but i can't use it!

i don't want to loose my files from the drive.. the idea is to get them copied so i can use them with ubuntu. i know there is an option where i can format the drive and use it but this don't works for me.

**Some info**
I'm completly new to ubuntu... i was using Ms XP till yesterday.. so yeah i'm noob

i have 1 hdd with 3 partitions 
1=10gb swap file (i know it's too big.. i want to resize it to maybe 4-5 gb but that later..)
2=24gb fot the ubuntu

and 

3=40gb this is the NTFS partition with my files collection of the music i made, my working projrcts atc....

i'm using ubuntu studio 7.10 installed for audio, image and video editing...

i really need to rescue this partition from formating... 


i've found this : 

> Installing NTFS 3G Driver

    *

      Enable the universe repository and install the ntfs-config package. See Installing Software. ->**done**
    *

      Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool->** ok done too**
    *

      The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply. -> **nope it only asks me if i want to enable writing for internal and external drive - cheked... **
    *

      On the next screen Enable write support for internal device will be selected by default. Click OK. -> **can't reach that point**

Your NTFS drive will be now be available in the mount point you selected.  -> **no it's not... :( **



pls pls help.... !
if u need more info just ask.. 

:confused::confused:

---

### Post by hyper_ch on 2008-03-06
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by SoundFlame on 2008-03-06
thanks for the quic response... but i see info for For Ubuntu 6.06 LTS (a.k.a. Dapper Drake),For Ubuntu 6.10 (a.k.a. Edgy Eft),For Ubuntu 7.04 (Feisty Fawn):

i have 7.10 is this a problem?

> soundflame@ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-config is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
soundflame@ubuntu:~$ gksu ntfs-connfig
soundflame@ubuntu:~$ 


nothing happens.... 
am i doing something wrong?

---

### Post by SloYerRoll on 2008-03-06
> **hyper_ch said:**
> [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

That's pretty cool stuff hyper. Thanks for that nugget!

@Sound:
After you rescue  your files w/ hypers link. Just use gparted to format your partition to taste. 
If you don't have gparted yet:
[FONT="Courier New"]sudo apt-get install gparted[/FONT]

Best,

---

### Post by sisco311 on 2008-03-06
open a terminal:

Applications -> Accessories -> Terminal

and post the output from:

```
mount
```

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by SloYerRoll on 2008-03-06
> **SoundFlame said:**
> thanks for the quic response... but i see info for For Ubuntu 6.06 LTS (a.k.a. Dapper Drake),For Ubuntu 6.10 (a.k.a. Edgy Eft),For Ubuntu 7.04 (Feisty Fawn):

i have 7.10 is this a problem?



nothing happens.... 
am i doing something wrong?WHat happens when you go into the NTFS partition? I'm running Gutsy and can see my NTFS drives and partitions.

---

### Post by SoundFlame on 2008-03-06
**mount**
> soundflame@ubuntu:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
soundflame@ubuntu:~$ 


**sudo fdisk -l**
> soundflame@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43d143d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   82  Linux swap / Solaris
/dev/sda2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/sda5   *        1276        4462    25599546   83  Linux
/dev/sda6            4463        9728    42299113+   7  HPFS/NTFS
soundflame@ubuntu:~$ 


**cat /etc/fstab**
> soundflame@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cbc6aaf9-4489-45cd-8236-be66fcee872a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=6E3CA90E3CA8D1FF /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda1 :
UUID=c1710f9c-f778-4c10-b889-372c9ba29e0d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
soundflame@ubuntu:~$ 


---

### Post by Archmage on 2008-03-06
Please ignore this post. Othere where MUCH faster. ;)

---

### Post by SoundFlame on 2008-03-06
@SloYerRoll  yeah i can see them too but i can't access them :(

---

### Post by SoundFlame on 2008-03-06
@ Archmage 
hi i've posted this just before your post... maybe u arr right...

---

### Post by sisco311 on 2008-03-06
can you mount the partition manually?

```
sudo mount /dev/sda6 /media/sda6 -t ntfs -o  defaults,umask=007,gid=46
```

---

### Post by SoundFlame on 2008-03-06
soundflame@ubuntu:~$ sudo mount /dev/sda6 /media/sda6 -t defults,umask=007,gid=46
mount: unknown filesystem type 'gid=46'

---

### Post by SoundFlame on 2008-03-06
sorry i forgot -o last time...
this time the output is 

> soundflame@ubuntu:~$ sudo mount /dev/sda6 /media/sda6/ -t ntfs -o degults,umask=007,gid=46
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda6': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda6 /media/sda6/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda6 /media/sda6/ ntfs-3g defaults,force 0 0
soundflame@ubuntu:~$ 




help.... i don't have windows should i type mount -t ntfs-3g /dev/sda6 /media/sda6/ -o force

---

### Post by SoundFlame on 2008-03-06
sisco311 u there? 
what u think?

did i mention i'm using UbuntuStudio ? 

c'mon anyone ---  some ideas?

---

### Post by sisco311 on 2008-03-06
I don't know how secure is the force option. You can try it on **your own risk**. 
[FONT=monospace]
```
[/FONT]sudo mount /dev/sda6 /media/sda6 -t ntfs -o  force,defaults,umask=007,gid=46
```

---

### Post by SoundFlame on 2008-03-06
done that
> soundflame@ubuntu:~$ sudo mount /dev/sda6 /media/sda6 -t ntfs -o  force,defaults,umask=007,gid=46
[sudo] password for soundflame:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
soundflame@ubuntu:~$ 


now what?

lol i can see the content of the partition!!!!!!!!!!!!!!!!!!!!!!1

nice 10x a bunch... is it fine to copy files from and to it? 
and to use it as standart.. u know like writing some files to there?

---

### Post by sisco311 on 2008-03-06
Open your file browser and navigate to the /media/sda6 directory.

---

### Post by SoundFlame on 2008-03-06
yeah i've open it already 10x alot!!!!!!!

now i can copy files from it and format it after that... or i can use it as stnadart hdd.. even it's on ntfs?

---

### Post by sisco311 on 2008-03-06
> **SoundFlame said:**
> done that


now what?

lol i can see the content of the partition!!!!!!!!!!!!!!!!!!!!!!1

nice 10x a bunch... is it fine to copy files from and to it? 
and to use it as standart.. u know like writing some files to there?

yes, you can use the ntfs filesystem.

---

### Post by sisco311 on 2008-03-06
if you want to format the partition to ext3 and mount it at boot time:

0.) format the partition with gparted to ext3

1.) create a mount point:
```
sudo mkdir /media/my_disk
```2.) get the uuid of your partition:
```
sudo vol_id /dev/sda6
```3.) edit your fstab:
```
sudo gedit /etc/fstab
```add this lines:

> 
[B]#/dev/sda6
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/my_disk ext3    defaults        0       2[/B]and delete this one:
> UUID=6E3CA90E3CA8D1FF /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 1replace **xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** with the uuid you get from 2.)

4.) mount the partitions:
```
sudo mount -a
```5.) to get write permission chown the mount point:
```
sudo chown -R **your_username:your_grup** /media/my_disk
```by default **your_group** is your user name:

```
sudo chown -R **your_username:your_username** /media/my_disk
```done

---

