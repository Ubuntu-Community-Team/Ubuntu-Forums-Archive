---
title: "I cant install grub and dont know why"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
:( i cant install grub
i had a hard drive fail
so made room on the other disk for my windows install 
then installed linux 
linux is there but grub will not over ride the windows boot loader
it just will not do it dont know why very confused

---

### Post by JoshuaRL on 2008-02-18
Try burning off a copy of SuperGrub.  It can fix almost any Grub issue, and it's a Live CD.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
yes i used that it acually was able to install grub but the new install of grub will only let me boot windows even though it list all of the os i have on the computer

---

### Post by bodhi.zazen on 2008-02-18
This link should walk you through the process : 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by JoshuaRL on 2008-02-18
Okay, does it show Linux from the Grub list when you log in?

---

### Post by bodhi.zazen on 2008-02-18
I think I mis-read the question.

If you have GRUB installed into the MBR, but you can not boot Ubuntu, we need to edit a few things.

This is best done from a live CD

You need to edit /boot/grub/menu.lst and /etc/fstab

For menu.lst you need to edit the config portion as well, the stuff at the top. In the config section 

## = comments
# (single hash) = config options.

This link will get you started on the general process :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

I need to see the output of :

```
sudo fdisk -l
```

And /boot/grub/menu.lst to give detailed instructions.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
ya it show the ubuntu install i have 
it dosent work says invalad partion
any who

ight now i am grabing all the stuff of my hd so i can back it up

thinking about wipping drive
then windows
then i am going to reinstall linux

then i am going to screem
then i am going to work on grub

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
well just finished backing up 
going to try to reinstall ubuntu agin thinking about downloading an older virsion then 7.10 
just to see if it fixes it

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
good idea
i do have grub installed now
so i should just edit stuff and it should work
i kindof know what i am doing but will post just to see and make shur but i will probly have it done in no time 
but why couldn't i get grub to install from a live ubuntu cd ... is this a bug

```
sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x065cd7ea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2           27725       30401    21503002+   5  Extended
/dev/hda3            2551       27724   202210155   83  Linux
/dev/hda5           27725       27985     2096451   82  Linux swap / Solaris
/dev/hda6           27986       28768     6289416   83  Linux
/dev/hda7           28769       30401    13117041    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       42439   340891236    c  W95 FAT32 (LBA)
/dev/sda2           42440       60801   147492765   83  Linux
ubuntu@ubuntu:~$ 


```


well for get about that is only storage

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
oh ya /dev/hda6 is the ubuntu install
and /dev/hda3 is my /home partion

---

### Post by bodhi.zazen on 2008-02-18
> **<<joe>> said:**
> oh ya /dev/hda6 is the ubuntu install
and /dev/hda3 is my /home partion

OK, the fix is very easy.

Boot a live CD, mount your root partition at say /media/ubuntu

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda6 /media/ubuntu
```

Now edit fstab and menu.lst to point to the correct partitions (for / and /home)

```
gksu gedit /media/ubuntu/etc/fstab
```

Then

```
gksu gedit /media/ubuntu/boot/grub/menu.lst
```

Make sure the kernel line points to your root partition (/dev/hda6)

Also make sure in the configuration section grub lists the proper root (hd0,5)

---

### Post by bodhi.zazen on 2008-02-18
FYI: We went through a similar process on this thread : 

[http://ubuntuforums.org/showthread.php?t=688834](http://ubuntuforums.org/showthread.php?t=688834)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-02-18
thanks guys

---

### Post by bodhi.zazen on 2008-02-18
Please mark this thread as solved, it saves the time of many volunteers looking to help ...

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

