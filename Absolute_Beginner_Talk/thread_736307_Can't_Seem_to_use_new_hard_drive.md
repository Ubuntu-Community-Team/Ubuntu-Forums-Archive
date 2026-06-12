---
title: "Can't Seem to use new hard drive"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by algorithmplus on 2008-03-26
I just bought a 750 gb hard drive to expand my storage from my 80 gb hard drive.  I was able to create and ext3 partition and able to mount it, however, I am unable to write to it.  I have tried changing permissions on the mounted directory and the device, as well as using the command chmod 777 for both the device and the mounted directory.  I just can't seem to make the drive writable except with the command line using sudo.  

Any help is appreciated.

---

### Post by Existentialist on 2008-03-26
Did you add the device to your fstab?  Post the output from:

cat /etc/fstab

If it is being mounted through fstab, you can try this to change permissions of the drive to your user.  Replace user with your user, and drivename with whatever it mounts as.

sudo chown -R user:user /media/drivename

---

### Post by oldb0y on 2008-03-26
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

