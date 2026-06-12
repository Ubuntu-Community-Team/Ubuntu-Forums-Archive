---
title: "Not privileged to mount drives.."
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by blop on 2007-09-17
Hi all, im getting really really frustrated with mounting drives in Ubuntu 7.04. Im attempting to plug in my USB pen drive (fat32) and use it but it keeps giving me messages like...

im not privilaged to mount it and when i use Gparted to mount it it wont let me write to it..

IS there a way to auto mount and set correct rights....as doing this for every usb drive i use would be a pain.

many thanks!

---

### Post by blop on 2007-09-17
bump

---

### Post by PmDematagoda on 2007-09-17
I know this may not be the solution you want, but have you tried running Gparted as sudo?

---

### Post by blop on 2007-09-17
hi...thanks for the reply.

I have ran gparted as sudo and it allows me to mount it to /media/sdb1 but it then says i cant write to it....

i have tried to chown -c username /dev/sdb1 and /media/sdb1

all no go..

so annoying when its supposed to plug and play...

---

### Post by PmDematagoda on 2007-09-17
Did you check the USB drive for errors?

---

### Post by ellgor on 2007-09-17
> **blop said:**
> Hi all, im getting really really frustrated with mounting drives in Ubuntu 7.04. Im attempting to plug in my USB pen drive (fat32) and use it but it keeps giving me messages like...

im not privilaged to mount it and when i use Gparted to mount it it wont let me write to it..

IS there a way to auto mount and set correct rights....as doing this for every usb drive i use would be a pain.

many thanks!

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

	sudo chown “ YourUserName:YourUserName” don't include the quote marks /home /Your User Name/The name of the file you made

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

### Post by iansane on 2007-09-18
as root I can mount and unmount drives. I could just give my user account permission to mount but I want to learn the terminal sudo command. I tried using sudo mount XP because "XP" is the name of the mount point. It shows in "media" as "37.3 GB volume" when it is not mounted, but when it is mounted it shows as "XP" I have the ntfs3 config tool installed and set to allow read and right. I want to unmount it as root and just mount when I need to from limited account so all the user accounts can't see it when they log in. What should I type in terminal besides "sudo mount" ?

---

