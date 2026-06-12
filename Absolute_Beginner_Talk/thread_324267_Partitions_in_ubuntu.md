---
title: "Partitions in ubuntu"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by fca_neo on 2006-12-23
Hello,
I'm very new to linux (I installed Ubuntu last week).

I have some questions about partitions and the file system in general.

**What I have:**

Hard Drive 1: 20GB, w/ Windows (14 GB) and Ubuntu (4GB) installations, and swap (1GB)
HD 2: 160GB, with movies, music, documents, etc in various ntsf partitions.

At first I was not very sure of wanting to switch to linux, but when I saw how wonderful it is, I was convinced. I installed Ubuntu in one 4GB partition because I was willing to test it. Now I want it as my main OS so I would like to have it spread in many partitions.

Unfortunately I have to keep windows because I mainly need it for OrCad (PSPICE) and SolidWorks. But I will migrate all my linux available apps as soon as I can (matlab, maple, antidote, ...)

**What I want to do:**

As soon as I get the apps I need running in Linux, I'll uninstall the from windows and gain that space for linux. (I think I can do this from the live CD using Gparted, I could also use partition magic, but I would prefer a linux solution)

My media on the HD2 should be sharable between windows and linux (specially the documents partition, with pdfs, cad files and the like). I think there is a windows utility for ext3 compatibility, so I don't think this is an issue, but having some info on this would not hurt.

I aim to a file structure like this:

/                         ===>a partition in HD1(more info on this one would be appreciated)
/home                 ===>another partition, preferably on HD1
/home/Documents ===> a 5GB partition in HD2
/home/Movies       ===> a partition in HD2, big files
/home/Music         ===> a partition in HD2, small to medium files
/home/Some other partitions that I have not decided yet ===> partitions in HD2
hda1 with windows in ts own lonely ntsf partition on HD1

**My Questions:**

What partition format should I use for sharing files? I'll use ext3 for media, but I was thinking about using FAT for documents (generally small files and always <4GB). Is this a good thinking?

How to resize ntsf partitions safely? Gparted or PartitionMagic?

Once I create new ext3 partitions using Gparted, how do I mount them to the right place? Please be very clear on this one since I'm not familiar at all with linux command line. Also the partitions should be mounted by default each time I boot.

Is ext3 a good format? Are there other formats that I should consider?

Do you have any suggestions for the partition structure concerning the linux installation?

Thanks in advance.

Btw, this is a great community. Keep up with the great work Ubuntu guys, it is very very much appreciated. This also goes for all the people out there developing free software.

---

### Post by dbbolton on 2006-12-23
i recommend Gparted. when you ask about mounting them properly, are you referring to boot (as from the grub) or do you just want to access the files after booting ubuntu ?

i just use ext3, as i really don't know what difference it makes.

---

### Post by fca_neo on 2006-12-23
I just want to access the files once ubuntu boots. I do not now of any other way of accessing them. But I'm willing to learn!

---

### Post by Warbo on 2006-12-23
OK, firstly I would not recommend different partitions for your documents, movies, music, etc. as there is one big problem with partitioning a hard drive: If you get the sizes wrong to begin with then it's very hard to adjust them later (eg. you might have no room left in the documents partition for your new PDF file, yet you have 5GB free in the movies partition that you don't need). Also, if you are going to do something like that then I would not bother making /home a different partition to /, as the main reason many people do that is to keep their important files seperate from the system (in case they need to reinstall), but your important files would be on seperate partitions anyway.

I would say having a seperate partition for /home (or possibly /home/yourusername) would probably be the best way forwards, then keep all of your documents, movies, etc. on there.

Ext3 is a good filesystem to use, and I hear that the windows Ext3 driver is pretty usable (I don't know myself as I don't use Windows, and sorry I have no link because Google thinks I am an automated script :( ). The basic rule I follow is this: Ext3 is good for not corrupting stuff, and recovering anything that does corrupt. ReiserFS (as in, Reiser3, not Reiser4) is fast for lots of small files. XFS is fast for massive files. Generally if you don't know what to use, go with ext3.

Setting up partitions to mount at boot is really easy. Run the command "gksudo gedit /etc/fstab" which will open up the text editor with super-user permissions with the 'filesystem table' file. It is pretty straightforward to see how this file works, so just copy  one of the lines already there and fiddle around with it's values to add a new partition to be mounted automatically. The "Device" bit needs the partition device name, which will be in the form "/dev/XdYZ" where X is "h" or "s", Y is "a", "b", "c", etc. for which drive and Z is "1", "2", "3", etc. for which partition. If you don't know what something means in that file then a good rule is to just copy whatever it is for "/". Save it and your partitions should mount automatically at boot, and whenever you run the command "sudo mount -a".

Hope that helps :)

---

### Post by fca_neo on 2006-12-23
I had this partition setup in windows too for years. I know that that there could be some space wasted this ways but i prefer it like that. I know I'll always have 5GB (about twice what I need) for documents no matter how many other files I download to my system. They are also safe in their own partition.

I also use this method because of file fragmentation (it is easier to defrag a 50GB partition than a 160 GB one). But perhaps I don't need this anymore.

I could do one 5GB partition for documents (I'm not giving up that one) and use a big partition for the rest (movies, music, etc). Would hat be a better approach?

Thanks for the advice and the quick response time!

One more thing, can I have more than one swap partition or can I change my swap partition to another disk? Is it a good idea?

Thanks

---

### Post by Warbo on 2006-12-23
You can use more than one swap partition, it depends on how much RAM you have and what you get up to really. Common wisdom says that 1GB+ of RAM makes swap pretty much unneeded anyway. You can turn off swap partitions with the command "sudo swapoff /dev/<device name>" and turn them on with "sudo swapon /dev/<device name>" so yes, you can change your swap setup (make a new one, turn it on, turn off the old one then delete it). Oh, and don't forget to change the swap line in /etc/fstab.

Also, yes fragmentation is not really an issue on filesystems like ext3 (although they do like to check themselves every once in a while, I think it's every 30 mounts, which can take a while, although they would probably all check themselves at the same time if you had them seperate anyway)

At the end of the day only you know what your particular setup needs, so go ahead with whatever partitions you think are appropriate (as long as you have / :) )

---

### Post by fca_neo on 2006-12-23
Sorry, I am still having some troubles mounting the partitions with fstab.

Here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=d5c9b2e5-39b3-4cdf-bc49-48636430dee8 /               ext3    defaults,errors=remount-ro 0       1
#
# /dev/hda1
UUID=9EB04E3DB04E1C61 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb10
UUID=7C84F6F184F6AD30 /media/hdb10    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=7424931B2492E002 /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=D43C290E3C28ECE4 /media/hdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb7
UUID=32D4AA7AD4AA3FC9 /media/hdb7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb8
UUID=6618BFC318BF9093 /media/hdb8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb9
UUID=D688E83A88E81B2F /media/hdb9     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
#
# /dev/hdb11
UUID=6f913c43-acaf-4763-9819-0518f41c0f8c /home/carlos/Documents     ext3    defaults,errors=remount-ro 0       1
#
# /dev/hdb12
UUID=aeba1b64-e687-4740-a1f7-071da7d3abd1 /home/carlos/Media     ext3    defaults,errors=remount-ro 0       1
#
# /dev/hda3
UUID=906bc55c-6f63-4b80-9870-42a91ad09e2f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

The problem is I cannot write to /dev/hdb11 and /dev/hdb12. What parameters should I use for these partitions . I tried rw instead of ro at the end but it doesn't make any difference when I do "sudo mount -a".

Thank you for all your feedback Warbo, I really appreciate it.

---

### Post by Rooy on 2006-12-24
Hi there,
I'm struggling with the same problem as yours (regular user can't write) and found this page <http://www.die.net/doc/linux/man/man8/mount.8.html>. The options you would want to add are:
suid (so that using uid= below works)
uid=*your user id* (get this from System-->Admin-->User and Groups)
I haven't tested this yet (trying to solve the same prob on reiserfs), so you may want somebody to confirm it.
Also, you can add `user' to the options, saving a few keystrokes for ``sudo mount'' everytime you want to test if the options work ;)
FYI, the page above is the same content as this command gives you:
man mount
with all formatting retained.

Anyway, anyone knows how to give users write access on reiser3?

Edit:
i formatted the new reiserfs partition to ext3 and discovered that:
uid doesn't work on ext3
Now I'm stuck too
Sorry for the misinformation

---

### Post by steve.horsley on 2006-12-24
> / ===>a partition in HD1(more info on this one would be appreciated)
/home ===>another partition, preferably on HD1
/home/Documents ===> a 5GB partition in HD2
/home/Movies ===> a partition in HD2, big files
/home/Music ===> a partition in HD2, small to medium files
/home/Some other partitions that I have not decided yet ===> partitions in HD2
/home is normally where users' home directories are placed. You would probably be better off using /home/carlos/Documents, /home/carlos/Movies etc.

On reilserfs and ext2/3, the filesystem stores file ownership individually against each file/directory. Try :
**sudo chown -R carlos:carlos /home/carlos/Documents**

---

### Post by fca_neo on 2006-12-24
Tanks anyways for the info Rooy. I found this guide [http://www.ubuntuforums.org/showthread.php?t=283131&highlight=fstab+howto](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=fstab+howto)

It is pretty complete but I could not solve my problem yet.](*,) 

Steve, I tried the command you gave me but it did not seem to work.
Btw, I change my mind about partitions since ext3 doesn't seem to get fragmented. I'll have one big partition for media and stuff and a 5Gb partitions for my important documents.

I think there should be a graphical tool for this kind of setup. This is pretty basic stuff that everybody should be able to do easily without the need of manually editing fstab and setting permissions.

I had enough of computers for today.

Thank you all for your help and advice and have a very happy Holiday. This community rocks. :)

---

### Post by steve.horsley on 2006-12-24
> Steve, I tried the command you gave me but it did not seem to work.
Btw, I change my mind about partitions since ext3 doesn't seem to get fragmented. I'll have one big partition for media and stuff and a 5Gb partitions for my important documents.

Sorry about that. I don't know what went wrong there.

It sounds like you are going to end up with a single big partition mounted on /home, which is actually fairly standard practice. It's handy because it allows you to reinstall or upgrade the OS without losing user data.

---

### Post by mojoman on 2006-12-25
I have a dual-boot with /home partition that I use for documents, movies, music etc, all neatly organized in folders with appropriate names but I guess you could have different partitions as well. However, I would recommend a /home partion because it's so ... well, simple and stable (and I loooove simple and stable). 

To access it from Windows, I'd use ext3 and install this neat program on Windows. 
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

As for FAT32, it has several liitations and although readable/writable by both Linux and Windows, it does not support file ownership and permissions.

/Mojoman

---

### Post by Rooy on 2006-12-25
> **steve.horsley said:**
> On reilserfs and ext2/3, the filesystem stores file ownership individually against each file/directory. Try :
**sudo chown -R carlos:carlos /home/carlos/Documents**

Thanks Steve, this command is what i need (on reiserfs anyway).
Hope fca_neo can find one for his soon. :D

---

### Post by fca_neo on 2006-12-26
The command worked steve! I just needed to go into the folder properties and enabling read and write. Now, everything is fine. Thank you all for your help and advice. I really appreciate it.

**Summary**

[LIST]
[*]I used Gparted to make the partitions I wanted (ext3 partitions).

[*]Then I got the partition's UUID by using this: ls /dev/disk/by-uuid -alh

[*]Using the UUID I  set up the fstab (sudo gedit /etc/fstab)

[*]I changed the ownership of the mount points using "sudo chown -R [user name]:[Gourp name] /[mount point path]" (tanks to steve)

[*]Finally, I went into the mount point folder properties to enable read and write access.
[/LIST]
Also, I used this guide as a reference ([http://www.ubuntuforums.org/showthre...ht=fstab+howto)](http://www.ubuntuforums.org/showthre...ht=fstab+howto)).

I hope this summary will be useful for future users.

Thank you all again, you really rock guys.:D

---

