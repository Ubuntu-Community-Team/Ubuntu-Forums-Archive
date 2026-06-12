---
title: "Adding a 2nd hard drive"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by wink on 2007-06-18
Hi,

I have added a 2nd hd to my system (it is mounted in a mobile dock) which I plan to use for system backups, the idea being that this drive will only be inserted when a backup is made, otherwise it will be removed and safely stored away from the tower. 

This drive was originally formatted in NTFS, it still is and at the moment mounts as "read-only". 

Question 1: How do I go about making it "write-able"? or, better yet, 
Question 2: How can I format it for Linux, assuming that would remove the write restriction by default? 

As you can tell I am a newbie with more questions to come yet and would greatly appreciate any help. 
Thanks in advance.

wink

---

### Post by nymphaeles on 2007-06-18
Install ntfs-3g for read/write NTFS partition.
Install gparted to manipulate HD, partitions, formating, etc.

---

### Post by wink on 2007-06-18
Thanks for your reply. I installed ntfs-3g and gparted (actually gparted was already installed as I found out).

However the problem of not being able to write to the 2nd hd persists and - in gparted - the option to format it is grayed out. 

Any idea of what I am missing?

---

### Post by southernman on 2007-06-18
I've got a linky link for you if you like. It'll be easier than me trying to muddle my way through explaining it to you... *grin*

[http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml]("http://www.linux.com/howtos/Hard-Disk-Upgrade/format.shtml")
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

The links show you how to setup and format partitions using fdisk, which you'll have to use sudo with. Once you start fdisk in a terminal just type "m" and enter for a list of commands to use. It may seem daunting to do this from a terminal, it really isn't though if I can finger it out.

The second link is probably best to use since it's on ubuntu's help pages and has a slight variation for formatting the partition once it's created.

HTH's in some way.

[edited] I use to suggest using gparted, but it really isn't all that. It's ok, don't get me wrong but... it still leaves a little to be desired yet. Perhaps if you use a gparted livecd, and not the version that installs in ubuntu would net better - less flawed results.

---

### Post by wink on 2007-06-20
Thanks to the links provided by **southernman** I was able to reformat the 2nd drive as an extended partition in ext3 format, but - even though it shows up under *places* - am still unable to copy anything to it. 

Obviously I missed something, the question is what and where? TIA for any help.

wink

---

### Post by southernman on 2007-06-20
Try changing permissions like this:
> 
sudo chown -R username:username /dev/hdb1
sudo chown -R 755 /dev/hdb1

If you created a mount point for this drive/partition, replace the /dev/hdb1 with the name of the mount point.

PS - the code above assumes you only have one hdd in your system, which would be /dev/hda (or sda as the case may be)

---

### Post by gloxer54 on 2007-06-20

Wink, this is my first post, but perhaps you should be asking about this site: 
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
I stumbled onto it within the forums here.  I have NOT tried it, but ask around.  There are people here that really know their stuff.  Good luck.
        gloxer54

---

### Post by wink on 2007-06-20
**gloxer54**: Thanks, but the drive is now an ext3 drive, no longer ntfs.

**southernman**: Will follow your suggestion. Thank you and wish me good luck. 

Darn, I hate to be such a newbie (read *pest*). :(

---

### Post by southernman on 2007-06-20
> **wink said:**
> **gloxer54**: Thanks, but the drive is now an ext3 drive, no longer ntfs.

**southernman**: Will follow your suggestion. Thank you and wish me good luck. 

Darn, I hate to be such a newbie (read *pest*). :(

Your welcome Wink. As for your comment on the newbie-ness... Don't sweat it at all. That's what the community is for. Well for support and idle chit chat down in the community cafe... ;)

To see myself typing more - I didn't go the full route of how you could create a mount point, add the mount point in your /etc/fstab so that it would auto mount simply for the fact that you said this would be a hdd you used for backups alone. When not backing up, or restoring your backups, having the entry in etc/fstab *may* cause a problem when booting your system... if the drive isn't plugged in. You can always mount the drive from (Places > Computer) by right clicking on the drive and select "mount." You will be asked for a password, just enter it and shes all mounted and ready to go.

Now that I think of it, each time you plug in the drive and turn on your system, you may have to chown the drive each time. I can't say for certain though. (read noob too!) ;)

Good luck, glad to have sorta helped out.

---

### Post by wink on 2007-06-20
> Your welcome Wink. As for your comment on the newbie-ness... Don't sweat it at all. That's what the community is for. Well for support and idle chit chat down in the community cafe..

Agreed, the support here is definitely outstanding, otherwise I'd still be out in la-la land.

> To see myself typing more - I didn't go the full route of how you could create a mount point, add the mount point in your /etc/fstab so that it would auto mount simply for the fact that you said this would be a hdd you used for backups alone. When not backing up, or restoring your backups, having the entry in etc/fstab may cause a problem when booting your system... if the drive isn't plugged in. You can always mount the drive from (Places > Computer) by right clicking on the drive and select "mount." You will be asked for a password, just enter it and shes all mounted and ready to go.

I am aware of the possibility of encountering a problem at boot time. If this should happen I'll just use an external USB drive instead. Actually, I am already using it with my laptop and it's big enough to hold several backups from both machines.

 Make that several *dozen*. ;)

---

