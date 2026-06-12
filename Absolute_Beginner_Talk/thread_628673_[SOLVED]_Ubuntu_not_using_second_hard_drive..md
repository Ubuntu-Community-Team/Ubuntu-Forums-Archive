---
title: "[SOLVED] Ubuntu not using second hard drive."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by pelicanghost on 2007-12-01
I recently installed a second internal hard drive under the master/slave configuration.  It is 500 GB an I want My Ubuntu on the master (first) drive to use this as storage.  Ubuntu recognizes that it's there: output of sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         702       15996   122857087+   7  HPFS/NTFS
/dev/hda2               1         701     5630751    b  W95 FAT32
/dev/hda4           19645       30401    86405602+   5  Extended
/dev/hda5           30072       30401     2650693+  82  Linux swap / Solaris
/dev/hda6           23167       29783    53150989+  83  Linux
/dev/hda7           29784       30071     2313328+  82  Linux swap / Solaris
/dev/hda8   *       19645       23015    27077494+  83  Linux
/dev/hda9           23016       23166     1212876   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System


When I boot up in Ubuntu, and I look at the disk usage analyzer, it says the I have around 25 GBs total on Ubuntu, and used around 9 GBs.  This is what it read before I put in the second hard drive.

Then I go into Gparted and take a look at /dev/hdb, which is unallocated, but has an msdos disklabel.

I go back to Disk Usage Analyzer, and it says I have a total of 197 GBs, and I used 50 GBs already.  It should be above 500 GBs of total space, and around 9 GBs of used space.

How do I get Ubuntu to use the extra hard disk space?

---

### Post by fenian on 2007-12-01
A few questions...

Did you format the drive using GParted?

If not you should do this first ,down load gparted live cd from[ here]("http://gparted-livecd.tuxfamily.org/") and use it to format the drive,format it to ext or you can use xfs if you want.

If you have already formatted the drive have you added it to you fstab configuration?

---

### Post by RRS on 2007-12-01
> .....Gparted and take a look at /dev/hdb, which is unallocated......
Go back to Gparted and /dev/hdb from the right dropdown menu as you seem to have done before.

Select /dev/hdb by mouse click in the grayed graphical display. Then from the upper "Partition" menu format to ext3 or whichever file system you plan to use.

Then from the same menu "New"
You'll have the choice here to use the entire disc or you can create smaller individual partitions if you want.

This will make the drive useable to you.

---

### Post by pelicanghost on 2007-12-01
I believe I found out why my disk says I have 197 GB of total space:  It's reading **all** of the partitions in my first hard drive.  that goes for why it says I used 50 GBs, because I have 9 in Ubuntu, 4 in Windows recovery, and 39 in Windows.

I have now formatted it to ext3 file system.

---

### Post by pelicanghost on 2007-12-01
I have followed a guide here:
[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)
and I'm now at the point where I have to add a line to fstab, but I can't save it because it is read-only: that might not be the problem, but I think it is.

---

### Post by shad0w_walker on 2007-12-01
I assume this is the section of the guide you are using:

```

There! Now you are temporarily mounted. But…if you want it to be permanent, you need to edit your filesystem tab file. Run the following command in terminal:
$ gedit /etc/fstab

```

Try this instead:

```
gksu gedit /etc/fstab
```

---

### Post by linuxonbute on 2007-12-01
> **pelicanghost said:**
> I have followed a guide here:
[http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)
and I'm now at the point where I have to add a line to fstab, but I can't save it because it is read-only: that might not be the problem, but I think it is.

If you are trying to edit the file you have to be root user to have write permissions.

so from a terminal window do ```


sudo gedit /etc/fstab


```
When asked, for it, give your password.

---

### Post by fenian on 2007-12-01
You now need to edit your fstab so this drive mounts at bootup.
First make a directory to mount the drive to,if you create the mount point in /media it will show up under the places pulldon menu and can also be available through an desktop icon if you wanted that.To make the directory open a terminal and type...

> sudo mkdir /media/nameofdrive

change nameofdive to whatever you want to call your drive.

Next we need to ge the UUID for the drive in the terminal enter...

> ls /dev/disk/by-uuid -lah

you will get some output like this.... 

052b7d71-73d0-4fb4-956f-7f02feb49bf0 -> ../../hdb1

the uuid is the string of numbers (your numbers will be different then the ones above) before -> ../../hdb1.Copy these numbers or write them down you need them later.

Next make sure the drive is not mounted with the command....

> sudo umount /dev/hdb1

Next edit the fstab file,from the terminal enter

> sudo gedit /etc/fstab

a file will open in text editor,add the line...

> # /dev/hdb1
UUID=numbers yousaved /media/nameofdrive   ext3    defaults         0       1 

replace numbersyou saved with the string of numbers you wrote down or copied
replace nameofdrive with whatever you named your drive.

save and exit.Then run the command...

> sudo mount -a

next apply permisions with the commands...

> sudo chown -R user:user /nameofdrive
sudo chmod -R 755 /nameofdrive

replace user with your user name and nameofdrive with what you named the drive.
The drive should now be available in the places menu.

---

### Post by pelicanghost on 2007-12-01
Thank you everyone that responded.  I have finally installed it correctly and I have read/write permission over it.

[SIZE="7"][FONT="Impact"]IT WORKS!!!!!!!!!!!
THANK YOU![/FONT][/SIZE]

---

