---
title: "Hards Drive Partitions"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Majorflam on 2007-04-18
Hi,

I have just installed Ubuntu and I really like the look and feel of it. 

My system was set up as follows:

One physical hard drive 160 GB. It was partitioned into 4 -:

C: Windows XP Pro installed on this
D: Software backup drive (web downloads etc...)
E: Web design partition, containing all my design work
F: A partition holding all my MP3

When installing Ubuntu, I chose the "Use largest available space" for the partitioning part, as I was confused as to what to do. Ubuntu has loaded fine, and I get Boot options at start up (I can still access my Windows XP setup just like before).

My questions are as follows:

Which partition is Ubuntu installed on? When I boot into Windows, it's as if Ubuntu doesn't exist anywhere. 

How do I access my file system from Ubuntu the way I could from Windows i.e. in Windows I would have right click`ed on My Computer and selected "Explore". How do I explore my partitions using Ubuntu?

The main problems I have from Ubuntu is that I cannot access my partitioned drives to use my stored data in Ubuntu, and I have no idea where Ubuntu has intalled itself (for all I know, there could be insufficient space on the "partition" it installed on, if that's how it installed.

Many thanks in advance.
MF

---

### Post by eholly on 2007-04-18
In a terminal (Applications > Accessories > Terminal) type "df" to find out where your root sys in Linux

Windows will not recognize   Linux file systems, To Proud ????

In Ubuntu, System > Administration > Disks > Partitions you can change the mount points of the Partitions. 
You can get to them in Places

---

### Post by Stickymaddness on 2007-04-18
Linux and windows handle hard drives very differently.

In windows you would have c: d: e: etc, where as in Ubuntu you have "root" or /  and different partitions are "mounted" in different places on the root. eg: allot of people like to make a separate partition for user data, and mount it to /home/

To get your windows partitions working, you'll need to install ntfs-3g and mount your partitions eg:

```


/mnt/windows/
/mnt/backup/
/mnt/webdesign/
/mnt/mp3/


```

Windows cannot see your Ubuntu partitions, because it does not recognize the filesystem that Ubuntu uses, but there are windows applications to recognize windows partitions.

As a starting point I would read up on how the Ubuntu file system works... I would post a link, but I can't remember it....its on a post around here somewhere....

---

### Post by Majorflam on 2007-04-18
> **Stickymaddness said:**
> Linux and windows handle hard drives very differently.

In windows you would have c: d: e: etc, where as in Ubuntu you have "root" or /  and different partitions are "mounted" in different places on the root. eg: allot of people like to make a separate partition for user data, and mount it to /home/

To get your windows partitions working, you'll need to install ntfs-3g and mount your partitions eg:

```


/mnt/windows/
/mnt/backup/
/mnt/webdesign/
/mnt/mp3/


```

Windows cannot see your Ubuntu partitions, because it does not recognize the filesystem that Ubuntu uses, but there are windows applications to recognize windows partitions.

As a starting point I would read up on how the Ubuntu file system works... I would post a link, but I can't remember it....its on a post around here somewhere....

How would I install that software... sorry man, I'm a complete newbie here.

---

### Post by mikewhatever on 2007-04-18
Can you please post the output of (from Application>Accessories>Terminal)
> sudo fdisk -l
It should show your current partitions set up. Also, post the output of 
> sudo cat /etc/fstab
to check what is mounted and where.

---

### Post by Majorflam on 2007-04-18
First output:

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        6374    30716280    7  HPFS/NTFS
/dev/hda3            6375       16824    83939625    f  W95 Ext'd (LBA)
/dev/hda4           16825       19457    21149572+  83  Linux
/dev/hda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/hda6           12749       16708    31808668+   7  HPFS/NTFS
/dev/hda7           16709       16824      931738+  82  Linux swap / Solaris
```

Second output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=d6007e8e-f5f5-44b1-a20b-aac8c0b09f90 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda7
UUID=7f49810c-2958-4b61-8bf0-e814bcba4f42 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Hope that helps.

---

### Post by mikewhatever on 2007-04-18
As you can see, Ubuntu installer has created two partitions: hda4 and hda7. hda4 is the partition where Ubuntu is installed, and hda7 is the swap partition similar to the page file in Windows. None of the other partitions are mounted, so you have no access to them at the moment. Here is how to mount them [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)
If you don't know what mounting or mount points are, check this [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

---

### Post by Majorflam on 2007-04-18
I created a new directory called hardrive1 by issuing the following command:

```
sudo mkdir /hardrive1
```

Now I am trying to mount the partition hda2 onto harddrive1 by typing:

```
mount /dev/hda2 /mnt/harddrive1
```

But, I am recieving an error message:

```
mount: only root can do that
```

Am I doing something wrong?

---

### Post by RRS on 2007-04-18
You need to preceed the command with"sudo", as in;
```
sudo mount /dev/hda2 /mnt/harddrive1
```
You'll be asked for a password, type in the one you created during installation. It won't display, just type it in and hit enter.

The first link in mikewhatever's post has good instructions to set things up so the partitions will be mounted automatically @ boot-up.

If you need to do any editing or additions to your ntfs partitions ntfs3g has proven quite safe and reliable, it's now included in the Feisty repositories and there's some good info in the forums on set-up, etc.

---

### Post by Majorflam on 2007-04-18
OK, I have managed to mount the drive (I think), but when I browse to the hardrive1 folder in the filesystem, it says it is unreadable!

Sorry for being a complete newbie here, but this just isn't straight forward.

---

### Post by al_erola on 2007-04-18
If I read you steps correctly, you created a directory at the root level ie /hardrive1.
In the second step you are trying to mount /dev/hda2 to **/mnt**/hardrive1.

Do you have a directory /mnt/hardrive1 set up or not?  If not, you can't mount there because it doesn't exist.

---

### Post by Majorflam on 2007-04-18
> **al_erola said:**
> If I read you steps correctly, you created a directory at the root level ie /hardrive1.
In the second step you are trying to mount /dev/hda2 to **/mnt**/hardrive1.

Do you have a directory /mnt/hardrive1 set up or not?  If not, you can't mount there because it doesn't exist.

You are correct, I removed the mnt/ directory and typed the proper path, but it still doesn't seem to work.

I was looking at a tutorial to add NTFS3G but it seems so complex.

I am running an AMD64 version of Ubuntu 6.10. Does anyone have a step by step guide on how to have my NTFS partitions mount on startup automatically, and also to be readable and writeable?

If I can't have these NTFS partitions available, would it be easier to format the hard disk and start again with new partitions etc...?

TIA

---

### Post by al_erola on 2007-04-18
If you're trying to mount NTFS partitions, Try using the Automatix2 scripts.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Majorflam on 2007-04-18
> **al_erola said:**
> If you're trying to mount NTFS partitions, Try using the Automatix2 scripts.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Wow, that is an awesome little piece of software. I got it installed, but I don't see anything for mounting drives. What exactly do I do now that I have installed it?

---

### Post by mikewhatever on 2007-04-18
Automatics2 can install software which is not included in Ubuntu repositories for various reasons (mainly closed source or legal). It can not mount partitions for you or install something that would. You have to do it yourself.

---

### Post by Majorflam on 2007-04-18
This is a nightmare. I could easily backup my critical data to DVD, and then completely format my Hard Disk ready for a clean install of Ubuntu. Would it be worthwhile doing this, or would it be easier persevering with getting Ubuntu to "see" my NTFS drives?

By the way, the previous tutorial for mounting drives [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) does not make sense. The text it tells me to edit doesn't even exist on my screen.

I really want to ditch Windows, but I also really need to keep my old photo's and MP3's etc...

---

### Post by mikewhatever on 2007-04-18
You do not need to wipe out the disk. The tutorial I linked to assumes the partitions are mounted elsewhere and remounts them. You'd need to enter that text into fstab file manually. 
If you do feel like doing massive changes, reinstall Ubuntu, but manually point it to hda4 partition and mount all the others. All you'd have to do is type the mount points in the option of 'manually edit partition table', for example
/partition1
/partition2
...
...
swap

---

