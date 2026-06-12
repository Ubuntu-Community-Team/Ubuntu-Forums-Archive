---
title: "Why does my 2nd HD appear as a folder?"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by Vulpus on 2005-09-29
I have just done a clean install of Breezy Badger and it has automatically mounted my windows partition (hda1) and shows it as a hard drive icon on the desktop.  I want to do the same with my second hard drive (hdb1) with all my data on it.  I have manually mounted it (as /mnt/data) but it only appears as a folder.  Why doesnt it appear as a seperate drive (or partition) like hda1?

---

### Post by xristos on 2005-09-29
You can add an new line in your /etc/fstab file to mount the drive when the system boot

---

### Post by Vulpus on 2005-09-29
[QUOTE=xristos]You can add an new line in your /etc/fstab file to mount the drive when the system boot[/QUOTE]

I have done that and it does mount automatically on boot.  The issue is that it appears as a folder, not a drive.  In practice this is not a huge problem but it just doesnt seem correct somehow? :confused:

---

### Post by elygirang on 2005-09-29
I don't think it should be a problem. :) 
 
Linux operating systems as well as Unix normally mount physical devices as folders.
 
Honestly, I have not yet seen a Linux/Unix system that mounts hard disks as a physical drive. I even don't know if it's possible.

---

### Post by GreyFox503 on 2005-09-29
If you just mean make it look like a hard drive icon, you can probably just change that for the desktop icon by right clicking on it...

otherwise, I think the only way to mount your drives is to put them in a folder.  Where else would it appear?  As far as I know, there is no drive D:\ in Unix\Linux systems :)

---

### Post by PsyberOneZero on 2005-09-29
try setting the mount point to the media folder.
```

#cd /media
sudo mkdir data

```
then just edit the /etc/fstab file
```
/dev/hdb1	/media/data	ntfs	nls=utf8,umask=0222	0	0
```
I had similar problems, I assume that ubuntu treats the /media directory differently than the /mnt directory

---

### Post by Vulpus on 2005-09-29
It still appears as a folder.  It doesnt really matter as I have set up a link and changed the icon to a hard drive.  It still seems a bit strange though that a seperate hard drive and/or partition shows up as a folder by default.

---

### Post by Vulpus on 2005-09-30
[QUOTE=PsyberOneZero]try setting the mount point to the media folder.
```

#cd /media
sudo mkdir data

```
then just edit the /etc/fstab file
```
/dev/hdb1	/media/data	ntfs	nls=utf8,umask=0222	0	0
```
I had similar problems, I assume that ubuntu treats the /media directory differently than the /mnt directory[/QUOTE]

I have switched on my PC today and the drive is there on my desktop with an HD icon!  It looks like you were correct about setting the mount point to /media but you have to reboot for it to work.

---

### Post by earobinson on 2005-09-30
wouldent sudo mount -a do the job also?

---

### Post by PsyberOneZero on 2005-09-30
Glad to hear that everthing is working ok.
[QUOTE=earobinson]wouldent sudo mount -a do the job also?[/QUOTE]
thinking back I should have added:
```

#sudo umount /dev/hdb1
#sudo mount -a
```
but I goofed, luckily it worked itself out with the next reboot.

---

### Post by Vulpus on 2005-10-01
I did the sudo mount -a but that didn't seem to have any effect.  It only changed after the reboot.

---

### Post by Vulpus on 2005-10-02
[QUOTE=PsyberOneZero]Glad to hear that everthing is working ok.
thinking back I should have added:
```

#sudo umount /dev/hdb1
#sudo mount -a
```
but I goofed, luckily it worked itself out with the next reboot.[/QUOTE]

I have just gone through this whole process again and everything worked as described, including sudo mount -a.  So i can only assume i did something wrong the first time.

---

