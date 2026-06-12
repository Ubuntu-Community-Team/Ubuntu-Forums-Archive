---
title: "Absolute Beginner Question"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Woggie on 2006-02-10
I just installed last night and cleared out any traces of Windows.  I have 2 issues that need to be fixed.  I have seen some suggestions on inputting codes but I am uncertain where and when to put these codes.

1.  I have a master and a slave drive (hda, Master, hdb, Slave) and the system will recognize the drive and it's total capacity, but will not allow me to access the information on it.  Mostly I have pictures and songs on there, at least that's the most important stuff.

2.  Internet access.  I am on DSL with an action tec modem with wireless capability.  According to my ISP (Qwest) I should be able to set it up to work with the new system but I can't seem to access anything outside of these forums and the Mozilla main page.

Any suggestions would be very helpful.  And remember, I am a mental midget when it comes to this system so explain it like I'm 12.

Thanks

---

### Post by LordBug on 2006-02-10
1.  Since you had Windows, I'm assuming these 2 drives are either FAT or NTFS formatted?  You'll need to use the appropriate mount command in order to access them.  Note that NTFS access in Linux is READ-ONLY.

2.  If you can hit these forums, you're getting out.  If you can't go elsewhere, then I honestly don't know.  Maybe a DNS issue?

---

### Post by Woggie on 2006-02-10
I'm not sure on the formatting, but I think its NTFS.  Is there a way to find out?

On the modem, I can get out, but not to anything with a domain name.  For example, I can get to the IP for my modem by inputting the IP numbers, but I can't go to google.com.

---

### Post by Derek Djons on 2006-02-10
That's very odd. Either you can go online, you can't or you DNS isn't setup (you can only access IP numbers). There's actually nothing in between except perhaps an overconfigured firewall?

---

### Post by Woggie on 2006-02-10
Should the modem be set to DHCP or PPPoA?

---

### Post by Woggie on 2006-02-10
I have the DNS settings in front of me.  What should they be set at?

---

### Post by Woggie on 2006-02-10
Here's my fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


When I try to mount hdb I get a  "can't find /dev/hdb in /etc/fstab or /etc/mtab"

---

### Post by steve.horsley on 2006-02-10
System->Administration->Disks should let you set up the disk access. Ihave no idea about the internet though. If you get these forums, you're getting out.

---

### Post by Woggie on 2006-02-10
When I try to access a web page, other than these forums or an ubuntu site, I get a timed out error.

---

### Post by Woggie on 2006-02-10
When I try to access a web page, other than these forums or an ubuntu site, I get a timed out error.  

And the system/administration/disks suggestion I have tried.  It will not enable the disk.

---

### Post by Mustard on 2006-02-10
Can you copy and paste the output of this command (below) in this thread please?  Enter the command in your terminal, which can be found in your Applications>>Accessories menu.  The password it asks for is your user password.  You won't be able to see the password being typed in, it hides the keypresses.

```
sudo fdisk -l
```

It will show all the partitions on your system and what filesystems they are.

Preferably paste them between these forum codes for neatness. :)

[noparse]```
..your code in  here...
```[/noparse]

-edit-

I'd be tempted to start another thread on the networking issue, perhaps with the title 'Internet can connect to ubuntuforums but not other websites' or something along those lines.  Describing the problem in your thread title is the main goal anyway.  That might draw in people who specifically have some knowledge on networking and the internet.

---

### Post by Woggie on 2006-02-10
```
Disk /dev/hda: 4327 MB, 4327464960 bytes
255 heads, 63 sectors/track, 526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         500     4016218+  83  Linux
/dev/hda2             501         526      208845    5  Extended
/dev/hda5             501         526      208813+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4865    39078081    7  HPFS/NTFS

```

---

### Post by Woggie on 2006-02-10
You can split the topics if you'd like.  It sounds like I'd get more of a response that way.

---

### Post by Mustard on 2006-02-10
I would think that you could mount the /dev/hdb1 **manually** by doing this..

```
sudo mkdir /media/windows
#the above command will create a directory in /media called windows which will the the 'mount point' for the partition.

sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
#the above command should mount the ntfs partition in question on the /media/windows 
```

To **automatically** mount the drive on startup, you would need to edit your /etc/fstab file to include this drive in the list of drives automatically mounted at boot time.

To do this you would do these commands...

```
sudo mkdir /media/windows
#you might have already done this if you have attempted the manual mount instructions above

sudo cp /etc/fstab /etc/fstab_backup
#the above command will make a backup copy of your current /etc/fstab file and call the backup 'fstab_backup'

sudo gedit /etc/fstab
#this command will open up the /etc/fstab file in a gui editor
# then you would append the following line at the end of file 

/dev/hdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0


```

The instructions for doing this in a general sense were sourced from this link if you want to look at where you can find this type of information...

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Woggie on 2006-02-10
YOU ROCK!!!!!!!

Sorry I didn't mean to actually sound like a 12 year old there.

I now have access to my slave.  Thank You!  \\:D/

---

### Post by don cole on 2006-02-10
I can't figure out how to post a new message .

So I am repling to this one.

On the ubuntu istallation disk version 5.04 for Intel x86.

(Will this work on Pentium III?)

in -B.5. Ubuntu Partitioning Programs

under -cfdisk

there is a 'cfdisk manual page' link.

this link says 'page not found' 

Where can I find this link? 

And is this the stock partitioner the comes on the ubuntu installation

disk?

Don Cole
 A Bug is an un-documented feature.
A Feature is a documented Bug.

---

### Post by Woggie on 2006-02-10
I don't know the answer to your question, but to post a new thread look to the right of the screen under "Forum Tools"

---

