---
title: "What is this silly NooB doing wrong?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by Chickenfoot on 2006-10-09
Hi,

I'm brand new to linux. Been searchng through the forums, trying to figure it out on my own. But I think it's time to admit, this Noob needs help...

I'm trying to mount a 2nd hd containing XP. It's set as my secondary master.

I've found the thread, [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), courtesy of Aysiu...thanks!!

I've created the mounting point: sudo mkdir /windows

Went and down loaded the Gnome Partition Editor, so I am certain that the info on the XP HD / Partition is corect.

My fdisk - l looks like this:

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38346   308014213+  83  Linux
/dev/hda2           38347       38913     4554427+   5  Extended
/dev/hda5           38347       38913     4554396   82  Linux swap / Solaris

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14945   120045681    7  HPFS/NTFS

My etc/fstab looks like this:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /windows        ntfs    nls=utf8,umask=0222 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Not only can I still not mount my XP drive, but now I can't even detect it in Places / Computer!

So, where did I go wrong? Any help would be greatly appreciated!!:confused:

---

### Post by Darrious on 2006-10-09
I have never used fdisk before.
I usually get to root then go to cfdisk.

Sorry that I could not be more help.

---

### Post by Jussi Kukkonen on 2006-10-09
Hi, 
Some details about the mounting could be helpful.
> Not only can I still not mount my XP drive, but now I can't even detect it in Places / Computer!
How did you try mounting it? Did you do *sudo mount /windows* in the command line? What is the output?

---

### Post by bulldog on 2006-10-09
I think you are wrong on this one:I've created the mounting point: sudo mkdir /windows

To create a mount point```
sudo mkdir /mnt/windows
```
To mount```
sudo mount -t ntfs /dev/??? /mnt/windows
```

---

### Post by tiago on 2006-10-09
Hi Chickenfoot,
I think that you have to install the package that alows you to read from ntfs...
```
sudo apt-get install ntfs8
```

---

### Post by Jussi Kukkonen on 2006-10-09
Bulldog, if he wants to use /windows as a mount point that's up to him...

tiago, as far as I know ntfs reading is possible on a default install. Do correct me if you know better.

---

### Post by Chickenfoot on 2006-10-09
Thank you, Jesse and Bulldog, for responding with alacrity!

Bulldog,

Took your info. This is my output:

sudo mount -t ntfs /dev/??? /mnt/windows

chickenfoot@spanky:~$ sudo mkdir /mnt/windows
Password:
chickenfoot@spanky:~$ sudo mount -t ntfs /dev/hdc1 /mnt/windows
mount: /dev/hdc1 already mounted or /mnt/windows busy
mount: according to mtab, /dev/hdc1 is mounted on /windows

I guess i need to unmount windows, but I'm not sure of the syntax...any suggestions?

---

### Post by Chickenfoot on 2006-10-09
Tiago,

Thank you for responding:

Here is my output:

chickenfoot@spanky:~$ sudo apt-get install ntfs8
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs8

---

### Post by bulldog on 2006-10-09
> **Chickenfoot said:**
> Thank you, Jesse and Bulldog, for responding with alacrity!

Bulldog,

Took your info. This is my output:

sudo mount -t ntfs /dev/??? /mnt/windows

chickenfoot@spanky:~$ sudo mkdir /mnt/windows
Password:
chickenfoot@spanky:~$ sudo mount -t ntfs /dev/hdc1 /mnt/windows
mount: /dev/hdc1 already mounted or /mnt/windows busy
mount: according to mtab, /dev/hdc1 is mounted on /windows

I guess i need to unmount windows, but I'm not sure of the syntax...any suggestions?

```
sudo umount /dev/hdc1
```

@Jussi Kukkonen,

I know he can mount where he want to,**but** there is a nice /mnt folder to keep things simple.

---

### Post by timnoc1456 on 2006-10-09
> **tiago said:**
> Hi Chickenfoot,
I think that you have to install the package that alows you to read from ntfs...
```
sudo apt-get install ntfs8
```

taigo,
        Which Ubuntu release are you using? Ubuntu 6.06 recognises and mounts ntfs volumes in default. It I think does'nt need any extra packages. The earlier release, might have needed that.

---

### Post by Chickenfoot on 2006-10-09
Hey Jussi,

thanks for the info. Here is the output:

chickenfoot@spanky:~$ sudo mount /windows
mount: /dev/hdc1 already mounted or /windows busy
mount: according to mtab, /dev/hdc1 is already mounted on /windows
chickenfoot@spanky:~$ sudo umount /windows
chickenfoot@spanky:~$ sudo mkdir /mnt/windows
mkdir: cannot create directory `/mnt/windows': File exists
chickenfoot@spanky:~$ sudo mount -t ntfs /dev/hdc1 /mnt/windows
chickenfoot@spanky:~$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38346   308014213+  83  Linux
/dev/hda2           38347       38913     4554427+   5  Extended
/dev/hda5           38347       38913     4554396   82  Linux swap / Solaris

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14945   120045681    7  HPFS/NTFS


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /windows        ntfs    nls=utf8,umask=0222 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

So now what. I still don't see the C drive in Computer. Will reboot and see if that helps.

---

### Post by bulldog on 2006-10-09
To see them in /media you have to alter fstab.
My entries for the ntfs drives lookes like```
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```in fstab.

---

### Post by tiago on 2006-10-09
> **timnoc1456 said:**
> taigo,
        Which Ubuntu release are you using? Ubuntu 6.06 recognises and mounts ntfs volumes in default. It I think does'nt need any extra packages. The earlier release, might have needed that.

Yes, I think you are right. I only needed to mount an ntsf partition in the previous version and I had to install a package...

---

### Post by Ptero-4 on 2006-10-09
Chickenfoot. To make your Windoze partition appear in the Ubuntu's Computer icon you need to mount your Windoze partition in a directory inside /media (f.e: /media/Windoze instead of /Windoze or /mnt/Windoze), then the ubuntu GUI will pick it up.

---

### Post by Chickenfoot on 2006-10-09
Bulldog,

I'm so frakin' lost....And frustrated Do you mean like this?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1	/media/hdc1	ntfs	nls=utf8,umask=0222 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Please help..I feel that despite my Noob ignorance, you guys have ALMOST walked me through it!

---

### Post by Chickenfoot on 2006-10-09
Hey Ptero,

you wrote:

Chickenfoot. To make your Windoze partition appear in the Ubuntu's Computer icon you need to mount your Windoze partition in a directory inside /media (f.e: /media/Windoze instead of /Windoze or /mnt/Windoze), then the ubuntu GUI will pick it up.

Do you mean instead of

chickenfoot@spanky:~$ sudo mkdir /mnt/windows

I should make:

sudo mkdir /media/windows  ?

Is that what you mean? Sorry for the dubm *** newbie questions...

---

### Post by timnoc1456 on 2006-10-09
Go here, this may help [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Chickenfoot on 2006-10-09
Hey Timnoc,

Thanks for the response. That is one of the pages I have been reading.  sadly, I still haven't got it to work. I'm probably 90% there. So close, yet so far...

---

### Post by Chickenfoot on 2006-10-09
Hey Bulldog...or anybody else,

I've tried the following:

Chickenfoot. To make your Windoze partition appear in the Ubuntu's Computer icon you need to mount your Windoze partition in a directory inside /media (f.e: /media/Windoze instead of /Windoze or /mnt/Windoze), then the ubuntu GUI will pick it up.

I've also tried:

To see them in /media you have to alter fstab.
My entries for the ntfs drives lookes like
Code:

/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1 /dev/hda5 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1 /dev/hda6 /media/hda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

in fstab.

My Ftab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1	/media/ windows	ntfs	nls=utf8,umask=0222 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Is this right?

---

### Post by timnoc1456 on 2006-10-09
Hi,
   Chickenfoot, sometime newbee or whatever it is see's a prob from same dimension. I am not clear what version of Ubuntu you are using? 6 months back just for a hack I installed Ubuntu breezee, and it did not stay a week in my PC. The most probable reason might have been, I could'nt mount automaticall my window's partition, where all amy works & data's resided. I did manage to get around with it using the link, I provided.
   But now I am really seriously trying linux and ubuntu that 'am forgetting my windows itself. The point is, mounting of HDD's should'nt be a problem even for a beginner like us, with all those helps around. In Ubuntu 6.06, their is no worry. It's just default or authomatic. However if you are using the earlier version of Ubuntu Breezee then you should, if I remember work through the terminal and issue commands:  all command should be listed in the link I had provided. Then you had to edit the fstab to mount it authomatically at the login. All through this the adminbsitrative privelage of sudo command was necessary.

If it helps you ( mine is working fine) I'll give my fstab configuration
I have 3 HDD. 2 SATA drive (80GB each) and 1 PATA drive(80GB). my windows XP pro resides on one of Sata Drive which was "sda1", I disabled it to be mounted authomatically by editing the /etc/fstab file , so it won't show on the configuration file  I'll show you.

MY FSTAB CONFIGURATION
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd1       /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdd5       /media/hdd5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdd6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Sometime when you can compare the obivious, you might able to make out. If I knew out of hand, I could have told you.

Good luck! if we are not in the same boat! ahh... ahh at least we may be in the same raft!

---

### Post by CatKiller on 2006-10-09
> **Chickenfoot said:**
> 
/dev/hdc1    **/media/windows**    ntfs    nls=utf8,umask=0222 0 0

Is this right?

No space.

Otherwise, it looks hunky-dory.```
sudo mount -a
``` to re-mount the entries in fstab.

---

### Post by Chickenfoot on 2006-10-09
TimNoc,

Thanks you for the response. Good to know I'm not the only one struggling with this. I'd like to think that I am fairly IT literate, on PC's. But, I gotta tell you, struggling with what appears to be rather simple instructions, and not being able to figure it out and make it work is quite humbling.

Thanks for all of your help. I'll just keep trying. Perhaps, it'll click at some point...

---

### Post by CatKiller on 2006-10-09
> **Chickenfoot said:**
> Perhaps, it'll click at some point...

I don't know if [this post]("http://www.ubuntuforums.org/showpost.php?p=1557220&postcount=10") will help you get it settled in your mind. It's one of mine, so it's not that great, but it does explain some of the concepts involved.

---

### Post by Chickenfoot on 2006-10-09
Thanks Catkiller,

chickenfoot@spanky:~$ sudo mount -a
Password:
mount: /dev/hdc1 already mounted or /media/windows busy
mount: according to mtab, /dev/hdc1 is mounted on /windows
chickenfoot@spanky:~$

Am I experiencing some sort of conflict? HAve I  saved (or mounted) to two seperate folders? Windows vs Media/Windows?

Is the Fstab like a Boot.ini? Only a file? KIll the file and nothing works? Or can I go in an delete/move the file, if I've saved to more than one location?

Linux...it's learning a whole new language....

---

### Post by Chickenfoot on 2006-10-09
Catkiller,

Great link. I am reading it now.

Very Helpful.

---

### Post by CatKiller on 2006-10-09
> **Chickenfoot said:**
> Am I experiencing some sort of conflict? HAve I  saved (or mounted) to two seperate folders? Windows vs Media/Windows?

That seems likely. You can use the **umount** command listed above to unmount the /Windows before the **mount** command I gave you.

> Is the Fstab like a Boot.ini? Only a file? KIll the file and nothing works? Or can I go in an delete/move the file, if I've saved to more than one location?

fstab is like a boot.ini in that it **is** only a text file, but problems with it can be... problematical. Mount points don't matter too much - they are just directories that are used as placeholders. And I discovered the other day that you **can** legitimately have the same filesystem mounted in two different places at the same time, but the command to do so is slightly different.

> Linux...it's learning a whole new language....

I think of it more as learning to speak, rather than just pointing and grunting. But then, I do seem to be having a bad night.

---

