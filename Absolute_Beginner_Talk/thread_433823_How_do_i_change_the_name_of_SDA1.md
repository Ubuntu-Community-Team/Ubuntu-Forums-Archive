---
title: "How do i change the name of SDA1?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-05-05
This name is realy strange it is from my windows partition how can i rename this:confused:

---

### Post by Bachstelze on 2007-05-05
You cannot change the name of the device node itself, but you ca change it's mountpoint...

---

### Post by Ocxic on 2007-05-05
you can't change the name of the drive, however you can change th name of the folder, so you can click on say storage, instead of SDA1 for you drive, 
to change this, open a terminal and post the following commands editing them for your needs.

sudo mkdir /media/your_folder_name_here
sudo nano /etc/fstab  -->this will allow you to edit you config file for your  drives mount points, find the entry for sda1 and change the mount point from sda1 to you new folder.
then cntl+x, then y then enter, then reboot. and you should have your own custom folder with the name you want.

---

### Post by Najand on 2007-05-05
Open a terminal.
Then make a new direcotry called "windows" or whatever you like in /media.
```

sudo mkdir /media/windows

```
Then try to edit your /etc/fstab file 
```

gksu gedit /etc/fstab

```
and change it like:
```

/dev/sda1 [COLOR="Red"]/media/sda1[/COLOR] ====> /dev/sda1 [COLOR="Blue"]/media/windows[/COLOR]

```
Then reboot your computer again.

---

### Post by mech7 on 2007-05-05
:confused: This sounds pretty complicated just to change the name of an icon.

---

### Post by CMNetworx on 2007-05-07
Ok, So I am looking to do the same thing, However my drive is not set to mount from what I can see, If it has nothing specified does it just automatically mount as /media/drivedefaultname?

Here is what my fstab looks like
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=22546a96-634d-5bee-z279-fr75090n8376 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=023a1443-2431-4bc6-8652-879da895b4b2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

I know the device is /dev/hda5, so would I just make a new line? I noticed a few of the lines have the # sign prior to them, does that mean that line is ignored??

Im thinking the new line would be something like this?? Assuming I want to name the hd ExternalHD correct me if im wrong.

```

/dev/hda5        /media/ExternalHD   ext3    defaults,errors=remount-ro 0       1

```

---

### Post by Ocxic on 2007-05-08
yep you got it my friend you may want to take out the "error=remount-ro" option, but i don;t think it would hurt anything, rmember to make that directory ExternalHD inyour /media folder, or it won;t work. you also don't have to mount it in /media it can be anywhere.

---

