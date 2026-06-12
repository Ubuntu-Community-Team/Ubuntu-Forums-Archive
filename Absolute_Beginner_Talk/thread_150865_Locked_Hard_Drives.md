---
title: "Locked Hard Drives"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by morwyn on 2006-03-26
I have a dual-boot system and I am trying to get read access to my NTFS partitions. I have followed the guide at [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs), but I am still unable to access the drives. They are locked and I am not sure how to change the permissions to allow me to access them. It says I do not have access rights to this location. What steps do I need to take to access these partitions?

---

### Post by Sutekh on 2006-03-26
You need to open a **Terminal** window.  It should be found in the **Applications -> Accessories** menu.  Alternatively you can press **Alt**+**F2** on your keyboard and type **gnome-terminal** to open the same.

To start you need to determine the location of your NTFS partitions using
```
sudo fdisk -l
```
Using you user's password when prompted.

You can post the output of this command here if you want to make sure that you are choosing the right device.


Once you know the name of thes NTFS partitions (/dev/hdb1, /dev/sda1, etc), you can edit your **/etc/fstab**.  fstab is a configuration file that contains information regarding your partitions and where they should be mounted.

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Once you have opened the fstab then you need to add the line to mount the shared drive. 

For NTFS partitions you should add a line similar to this one
```
[COLOR="Blue"]/dev/hdb1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]ntfs[/COLOR]   [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hdb1[/COLOR] - is the location of the NTFS partition, obtained from the output of **fdisk**

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the drive will be *mounted*.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/winxp[/COLOR]; its up to you

 - [COLOR="Green"]ntfs[/COLOR] - this specifies the filesystem as ntfs

 - [COLOR="DarkOrchid"]nls=utf8,umask=0222[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  The umask is important as it restricts the access to the drive.  [COLOR="DarkOrchid"]umask=0222[/COLOR] only allows read and execute access to the partition NOT write

---

### Post by morwyn on 2006-03-27
I figured it out... I had to unmount the drives before making changes...

---

