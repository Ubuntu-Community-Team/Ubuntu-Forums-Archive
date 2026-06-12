---
title: "mounting problem.. (Solved)"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Misfitmatt87 on 2006-11-05
Hey all, 

   This is my problem, hopefully you can help. After reading a bunch of theses posts i finally mounted my drive. Heres my problem after mounting it i can sudo into the drive no problem, but I want to make an icon on my desktop that lets me access the drive, i have all my music/movies on there and would like to access them in linux. i did a df -h for you all.```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdd1             9.0G  2.1G  6.6G  24% /
varrun               1014M   84K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   18M  997M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1              75G   75G  531M 100% /mnt/hda
```

---

### Post by taurus on 2006-11-05
You need to mount your /dev/sdb1 to /media/hda instead of /mnt/hda...

So, edit your /etc/fstab and change the mount point.

```
sudo nano -Bw /etc/fstab
```
Then reboot...

---

### Post by Misfitmatt87 on 2006-11-05
ok so i did what you said it shows up in the media folder, but its says i dont have premission nessesary to explorer the folder. that is using the explorer, so i checked out the properties of it and it says unreadable. its ntfs format could that be the problem?

---

### Post by aysiu on 2006-11-05
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by taurus on 2006-11-05
Can I have a look at your /etc/fstab?  Probably need to add "umask=0222" in there...

```
more /etc/fstab
```

---

### Post by Misfitmatt87 on 2006-11-05
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=c6ac9b0f-66f5-4224-9fba-04f0866cb76f /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hdd5
UUID=b6fd7d7f-0b2e-43f3-957c-b4f962cc7e02 none            swap    sw            
  0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by taurus on 2006-11-05
How did you mount your /dev/sdb1 anyway because it's not in your /etc/fstab?  I guess you mount it by hand, right!!! 

Check out the link that aysiu provided and if you still can't understand it, I will show you how then.

---

### Post by Misfitmatt87 on 2006-11-05
ok goin through this tutorial i come on edit thie fstab, and my drive isnt listed in there at all, i guess cause it sata. so should i add the line in like this? ```
/dev/sdb1 /windows ntfs nls=utf8,umask=0222 0 0

```

---

### Post by taurus on 2006-11-05
And make sure you have /windows if you want to mount to it...

```
sudo mkdir /windows
```

---

### Post by Misfitmatt87 on 2006-11-05
ok so i did that, it mounts it fine now, but when i go into the media folder it is not visible

---

### Post by Misfitmatt87 on 2006-11-05
and i did restart

---

### Post by taurus on 2006-11-05
Actually, it's not in the /media/windows.  It's in /windows.  Do you want to mount it to /media/windows?  If you do, you need to modify your /etc/fstab and make it look like /media/windows instead of /windows in there.  And before you do that, run these two commands to unmount it and create a new mount point for it...

```
sudo umount /windows
sudo mkdir /media/windows
sudo -Bw /etc/fstab
```
Once you have made the changes, mount it again with

```
sudo mount -a
```
Now, it will be in /media/windows...

---

### Post by Misfitmatt87 on 2006-11-05
thanks so much! it works!

---

### Post by taurus on 2006-11-05
> **Misfitmatt87 said:**
> thanks so much! it works!
Good job.  =D>

---

### Post by Kieranties on 2006-11-05
@aysiu:  Absolute legend!

I mounted my sata drive today and was having a few probs with it.  Your guide resolved all of them.  I am humbly thankful!

---

### Post by taurus on 2006-11-05
> **Kieranties said:**
> @aysiu:  Absolute legend!

I mounted my sata drive today and was having a few probs with it.  Your guide resolved all of them.  I am humbly thankful!
Maybe you should buy him a cup of ubuntu!!!  ;)

---

### Post by Misfitmatt87 on 2006-11-05
1 more question say i want to give my self premission to write on the windows drives do you change this ```
/dev/sdb1 /windows ntfs nls=utf8,umask=0222 0 0
``` to ```
/dev/sdb1 /windows ntfs nls=utf8,**umask=0777** 0 0
```

---

### Post by taurus on 2006-11-05
You cannot write to NTFS without major damage unless you use the ntfs-3g!  Even with ntfs-3g, use it as your own risk...

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Misfitmatt87 on 2006-11-05
ok ty again, i think ill avoid ntfs writing

---

