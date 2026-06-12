---
title: "Mounting HDD in 7.10"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by lhcpr on 2008-01-03
Dear all,

First time post so be kind. Nice to be here.

I have just installed 7.10 and I am having a hard time mounting my USB HDD. It is a 250GB IDE drive in a Welland GreenStar USB 2.0 enclosure. The enclosure is designed to powerdown at intervals to conserve power and drive light.

Basically what I want to happen is when Ubuntu starts, it automatically recognises and mounts the external HDD

Ok, so this is what I have done:

1) Edited /etc/fstab such that it reads ```
/dev/sdc1    /mnt/usbdrive     ntfs     user,auto,rw
```
2) I have created the mount point /mnt/usbdrive

When mounting using "mount" command or using mount panel on desktop, system is unable to mount the device. Can tell you at the moment exactly what this is (away from my machine) but it doesn't like it!!

Bit of info on the HDD enclosure, it has 4 modes: active, idle, standby, powerdown. My feeling is that this is what is giving me issues.

Any ideas guys.

Cheers,

lhcpr

---

### Post by Rocket2DMn on 2008-01-03
The entry should like this:
```
/dev/sdc1 /mnt/usbdrive ntfs-3g defaults,locale=en_US.utf8 0 0
```
Make sure that you made the /mnt/usbdrive folder and that it is owned by root:root.
Also, you will need ntfs-3g with read/write enabled to access a NTFS partition.

---

### Post by lhcpr on 2008-01-03
Hey Rocket,

Thanks for the help. I adjusted my code in fstab as below:

```
/dev/sdc1   /mnt/usbdrive    ntfs-3g defaults,user,auto,rw, utf8    0  0
```

As far as I am aware, this should work. But it seems to be unstable, and I get two things happening depending on the way my system is feeling at the time:

1) When logged into Ubuntu session, I can see the drive but when I use the desktop control panel to mount, I get the following error msg

> Fuse: failed to open /dev/fuse: Permission denied
> Fuse mount point creation failed, unmounting......

Fuse has been given RX permissions for all users and groups. The funny part is that I can mount and access the drive in terminal window using ```
mount -a
``` or ```
mount /dev/sdc1   /mnt/usbdrive
```. However, the drive cannot be seen as mounted in Ubuntu window session.

2) On other occasions though, the drive automatically mounts and is visible in the Ubuntu desktop session when Ubuntu is loaded. After investigating this further, it seems as though the drive is using different variables and settings in mtab. they are as follows:
```
/dev/sdc1   /mnt/usbdrive    fuseblk rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096   0  0
```
The mount point is the same ```
/mnt/usbdrive
``` and yes, it does exist (RWX*3 permissions)!!! I cannot unmount the drive using the desktop mount tool
> Cannot unmount: only root can unmount /dev/sdc1  /mnt/usbdrive although this is not the main issue here. My user account is given root group privileges.

To summarise, it is being unstable and unpredictable. My ultimate goal is for users to be able to log in and have the drive automatically mounted: predictably and issue free. The only variation to what I have written above is that The drive has 3 partitions on it, and they have been assigned the correct dev/mnt points (so this should not be an issue).

From what I can see, there really shouldn't be any issue: fstab looks correct. Mount points exist etc...  I will suggest that maybe it is my power saving enclosue causing these quibbles. It has 4 modes: active, idle, standby, powerdown.

Any thoughts guys?

Cheers,

lhcpr

---

### Post by Rocket2DMn on 2008-01-03
If you use the program called ntfslabel you can name each partition on the hard drive.  If there is no entry in fstab (you can comment out the entry with # sign at the beginning), it should automatically mount the drives at /media/labelname where labelname is what you labeled each partition.  The folders should not already exist in this case.

For your current setup, make sure that the folders in /mnt are owned by root:root.  Disconnect the drive and run
```
sudo chown root:root /mnt/usbdrive
```

In your fstab you shouldn't need those extra arguments next to default - auto and rw are included in default, and the "user" might be messing it up (default is nouser).  NTFS doesn't have permissions that work the same way as ext3, so when you mount you will have access to the files (use "sudo mount -a" instead of just "mount -a" in this case).  I suggest just using the arguments I presented above (they worked for me when I had my external in fstab and they work for my internal ntfs partition).

As far as the power saving feature is concerned, I honestly don't know.  I have heard that it can cause problems like unmounting the drive, but for the limited time I spend with my Seagate FreeAgent drive plugged in, it has yet to disconnect on me and it has some sort of power saving feature as well.

---

### Post by lhcpr on 2008-01-04
Rocket - thanks for the reply,

I can use the label program, but I don't thin the labels are the major issue. They are labelled as they should be already and referred to later correctly.

With regards to "default" and using other options, I will cut them out and just give the default a hit. I think I tried it last night, and I could be worng, but I dont believe it worked either.

With regards to auto-mounting in /media/, yes this does happen, but only every so often and depending on how my computer's temprement is at the time. This is my problem. Please see previous post for the mtab that is generated.

Silly me, will chown /mnt/. BTW could you enlighten me about what ```
root:root
``` means?

Also, I have always used ```
sudo mount -a 
``` and I CAN actualy mount the HDD this way and with my fstab settings, only the drives wont appear on the Ubuntu desktop session (although I can navigate the drive whilst in the terminal). I don't want other users to have to do this though, I would prefer to have it mounted automaticaly AND displayed on the desktop as an icon.

That's all I have for right about now. Sure, if Ubuntu consistently mounted my external HDD automatically, there wouldn't be a problem. For now, trying to sort this out.

Any other thoughts or suggestions? I will see what I can do in the meantime.

Cheers

lhcpr

---

### Post by Rocket2DMn on 2008-01-04
Sure thing, root:root means it is owned by user "root" and group "root", that is why there is UserGroupWorld permissions on files/folders.

I just remembered a little problem I have with my Seagate drive - if it gets unmounted, it won't automount again unless the power has been reset on the drive.

Although not ideal, one option is to make a launcher in your panel that runs "sudo mount -a" then you can create launchers to the folders on your desktop for each directory and just leave them there.  If the drive isn't plugged in, the folders will be empty, but if the drive is mounted, the folders will have the files in them.  This is what I did before I was able to get my other external USB disk to automount (when I still had an fstab entry).

I would have to say the problem is with the power saving features.

---

### Post by lhcpr on 2008-01-08
Hey Rocket,

Thanks for the tips.

I agee 100% that I think the issue here is the power saving function. With regards to your Seagate drive not auto-mounting after being unmounted without power-off, add that to the list of problems too!!!!

Well, thanks for the assistance. I look forward to more involvement and contribution to the community.

Cheers,

lhcpr

---

