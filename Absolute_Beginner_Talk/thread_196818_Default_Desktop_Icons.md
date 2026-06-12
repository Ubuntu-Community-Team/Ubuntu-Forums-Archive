---
title: "Default Desktop Icons"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by nitin_mz on 2006-06-14
(The search terms are too generic to get any meaningful results)

When I log into dapper drake, there are 3 icons on my desktop, each corresponding to the mounted windows partitions. 

I can remove the icons by disabling access to them through administration -> disks (or something like that).. but they reappear on next bootup.

Where do I configure this to:
a) Permanentaly disable access to the main windows partition
b) Hide the icons of the other windows partitions from the desktop

---

### Post by atomicSpatule on 2006-06-14
If you are not affraid of playing around in configuration files, here's how you do it :

Press alt+f2 and write :
```
gksu gedit /etc/fstab
```
Then press the **enter** key.
When prompted, enter your password.
In gedit, find the lines where the type is either *vfat* or *ntfs* and add [COLOR="Red"]noauto[/COLOR] to the options.

Example :
My unmodified fstab :
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda5       /media/hda5     vfat    defaults        0       0**
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

After the changes :
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda5       /media/hda5     vfat    defaults,[COLOR="Red"]noauto[/COLOR]        0       0**
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

[SIZE="3"][COLOR="Red"]Of course, your file WILL be different from mine, so do NOT copy and paste my result, or else bad things are likely to happen.[/COLOR][/SIZE]
 I hope I was clear enough, and I hope that helps. If you need more help, feel free to PM me :)

---

### Post by Sutekh on 2006-06-14
[quote=nitin_mz]
a) Permanentaly disable access to the main windows partition[/quote] First backup your /etc/fstab file, which controls the mounting of your partitions, then edit it using **gedit** (for GNOME users)
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Then you need to suss out the line that corresponds to your main Windows partition and then you can remove the line or 'comment it out', by placing a # sign in front of the line.

[quote=nitin_mz]
b) Hide the icons of the other windows partitions from the desktop[/quote] Whilst editing the configuration file you could change the mount point for these Windows partitions. If they are mounted to the /media folder, for example
```
/dev/hda1    **/media/windows**    ntfs    nls=utf8,umask=0222   0    0
``` Then change this mount point to a folder, which you will need to create, to something outside the /media folder, for example /mnt/windows. You would create the new mount folder using
```
sudo mkdir **/mnt/windows**
```Then the new line in the /etc/fstab would be
```
/dev/hda1    **/mnt/windows**    ntfs    nls=utf8,umask=0222   0    0
``` 
The other option is to open the GNOME Configuration Edtor, from the Applications -> System Tools menu.  

Expand the tabs on the left to find the apps -> nautilus -> desktop section.  There you should uncheck the **voumes_visible** option.

---

### Post by Sean-Michael on 2006-06-21
Sutekh,

Thankyou for your very helpful post!  I used this,

> The other option is to open the GNOME Configuration Edtor, from the Applications -> System Tools menu.

Expand the tabs on the left to find the apps -> nautilus -> desktop section. There you should uncheck the voumes_visible option.

Any they disapeared rather nicely :)

Thanks!

---

