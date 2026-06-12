---
title: "swap partition will not automount"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by scottym on 2007-09-18
Just upgraded to Feisty using CD and now my swap partition will not auto mount.
The fdisk output is:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1779    14289786   83  Linux
/dev/sda2            1780        1795      128520   83  Linux
/dev/sda3            1796        2350     4458037+  83  Linux
/dev/sda4            2351        2432      658665   82  Linux swap / Solaris
 
the fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d1856a7b-0d67-4613-bc4c-d9a13f370a21 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=44a09475-9391-41e3-9bff-d801ad74260c /boot           ext3    defaults        0       2
# /dev/sda1
UUID=0229e0b7-a13c-4955-9253-08384e2ee930 /home           ext3    defaults        0       2
# /dev/sda4
UUID=12bcec6d-d477-412d-a490-d9269f45567c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Here is the free output:

             total       used       free     shared    buffers     cached
Mem:        636412     487212     149200          0      13412     231136
-/+ buffers/cache:     242664     393748
Swap:            0          0          0


Can anyone shed any light on this?

---

### Post by overdrank on 2007-09-18
> **scottym said:**
> Just upgraded to Feisty using CD and now my swap partition will not auto mount.
The fdisk output is:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1779    14289786   83  Linux
/dev/sda2            1780        1795      128520   83  Linux
/dev/sda3            1796        2350     4458037+  83  Linux
/dev/sda4            2351        2432      658665   82  Linux swap / Solaris
 
the fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d1856a7b-0d67-4613-bc4c-d9a13f370a21 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=44a09475-9391-41e3-9bff-d801ad74260c /boot           ext3    defaults        0       2
# /dev/sda1
UUID=0229e0b7-a13c-4955-9253-08384e2ee930 /home           ext3    defaults        0       2
# /dev/sda4
UUID=12bcec6d-d477-412d-a490-d9269f45567c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Here is the free output:

             total       used       free     shared    buffers     cached
Mem:        636412     487212     149200          0      13412     231136
-/+ buffers/cache:     242664     393748
Swap:            0          0          0


Can anyone shed any light on this?

Hi I don't believe swap will mount it is just that swap
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Bothered on 2007-09-18
Have you checked the uuid of the swap partition? Could you post the result of "ls /dev/disk/by-uuid".

---

### Post by scottym on 2007-09-18
Here are the uuid results.



 ls /dev/disk/by-uuid
0229e0b7-a13c-4955-9253-08384e2ee930  4eb79727-8790-4d76-ba46-f224f6b00439
44a09475-9391-41e3-9bff-d801ad74260c  d1856a7b-0d67-4613-bc4c-d9a13f370a21

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
	Lastly here, the Status should be changed to Accessible, do so, and for those who are wanting data back, use the browse option and transfer it elsewhere ( if it says you are not allowed, or similar, follow the next part and then try again.

Step 3
	
	Because of the way the Linux system works, Root controls most of what goes on in the computer, now it would be nice if we the user also had a piece of that as well, we can, with this.

	Click on Applications, from the drop down menu click on Accessories, from the drop down menu click on Terminal and let the application start.
	Type in the following:-

	sudo chown &#8220; YourUserName:YourUserName&#8221; don't include the quote marks /home /Your User Name/The name of the file you made

	which is the path to the file you made and should look like this, mine personally

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

### Post by oilchangeguy on 2007-09-18
here's a novel idea. why not reinstall, and let ubuntu set it's own partitions.

---

### Post by rsambuca on 2007-09-18
> **scottym said:**
> Here are the uuid results.



 ls /dev/disk/by-uuid
0229e0b7-a13c-4955-9253-08384e2ee930  4eb79727-8790-4d76-ba46-f224f6b00439
44a09475-9391-41e3-9bff-d801ad74260c  d1856a7b-0d67-4613-bc4c-d9a13f370a21

For some reason your swap partition uuid has changed.  For simplicity, I would just edit your fstab to look like this.  Use ```
gksudo gedit /etc/fstab
```
> he fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=d1856a7b-0d67-4613-bc4c-d9a13f370a21 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda2
UUID=44a09475-9391-41e3-9bff-d801ad74260c /boot ext3 defaults 0 2
# /dev/sda1
UUID=0229e0b7-a13c-4955-9253-08384e2ee930 /home ext3 defaults 0 2
# /dev/sda4
**[COLOR="Red"]/dev/sda4[/COLOR]** none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by rsambuca on 2007-09-18
> **oilchangeguy said:**
> here's a novel idea. why not reinstall, and let ubuntu set it's own partitions.

Why does he need to re-install just to set the swap?

---

### Post by oilchangeguy on 2007-09-18
> **rsambuca said:**
> Why does he need to re-install just to set the swap?

mainly, because there's no need to manually partition a hard drive to do a ubuntu install. just because you can, doesn't mean you should. ubuntu does a good job of setting the needed partitions on it's own. and since the user just installed 7.04, they have nothing to lose by re-installing. and not manually partitioning the drive.

---

### Post by rsambuca on 2007-09-18
> **oilchangeguy said:**
> mainly, because there's no need to manually partition a hard drive to do a ubuntu install. just because you can, doesn't mean you should. ubuntu does a good job of setting the needed partitions on it's own. and since the user just installed 7.04, they have nothing to lose by re-installing. and not manually partitioning the drive.

I think we must be talking about different things here.  I was just trying to help the OP.  Honestly, I have no idea why ellgor posted those instructions in here.

---

### Post by anaconda on 2007-09-18
actually "ls /dev/disk/by-uuid" isn't very useful command. instead
```
ls -la /dev/disk/by-uuid
```
woud tell you which uuid points to which partition.

anyway. I think your problem is that the swaps uuid in your /etc/fstab file isn't the same than the uuid of your swap partition. (the uuid changes if/when you reformat the swap-partition)

so the solution is to change the fstab fiel to not use the uuid for your swap instead use the old /dev/sda4 notation, which wont change if you reformat the swap..

EDIT damn, rsambuca beat me to it...

---

### Post by scottym on 2007-09-18
Problem solved by matching up th uide and fstab designation for the swap.
Thanks for all the replys.

---

