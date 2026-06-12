---
title: "Moving Ubuntu to larger hard drive"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by SlappyPappy on 2008-04-05
Anybody got some tips for moving Ubuntu to a larger hard drive?

Mine is on a small 20GB job but I'm really happy with Ubuntu and would like to move it to a larger hard drive.

Got a tutorial or something that can get me to do this step by step without hosing anything?

Thanks a ton for the help fellas.   :)

---

### Post by markharding557 on 2008-04-05
if you have a separate home partition then all your settings can be preserved while you install ubuntu on your new drive i don't know any other way of doing it unfortunatly.

---

### Post by tamoneya on 2008-04-05
the easiest thing i can think of is to just mount your new harddrive to where ever your largest files are.  So assuming that you have a lot video in you user directory /home/username i would recommend that you format the new drive as ext3 and then mount it to /home.  This should then be added to fstab so that it gets mounted automatically at startup.```
/dev/sdb1 /home ext3 defaults 0 0
``` This line should be added into fstab assuming that your new harddrive is /dev/sdb1.

---

### Post by skymera on 2008-04-05
To be honest.

I would do a fresh install on a new drive.
Get back up to speed, Ubuntu dosen't take too long to configure nor install.

I would wait till 8.04 and do a fresh install.

---

### Post by stomakmonkee on 2008-04-05
If you're dead-set on keeping the same install and not just reconfiguring and moving over your home folder, then G4L will do the job, and its pretty straightforward.
[http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml](http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml)

---

### Post by joshrobinson on 2008-04-05
i would recommend keeping ubuntu on the 20gb hard-drive, and mounting your new drive as a storage drive, there you can save your music, videos, important files etc.

20gb should be fine for a linux install, and this way, if you ever somehow break your linux install you can have all of your important stuff on a separate drive, which will be un-touched
you could reinstall ubuntu, mount the drive, and its all there

---

### Post by SlappyPappy on 2008-04-05
Thanks for all the great ideas you guys. I like how you ask one question and you get so many different responses. I've got some time before I figure out how I'd like it all setup. 

Should be fun no matter what I decide to do!

---

### Post by SlappyPappy on 2008-04-07
Yes it can be done, I know, I did it. I used this post:

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

It was actually much easier than I thought and went really quickly. The only problem that I really noticed was a different UUID for the Swap but it was an EZ fix.

I'm now on a faster and bigger hard drive. Ubuntu is much snappier now. So very, very happy.

Take the plunge if you feel inclined. And it's good to know that your original HD can be your back up in case the clone doesn't go well. For me though, no problems that I've seen.

:guitar:

---

### Post by warp99 on 2008-04-07
> **SlappyPappy said:**
> Anybody got some tips for moving Ubuntu to a larger hard drive?

Mine is on a small 20GB job but I'm really happy with Ubuntu and would like to move it to a larger hard drive.

Got a tutorial or something that can get me to do this step by step without hosing anything?

Thanks a ton for the help fellas.   :)

This is simple. Install you new drive right next to your old driver. Download the LiveCD of gparted [here]("http://gparted.sourceforge.net/livecd.php"), boot to the CD. make and resize the partitions on your new drive, then copy the partitions from your old drive to your new. 

Make your new drive the boot drive in your BIOS, reboot and presto. If needed you may need to re-install the GRUB boot manager, but other then this nothing else.

You can also do this with a Ubuntu install disk by installing the new drive, booting to the Ubuntu install disk, mounting the drives then make the partitions, copy the data from one drive to the other, install the GRUB boot manager and then set the new drive to boot in the BIOS. New drive, old data.

More information on installing a new drive is available through the wiki:

[https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28new%29](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28drive%29%7C%28new%29)

Edit:

Yes you need to change the uuid to the new drive partitions in the fstab. Forgot about that one! So before you reboot to your new drive you would do the folllowing:

```
sudo vol_id -u /dev/<device_name_of_new_partition>
```

out comes a uuid, then replace the uuid in the /etc/fstab file on your new drive with the new uuid for your new partition. Repeat as needed for other partitions on the new drive.

---

### Post by hyper_ch on 2008-04-07
you can move your /home to the new harddisk... here's a small howto:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Just skip the partitioning part or your existing harddisk and make one big partition on your new harddisk with ext3...

---

