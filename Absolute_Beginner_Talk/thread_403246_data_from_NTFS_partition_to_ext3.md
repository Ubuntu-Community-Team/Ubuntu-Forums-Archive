---
title: "data from NTFS partition to ext3?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by fobnicat on 2007-04-06
Although I have been toying with the idea of installing Linux for a while now, I have only just installed Ubuntu today.  After piddling for a while, I have begun to miss the music I have become so accustomed to listening to while at the computer.  I have been told recently by a friend that when using ext3 and NTFS, it is possible to transfer data between the two partitions.  Now that I am in my linux OS I am unable to figure out how.

Do I need a separate program or am I just looking in all the wrong places?  Thanks!

---

### Post by benerivo on 2007-04-06
You can keep your music in  the same partition and just have your music player read it from the 'windows' partition. I think you should install the ntfs-3g package in Ubuntu (from Synaptic). This allows reading / writing to ntfs partitions.

You need to mount the ntfs partition in Ubuntu using the /etc/fstab file - making sure it is mounted using the ntfs-3g file system. To allow write permissions, the format of the entry in /etc/fstab should look something like this...
<the partition> <mount point> <file system> <options> <mounting options>

 see here for an overview...
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

an example of a windows partion in the fstab file would be...
/dev/hda1   /mnt/windows   ntfs-3g   umount=000 0 0

---

### Post by LowRadio on 2007-04-06
You should be able to read your NTFS partition just fine (ubuntu will automount it to /media/....) 
However you can't write to NTFS without installing additional software.

If you wish to simply copy your music from one partition to another just copy/paste it from your NTFS to EXT3 partition.

---

### Post by LowRadio on 2007-04-06
or use benerivo's method which is also a good idea.

(I was writing while benerivo posted his msg, sorry) :)

---

### Post by fobnicat on 2007-04-06
hmmm I don't see my Windows partition in my media folder.... What did I do wrong?

---

### Post by g_monkey on 2007-04-06
have a look [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by fobnicat on 2007-04-06
thanks...  ill let you know how it turns out!

---

### Post by fobnicat on 2007-04-06
must have done somethign wrong again.. as i said I know very little about Linux so most of what has been said is gibberish! hah.. Thanks for the help, but I must have done something wrong again

---

### Post by confused57 on 2007-04-06
Here's how to mount your Window's partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

or here:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by FrostyFlames on 2007-04-06
I am assuming you're running 6.10 Edgy.

The first thing you need to do is find out where the windows hard drive is assigned. Type in the following command in a terminal to list your current hard drive setup. (Note: The Terminal is located under Applications -> Accessories -> Terminal)
```
sudo fdisk -l
```
This should list something that looks like:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       12158    97659103+   7  HPFS/NTFS

/dev/sda2           12159       19157    56219467+  83  Linux

/dev/sda3           19158       19457     2409750    5  Extended

/dev/sda5           19158       19457     2409718+  82  Linux swap / Solaris


```

Notice that my NTFS partition (Windows XP) is set to /dev/sda1. Your output will be different, but similar. You may end up with something other then an sda type. Whatever the case is, write that device name down that corresponds to your NTFS drive that holds your data.

The next step is creating a folder to mount your NTFS drive. This will allow you to view your NTFS drive. Type in the following commands in a terminal to create the folder:
```

cd /media
sudo mkdir windows
sudo mount YourNTFSDrive /media/windows/ -t ntfs -r -o umask=0222
```
Replace the YourNTFSDrive part with what you wrote down from the fdisk output (something like /dev/sda1 or /dev/hda1, or whatever was from the fdisk output). This will mount your NTFS drive to the /media/windows/ folder as *_READ ONLY_*. This is also not a permanent fix. You can make linux automatically mount this drive like this every time you boot from now on. Follow the following guide to do so: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

This covers part of what I already stated, so there is no need to repeat that first step. Remember to replace the guides "/dev/hda1" with what you wrote down from the fdisk output.

From here you can open up the file browser. Navigate to the /media/windows/ folder. When you click on the windows folder you are accessing your C: drive basically. I don't know where you store all your music, but you do. If all is good you can find your music and open it with whatever media player you have installed.

Any questions please ask :popcorn:

---

### Post by fobnicat on 2007-04-06
AWESOME! thanks guys! I can't believe how helpful everyone is on this forum... I finally got it through some strange mix of all the techniques that were mentioned.. Maybe I will remember atleast one of them for the next time I have to do this!

---

