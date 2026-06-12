---
title: "USB Hard Drive mounts as &quot;read-only&quot;"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by tygern on 2007-09-17
I have a USB external hard drive with a FAT32 filesystem.  I have been able to read and write to it for the past couple of months, and now all of a sudden it will only mount as read only.  I have tried chown, 755 chmod, running nautilus with gksudo, and trying to change the permissions, but none of this works.  Any time I try to change the permissions, it says that the hard drive is read-only.  What else can I try?

---

### Post by wixo on 2007-09-17
yah i'm havin the same problem with that to...anyone could kinly help us

---

### Post by rybu on 2007-09-17
You probably need to load some driver to write.  I had the same problem with a new USB hard drive, so I ran mkfs and reformatted the drive as an ext2 drive.  Solved my problems.  Probably isn't the answer you wanted. You'll probably find a way to write to the drive without formatting it...

---

### Post by tygern on 2007-09-17
I shouldn't need to load any drivers, since I could read and write to the drive just a few days ago.

---

### Post by ellgor on 2007-09-18
A howto mount/access hard-drives, cd units etc. easily.
	        (for newbies to Linux) 

   

	The following aid is based on using Ubuntu, Dapper, and the Gnome desktop with Nautilus manager.
	
	
	It should still apply to most applications providing that the tool 
DISK MANAGER is available.


Hi,


Step 1
	
	In order for the hard-drive etc. to interact with the computer, it needs its own space or office (in human terms) to operate from, this is what we will do here.

	Click on Places, from the drop down menu click on Home Folder, you should now have your Home Folder open in front of you.
	Right click anywhere on a blank space inside your Home Folder, from the drop down menu click on create folder.
	Right click on the new folder and from the pop-up menu select rename and do so with the name of your choice, now close your Home Folder.  
	

Step 2

	Click on System, from the drop down menu click on Administration,  from the drop down menu select Disks and the application starts up, you will be asked for your password to continue, do so and let the application finish loading.
	
When the application has loaded you should see a list of all attached drives etc. (Storage List) on the left side and a big open space on the right (Storage Properties) with a  Properties tag and a Partitions tag.
	
In the storage list select the drive you want to mount  (this is assuming you can identify it by size etc.) clicking on it will highlight it and some info will appear over in the Storage Properties side, presuming you have the right one, click on the Partitions tag and more options will be made available, namely, Format and Enable.
	
Under the new heading Partition Properties will be the Device: hdc1 or sda2 and so forth (make a physical note of the device name for later use) and right next to this is the format option.
	
Now, unless you want some data off it  don't do the following (go to Once the formatting), if the Status reads as Enable leave it, if it reads as Accessible, disable it, either way the Format option should be highlighted ready for use.
	
Click on the Format panel (I think it's default is the Ext3 type) and off it goes,  during the process you will be asked if you want to continue, go ahead,and unlike Window's, it's done in a few minutes.
	
Once the formatting is done the next thing is the Access Path, which might read at the moment as None, click on the box marked change and a new panel marked as Select New Mount Point Path should appear, and, that file you made earlier should be in the list to choose from, select it.
	
Lastly here, the Status should be changed to Accessible, do so, and for those who are wanting data back, use the browse option and transfer it elsewhere ( if it says you are not allowed, or similar, follow the next part and then try again).

Step 3
	
	Because of the way the Linux system works, Root controls most of what goes on in the computer, now it would be nice if we the user also had a piece of that as well, we can, with this.

	Click on Applications, from the drop down menu click on Accessories, from the drop down menu click on Terminal and let the application start.
	Type in the following:-

	sudo chown &#8220; YourUserName:YourUserName&#8221; don't include the quote marks /home /Your User Name/The name of the file you made

	which is the path to the file you made and should look like this, mine personally, me being Gordon and the file called  hardtwo

	sudo chown gordon:gordon /home/gordon/hardtwo

	I've put the username twice as this will stop Root from interfering as part of group.

	Also this to set the permissions type:-

	sudo chmod 777 /home/YourUserName/the name of the file you made

	If all has gone accordingly there will be no error messages and you can proceed, further use of your system will bring enlightenment as to the whys and wherefores of what was done , for now we want things to work.


Step 4 

	Because what we did previously was temporary we need to make it permanent  i.e. you will want it to auto load and be there at all times, we also need to make a copy of the original file and to do this we do the following.
	In your terminal  type in the following:-
	
	sudo cp /etc/fstab /etc/fstab.backup
	
	Which will copy fstab and be named backup(to differentiate) then type in
 
	sudo gedit  /etc/fstab    (Gedit is the default editor in Gnome) 

	You will see a new panel which lists the current state of drives etc. attached to your comp, use the arrow keys and come down to the bottom of the list ready to start a new line.

	The first part is to enter in the drive name/file system, this is the one from the Disk Manager which should be something like  /dev/hdc1 which if you look at the list is similar to the other entries, use the one I asked you to make a note of.
	
Done that, then leave a space and enter in the Pathname/mount point, which is /home/YourUserName/the file you made.
	Leave a space and enter the filesystem/type   ext3
	Leave a space and enter the options     defaults
	Leave a space and enter these two numbers with a space between 0 2 (don't ask)

	Your finished line should look like this:-

	/dev/hdc1 /home/gordon/hardtwo ext3 defaults 0 2 

	Everything done then close the window and you will be asked if you want to save it, do so and that's about it.

	To check things, open up your home folder and open up the file you made and click on properties (it may need a reboot to sort things out) you should be the Owner and Group with full permissions throughout.
	You should also see if the size matches what you put in and there will be a folder already in there called lost+found, its your folder.

	 Hope this helps, Regards Ellgor.

---

### Post by tygern on 2007-09-20
Thanks for trying, but I have already configured my hard drive and have lots of data on it without sufficient space to back it up.  Re-formatting the drive is not an option for me.  The dirve has been working perfectly as read/write for a couple of months, so it must have been set up correctly.  What could have caused it to suddenly become read only?

---

### Post by tygern on 2007-10-02
bump

---

### Post by philinux on 2007-10-02
Try installing Konqueror from the repo 

you can change permissions much easier with it. gksudo konqueror if you really need it.

---

### Post by alienexplorers on 2007-10-02
Please post here:
> sudo fdisk -l
> cat /etc/fstab

---

### Post by odzk on 2007-10-02
there may be a problem on your usb hard drive, did you tried it on windows, try to check if you can write on windows. if not then the problem is on your hdd

---

### Post by tygern on 2007-10-02
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        3321    26624000   83  Linux
/dev/sda3   *        3321        7034    29825024    7  HPFS/NTFS
/dev/sda4            7035        7296     2104515   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

---

### Post by tygern on 2007-10-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda2
UUID=43b1a553-5cf2-49f9-b860-cd618d00f8d2  /              ext2         defaults,errors=remount-ro          0  1  
# /dev/sda1
UUID=07D4-071B                             /media/sda1    vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/sda3
UUID=D6949E87949E6A2F                      /media/sda3    ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                         0  0  
/dev/sdb1                                  /media/disk    vfat         uid=root,owner,users,user           0  0

---

### Post by spycloud on 2008-06-29
Yep, mine happened after a 6/28 security update. All my files suddenly became owned by root, but sudo couldn't change it back.

---

### Post by mempman on 2008-06-29
> **tygern said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                            0  0  
# /dev/sda2
UUID=43b1a553-5cf2-49f9-b860-cd618d00f8d2  /              ext2         defaults,errors=remount-ro          0  1  
# /dev/sda1
UUID=07D4-071B                             /media/sda1    vfat         defaults,utf8,umask=007,gid=46      0  1  
# /dev/sda3
UUID=D6949E87949E6A2F                      /media/sda3    ntfs         defaults,nls=utf8,umask=007,gid=46  0  1  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                         0  0  
/dev/sdb1                                  /media/disk    vfat         uid=root,owner,users,user           0  0



Have you been able to write to your usb drive as super user?  Try the following....
```

cd /usb-drive
sudo touch file.txt

```

Also, is the drive in question /dev/sdb1...if so, there seems to be a root ownership option active in your /etc/fstab...this will mean that only the root can write to it.

What version of Ubuntu are you running...for fiesty, for example, a user wasn't able to write to ntfs partitions without installing additional drivers.

---

