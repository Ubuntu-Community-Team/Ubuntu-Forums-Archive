---
title: "external drive questions"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by willough on 2007-05-22
We have Ubuntu Feisty 7.04 server running (but also the desktop version which I switch in and out of).  I have purchased two identical external hard drives for archiving backups and am having issues giving them write access.  For reference the drives are Seagate FreeAgent 320 GB drives and they are immediately recognized by Ubuntu but are read-only out of the box.  From what I have read this is because they are currently formatted for ntfs.  I have read several different approaches on these threads for making these drives writable and I would like an opinion of how to proceed before I go further.  The drive comes formatted with ntfs and by default has this device name and info on the volumes tab of properties:

/dev/sdb1/ on /media/FreeAgent Drive type ntfs ( ro, nosuid, nodev, umask=222, utf8 )

The three approaches I've read in the forums for making these drives writable are:

1. Unmount, change the mount point, reformat using either "vfat" or preferably "ext3".  Than, edit the fstab file and lastly reboot. See:
[http://ubuntuforums.org/showthread.php?t=418002](http://ubuntuforums.org/showthread.php?t=418002)

2. Change the volume permissions by editing fstab
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)
or
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

3. Follow the directions in the tutorial for integrating NTFS with read/write support using the ntfs-3g.  Use the drive with ntfs as it came.  Do not reformat.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

As you will note there appear to be multiple ways to achieve what should be a relatively simple thing:  configuring an external drive for backup.  Perhaps there are other ways too.  I would appreciate some input so I can finish the configuration and move on to setting up the backup routine.  In case it has any meaning we also use Samba and Webmin.  Thanks in advance.

---

### Post by techno-mole on 2007-05-22
have you tried installing ntfs-config using synaptic ? i use an external for storage and ntfs-config worked a treat, and its alot easier to instll with fiesty than it was in edgy.

---

### Post by Inxsible on 2007-05-22
If you are gonna keep the drives in NTFS format then there are two things you need to do.
 
1) Install ntfs-3g and enable write support on external Drives. To do this, first install ntfs-3g
```

sudo aptitude install ntfs-3g

```
 
Then Go to Applications --> System Tools --> NTFS Configuration Tool
Select Write support for internal drives and write support for external drives.
 
2) After doing that, you need to assume ownership of the drive / folder that you want to write to like so 
```

sudo chown -R <your-username> <drive path>

```
 
So for you it will be : assuming your username is willough
```

sudo chown -R willough /dev/sdb1

```

---

### Post by willough on 2007-05-22
I'm trying the suggestion of Inxsible first but hit a snag.  The install went without a problem but in the next step

> Go to Applications --> System Tools --> NTFS Configuration Tool

Well, I don't see anything that fits that description.  I've checked all the Ubuntu menus and do not see a branch for System Tools or NTFS Configuration Tool.   I finally found under System --> Preferences --> Main Menu the ability to make System Tools visible on the Applications Menu.  But I unable to locate the NTFS Configuration Tool that you reference.

On a separate note would it cause a conflict if I install ntfs-config as suggested by techno-mole in addition to ntfs-3g?  Or is it redundant?  I have not done it but am curious.  Thanks.

---

### Post by Inxsible on 2007-05-22
> **willough said:**
> I'm trying the suggestion of Inxsible first but hit a snag.  The install went without a problem but in the next step



Well, I don't see anything that fits that description.  I've checked all the Ubuntu menus and do not see a branch for System Tools or NTFS Configuration Tool.   I finally found under System --> Preferences --> Main Menu the ability to make System Tools visible on the Applications Menu.  But I unable to locate the NTFS Configuration Tool that you reference.

On a separate note would it cause a conflict if I install ntfs-config as suggested by techno-mole in addition to ntfs-3g?  Or is it redundant?  I have not done it but am curious.  Thanks.

I think they are both the same, but i could be wrong !

Try this :
Go to Applications --> Add/Remove

In that search for "ntfs" without the quotes. It should show up something called NTFS Configuration Tool. Select that for install and then follow my earlier post.

---

### Post by willough on 2007-05-22
Yes, I needed to install ntfs-config from the Synaptic package manager and now the configuration tool is on the System Tools menu.  So, I assume both ntfs-config and ntfs-3g are required.  I have enabled write support for external drives ( the only option I could choose ).  I also did chmod as directed and I believe I can write to the disk now though it still shows root as the owner and group.  I will try to run a backup routine tomorrow and report further.  Thanks.

---

### Post by Inxsible on 2007-05-22
> **willough said:**
> Yes, I needed to install ntfs-config from the Synaptic package manager and now the configuration tool is on the System Tools menu.  So, I assume both ntfs-config and ntfs-3g are required.  I have enabled write support for external drives ( the only option I could choose ).  I also did chmod as directed and I believe I can write to the disk now though it still shows root as the owner and group.  I will try to run a backup routine tomorrow and report further.  Thanks.

To change the owner simply use chown like i told  you in my previous post

---

### Post by willough on 2007-05-23
I did follow the chmod instructions and it went smoothly.  The owner and group changed for /dev/sdb1 as expected.  However, the drive and all its contents are still owned by root when I look at the properties --> permissions of /media/FreeAgent Drive and I am unable to change that.  Is that how it's supposed to be?

---

