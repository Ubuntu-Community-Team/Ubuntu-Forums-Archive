---
title: "Removing Window Forever"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-03-24
I have been dual booting xubuntu and windows xp for several days now.  Ever since I got my wireless internet to work, I haven't even booted up my windows partition.  I have 40 G hard drive,  I have a ubuntu partition, a windows partition, and a 7 G recovery partition that was installed my Compaq (I am using a Compaq Presario Desktop with an AMD64 processor.  How should I go about removing windows and telling xubuntu 7.10 that it is okay to write on that space.  Should I delete the recovery partition?  I think that has to with windows recovery only.  I also want grub to recognize that windows is no longer there.  I am not 100% sure I want to do it yet, but it'll be good to have the instructions just in case. :)

---

### Post by phr0ze on 2008-03-24
An easy way, if you have not configured much, is to reinstall and tell it to use the entire disk. 

Something else you can do is just format the windows partition and set that as your home folder. This is normally recommended anyways. Then edit the boot menu to remove windows.

Thanks,
John

---

### Post by hikujk123 on 2008-03-24
I have configured a lot.  Also, I know I have to do everything you said...I just don't know how to do it. :(

---

### Post by phr0ze on 2008-03-24
Well, I'm not an expert but these are the general steps. Someone with more knowledge will need to provide the actual commands.

Backup your home folder.
Delete all the data in your home folder.
unmount the windows drive.
Use gpart to format the drive and set it's mount point to /home
Mount the new drive and restore the files.
Update the boot menu.

Here is a link to an easy article you should be able to use to do most of this.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by hikujk123 on 2008-03-24
> **phr0ze said:**
> Someone with more knowledge will need to provide the actual commands.

Please do.

---

### Post by forestpixie on 2008-03-24
I'd get parted magic - there is a partition editor on there and some other useful stuff, or you can use the livecd partition editor.

Delete the win partitions and create a new partition formatted ext3. This will be called sda* - you need the number.

This for the new /home seems to work.. [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Read through that bu you need to work from the part that's labelled - Using the new partition

---

### Post by hikujk123 on 2008-03-24
Can I just use GParted from ubuntu's liveCD?  Also, should I delete compaq's recovery partition?  Will Grub update automatically?  Which partition is it on?

---

### Post by update_manager on 2008-03-24
> **hikujk123 said:**
> I have configured a lot.  Also, I know I have to do everything you said...I just don't know how to do it. :(

One option would be to backup your system to a USB key, then reinstall using the whole disk.
[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by hikujk123 on 2008-03-24
I would prefer not to reinstall because I originally started with ubuntu and then using the terminal switched to xubuntu.  Also, my wireless did not work out of the box.  It took great effort to get it to work.

---

### Post by alexforcefive on 2008-03-24
> **hikujk123 said:**
> Can I just use GParted from ubuntu's liveCD?  Also, should I delete compaq's recovery partition?  Will Grub update automatically?  Which partition is it on?

This was my first thought, but use with caution unless someone wants to confirm it: Boot into the livecd, run gParted, delete the two unwanted partitions, resize your ubuntu partition to fill the hard drive. I have an inkling that you might not be allowed to increase the size of a partition without reformatting, but if that's the case you could just consolidate your two unwanted partitions and use it as a separate hard drive.

I'm not sure if grub will update automatically, but if it doesn't just boot back into ubuntu, hit alt+F2 and type 
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by hikujk123 on 2008-03-25
```
gksudo gedit /boot/grub/menu.lst
```

I use xubuntu so I don't have gedit.  Also, can someone please confirm this.  It sounds like the best plan.

---

### Post by forestpixie on 2008-03-25
substitute mousepad for gedit - or install gedit if you like

You could just merge the 2 win partitions into 1 ext3 and use it for storage - if you're doing that you will need to make an entry in fstab and make a directory to mount it - but that's easy enough. But /home will still then be within you're normal / and reinstalling will overwrite it - make sure you have backups before you do anything like that. 

Grub woin't update itself about win going - but it's just a matter of deleting the win entries.

There is nothing to stop you backing up any configuration files you've changed an copying them onto a clean install I did it with xorg.conf

---

### Post by Bölvaður on 2008-03-25
You should wait until Ubuntu 8.04.
Backup your datafiles you want to save.
Burn and install the new Ubuntu version, and in the process you should chose to install to the entire disk.


That is probably the easy (lazy) way, but the other's are also correct, but only if you need the extra space right now and you are unable to wait for a month for it.

But you might learn a lot about partition manipulation if you go into that =)

---

### Post by alexforcefive on 2008-03-25
> **forestpixie said:**
> But /home will still then be within you're normal / and reinstalling will overwrite it - make sure you have backups before you do anything like that.

I haven't tried this, but couldn't you copy your home directory to the new partition, then go to...
```
system > administration > users and groups > your username > properties > advanced
```

and point it to wherever you moved it to?

---

### Post by forestpixie on 2008-03-25
I think it's a bit more involved than that - I use the psychocat tutorial when I tried it out. But wouldn't know if you're method would work or not :)

---

### Post by mcdan on 2008-03-25
you can use gparted from the live CD, and turn your windows partition and recovery partition into a fat32 or ext3 partition.  you wouldn't have to touch your ubuntu partition

---

