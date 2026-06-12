---
title: "Another newbie with a question &lt;grin&gt;"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by TracyLBaker on 2007-05-20
OK, This is what I've done.

1) Successfully installed ubuntu onto a computer with a 120Gb and a 200Gb hard drive (both IDE).  I installed the OS onto the 120Gb drive as a "full disk" installation.

2) At this time, I was able to go in and completely remove an old Windows XP installation from the 200Gb drive.

3) After I saw that this would work, I shut down and installed a 37Gb SCSI hard drive and adapter.

4) I reinstalled ubuntu to the 37Gb hard drive, again as a full "full disk" installation.  Everything went well, and it works fine.

5)  What I want to do now, however, is remove the ubuntu installation from the 120Gb IDE hard drive.  However, it won't let me,  It says I'm not the owner and that I don't have permissions.  (I did, incidentally, use the same username and password for both installations.).

So, how do I get rid of the ubuntu installation from the 120Gb IDE hard drive so I can use it as I wish?

I know I could just take the drive out and repartition it using one of my other computers, but I'd really like to learn how to it from within ubuntu.  

Thanks in advance.

---

### Post by Nekiruhs on 2007-05-20
Assuming your connected to the internet
```
sudo apt-get install gparted
```Make sure you disable auto-mount, auto-browse, and the others on the first page of System > Preferences >Removable Media
Run it, select hdx where x is the number of your drive, unmount it,  and format it to what ever.
You can then re-enable the auto-mount options. (Just turned them off because sometimes, when I do this, Nautilus tries to mount them before their finished formatting and gParted gets angry)

---

### Post by zvacet on 2007-05-20
Download Gparted live CD and delete partition with it.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by laidback on 2007-05-20
Gparted is also on the Ubuntu Live CD

---

### Post by TracyLBaker on 2007-05-20
OK, gparted did work.  I was able to remove the old partitions on both IDE drives (the 200Gb had a FAT32 that I didn't want), and recreate them so that they're ext3.

I found that I had to unmount them, remove the old partition, create the new partition, format it and then reboot.  (I know that this is odd-ish, but I didn't see any way in gparted to (re)mount the drives -- but that could be due to a case of temporary, selective, blindness), so I turned back on the options in the the "Removable Drives and Media" section and rebooted.

Anyhoo -- the drives do show up now, but I cannot write anything to them.  The only thing they both show as having is a "lost+found" folder (?).  

When I check the permissions, it says that the "owner is" 'root', and they can "create and delete files".   The "Group" is 'root' and they can "access files".  "Others" is blank, and they can only "access files".

What am I doing wrong (or, where did I go wrong), and how do I fix it so I can use these two drives as normal, regular, storage places?

Thanks again!

---

### Post by Happy_Man on 2007-05-20
```
gksudo nautilus
```

Will run file manager as root, so you can go in and change the permissions.

---

### Post by TracyLBaker on 2007-05-20
I ran the command line in the terminal (Applications | Accessories | Terminal) and up popped the File Browser for the root account.  (Title bar says, "root - File Browser".)

The however portion of this is that neither of the 2 IDE drives show up here.  All I have is Desktop and File System.  As a result, I cannot change the permissions on the 2 IDE drives.

------------------------------------------------------

HOWEVER -- I think I made a boo-boo in describing my last set of symptoms.  The information that I previously gave were from the Properties for the "disk" and "disk-1" icons that were on my desktop.  

When I go into Places | Computer and then select the Properties | Permissions for one of the two drives (labeled as "111.8 GB Volume: disk" and "186.3 GB Volume: disk-1"), it says that the Owner and Group are both "unknown" and all of the "Access" fields are marked as 'Read-only'.  I can drop down the "Access" drop-box and choose "Read and Write", but then I'm told that the permissions could not be changed.

What should I be doing now?

As always, this is greatly appreciated!

---

### Post by TracyLBaker on 2007-05-20
Sorry for the double post.  This also happens when I type in: gksudo nautilus

```

(nautilus:5802): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

```

And, when the root- File Browser opens, the IDE drives do not show up.  I can see them when I go to Places | Computer.

---

### Post by TracyLBaker on 2007-05-20
[bumpage] bump [/bumpage]

---

### Post by confused57 on 2007-05-20
Excellent information here for mounting different filesystem types:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

and here:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

I don't think you'll be able to mount an entire hard drive...only individual partitions.

Added:  If you unsure what to do after reading through the links, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

describe which partitions you want mounted automatically when booting Ubuntu & someone should be able to guide you...mounting in /media should place an icon for the partition on your desktop.

---

