---
title: "Need help running Windows partition in VMWare Player"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Wargazm on 2007-03-11
Hello all.  Today was my first day with Ubuntu, and I must say that I am already completely in love with it.  There were a few hiccups along the way (had trouble with video drivers, audio drivers, etc), but nothing that I couldn't handle, especially with the help of these wonderful forums.

My question is about the VMWare Player.  I tried following the instructions in this thread:
[http://www.ubuntuforums.org/showthread.php?t=380699&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=380699&highlight=vmware)

Thing is, that my partitioning is set up differently than the example given.  Here is my output:

```
Disk /dev/sda: 312499999s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End         Size        Type     File system  Flags
 1      63s        40965749s   40965687s   primary  ext3              
 2      40965750s  45062324s   4096575s    primary  linux-swap        
 3      45062325s  75778604s   30716280s   primary  ntfs         boot 
 4      75778605s  312496379s  236717775s  primary  ext3              

```

```
Disk /dev/sda: 19452cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: 19452,255,63.  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start    End       Size      Type     File system  Flags
 1      0cyl     2549cyl   2549cyl   primary  ext3              
 2      2550cyl  2804cyl   255cyl    primary  linux-swap        
 3      2805cyl  4716cyl   1912cyl   primary  ntfs         boot 
 4      4717cyl  19451cyl  14735cyl  primary  ext3              

```

As you can see, I have my windows partition in the third partition, not the first. What values do I need to put into my windows.vmdk, then?  Also, does it matter that my disk is labeled /dev/sda instead of dev/hda?  what's the difference between those tow anyway?

Any help/answers is much appreciated. Thanks very much.

---

### Post by scxtt on 2007-03-11
/dev/sd* is a non-ide disk (SATA or USB mostly, probably scsi too) - /dev/hd* are (e)ide disks ...

---

### Post by Wargazm on 2007-03-11
I figured that's what it was.  Thanks for the reply.

---

### Post by scxtt on 2007-03-11
as for what values you should use, hmm - just a guess here:

312499999 - 45062325 - 63 = <use that value>

RW <value above> FLAT "/dev/sda" 63

for the other underlined values - 63, 255, and 19452 should work - and go in places similar to how the poster's example had (just a different value for cylinders) ...

---

### Post by Wargazm on 2007-03-11
When I try to run windows.vmx, it give me the following error:

> Cannot open the disk '/home/wargazm/vmware/windows.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.

The tutorial says I need to add myself to the "disk" group by doing this:

```
sudo adduser USERNAME* disk
```

I did that, and it still doesn't work.  is there any way I can verify I am actually in that group?  I looked in "Users and Groups", and I didn't even see "disk" as a group in there.  Is that the problem?

any help is appreciated.

---

### Post by Wargazm on 2007-03-11
ok, I was able to get past that error by typing "sudo vmplayer"...but then I hit another error:

> Could not connect to floppy "/dev/fd0". Please correct your configuration and then re-attempt to connect the virtual floppy drive.

---

### Post by Wargazm on 2007-03-11
ok, that one was kind of obvious....I have no floppy drive.  duh. haha

the virtual machine start up, and I get to my windows install just fine...but my mouse doesn't work.  doh.  :)

---

### Post by scxtt on 2007-03-11
what kind of mouse do you have?  USB or PS2?

you should be able to do a "cat /etc/group" to see who is in the "disk" group ...

---

### Post by Wargazm on 2007-03-11
It's USB.  It's a Logitech Cordless Desktop, so there's a single wireless receiver that plugs into a USB port, it is the receiver for both the keyboard and the mouse.

---

### Post by scxtt on 2007-03-11
i'm guessing the following lines in your *.vmx need to be changed:

_from_:
usb.present = "FALSE"
usb.generic.autoconnect = "FALSE"

_to_:
usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"

---

### Post by Wargazm on 2007-03-12
That worked.  thanks very much!

---

### Post by Wargazm on 2007-03-15
ok, my next problem.  I have two hard disks.  The 1st is a 160 gigst, he 2nd is 300 gigs.  The 2nd disk is where all of my media is, it's partitioned into 5 equal partitions, all formatted as NTFS.  The 2nd disk has the Ubuntu and Windows installations in two roughly equal partitions, and there's an extra partition on there as ext3.  

The problem right now is that when I start up the Virtual Machine and get XP loaded, I can't see the 300 gig disk.  I don't really know what to mess with to make it work, so any help is appreciated.

---

### Post by scxtt on 2007-03-15
make samba shares (via ubuntu) for any drive you want your XP to see and connect to it using "map network drive" in XP ...

---

### Post by Wargazm on 2007-03-15
Will that affect the Windows install in any way?  I can see the drives just like normal when I boot into Windows, so I don't want to mess that up.

as an aside, thanks a lot scxtt for your help.  You seem to be the only one looking at my thread!  :)

---

### Post by scxtt on 2007-03-15
no, it shouldn't -- at worst, it'll tell you it can't connect to them when you boot it natively (if you select "connect at logon") ... when you run it as a VM, the VM profile doesn't have access to the hardware in the same way it does natively ... as far as i can remember, you're supposed to create a 2nd "hardware profile" for when you run an already existing native install as a VM ...

funny i've been able to help so far, i've never done this myself (don't have windows installed on my HDD, just run XP and 2k3 as VMs) ... i did read an article about it one tho :p

---

