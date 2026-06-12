---
title: "how do I format a drive in ubuntu?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-19
how do I tell ubuntu to erase/format a drive?  I have a drive mounted on there now via USB that is currently in Mac format, which I want to use as a backup drive for the ubuntu system.  How do I format it into whatever format ubuntu wants?  Or could I just leave it in Mac, I guess?  (actually, the "drive" I want to format is a drive that I already partitioned into two sections on the mac... half is a backup of part of the music collection, half is going to be the backup of the ubuntu system (if that's not too compicated)...

---

### Post by hyper_ch on 2007-09-19
install gparted... that a graphical disk partitioner. That should be able to do the job.

---

### Post by logos34 on 2007-09-19
Find the partition you want to format:

**sudo fdisk -l **(lowercase L)

For example, let's say your internal drive is showing up as sda, and the external usb as sdb, and the partition you want to format is the second one, sdb2.  You could use mkfs to format as ext3:

**sudo mkfs.ext3 /dev/sdb2**

Or use gparted.

---

### Post by willfriedwald on 2007-09-19
thank you  - will give it a try right now - always anxious to do something graphical rather than terminal!

w

---

### Post by ellgor on 2007-09-19
> **willfriedwald said:**
> thank you  - will give it a try right now - always anxious to do something graphical rather than terminal!

w

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
	
Lastly here, the Status should be changed to Accessible, do so, and for those who are wanting data back, use the browse option  ( if it says you are not allowed, or similar, follow the next part and then try again).

Step 3
	
	Because of the way the Linux system works, Root controls most of what goes on in the computer, now it would be nice if we the user also had a piece of that as well, we can, with this.

	Click on Applications, from the drop down menu click on Accessories, from the drop down menu click on Terminal and let the application start.
	Type in the following:-

	sudo chown “ YourUserName:YourUserName” don't include the quote marks /home /Your User Name/The name of the file you made

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
	Leave a space and enter the filesystem/type   ext3(or Ntfs etc)
	Leave a space and enter the options     defaults
	Leave a space and enter these two numbers with a space between 0 2 (don't ask)

	Your finished line should look like this:-

	/dev/hdc1 /home/gordon/hardtwo ext3 defaults 0 2 

	Everything done then close the window and you will be asked if you want to save it, do so and that's about it.

	To check things, open up your home folder and open up the file you made and click on properties (it may need a reboot to sort things out) you should be the Owner and Group with full permissions throughout.
	You should also see if the size matches what you put in and there will be a folder already in there called lost+found, its your folder.

	 Hope this helps, Regards Ellgor.

---

### Post by willfriedwald on 2007-09-20
hey - I don't have the "discs" application - at least I can't find it in administration or any of the menus -

have been trying to do this with gparted ---- but should I be using DISCS - where can I get that?

thanks!

w


-----------

Hey - I did get it to work with gparted, after trying a bit...

I took a 400 GB USB drive and broke it down into two partitions, both in ext3.

however, when I try copying a file to either drive I get an error message: you do not have permission to write to this drive!

what do I do?  I go into properties, then into permissions - and everything is greyed out - it won't let me change any permissions.

what to do?

thanks!

w

---

### Post by psusi on 2007-09-20
Just use gparted.  The disk manager thing was a POS and has been removed.

---

### Post by willfriedwald on 2007-09-20
can gparted help with permissions?  I can't find anything in gparted that pertains to changing permissions .... or anything anywhere else with regards to changing partitions either!

w

---

### Post by logos34 on 2007-09-20
you have to use 'chmod' from the command line to change permissions

---

### Post by willfriedwald on 2007-09-20
great!

I need more than just "chmod" at the command prompt, right?

if I type that, does it give me a list of options?  would like to change the permissions for these two partitions on an external USB drive - or at least one of them...

---

### Post by logos34 on 2007-09-20
this should answer your questions:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by willfriedwald on 2007-09-20
will@will-linux:~$ chmod a=w /dev/sdf
chmod: changing permissions of `/dev/sdf': Operation not permitted
will@will-linux:~$ chmod a=w /dev/sdf1
chmod: changing permissions of `/dev/sdf1': Operation not permitted
will@will-linux:~$ 

that's what I get - but I do believe sdf1 is the correct name for the partition...

at least it didn't tell me that sdf1 does not exist!

assuming that I have the right name (how do I find out if I don't) why wouldn't it let me change the permission on a blank usb drive?

thanks

willfriedwald

---

### Post by logos34 on 2007-09-20
use
[B]
sudo[/B] chmod ...


The '=' in

sudo chmod a=w /media/sdf1

is going to erase all permissions and add just write...but you need read permision too!  So then you have to go

sudo chmod a+r /media/sdf1

so you end up with    -rw-rw-rw-

EDIT: the partition needs to be mounted first to run chmod (i.e. /media/sdf1)

---

### Post by willfriedwald on 2007-09-20
well this is promising, I must say, no error messages :

will@will-linux:~$ sudo chmod a=w /dev/sdf
Password:
will@will-linux:~$ sudo chmod a+r /dev/sdf
will@will-linux:~$ 

for good measure I ran both lines with sdf1

will@will-linux:~$ sudo chmod a=w /dev/sdf1
will@will-linux:~$ sudo chmod a+r /dev/sdf1
will@will-linux:~$ 

I didn't get an error message - but then when I tried to copy something to the drive, it still would NOT let me ... so am not sure what happened or didn't happen - do I need to restart the computer or something?  or maybe I have to close terminal first for the changes to be implemented?

thanks yet again...

w

---

### Post by logos34 on 2007-09-20
see my edited post above...it needs to be mounted (sorry, tired)

create mount point if necessary:

sudo mkdir /media/sdf1  (or use anything in place of sdf1)

sudo mount -t ext3 /dev/sdf1 /media/sdf1

make yourself the owner with your username:

sudo chown username:username /media/sdf1

now run your chmod commands to set permission however you want.

---

### Post by psusi on 2007-09-20
You do not want to change the permissions on the device itself; that just sets who can access the raw device.  You want to change the permissions on the files in the mounted filesystem.

---

### Post by willfriedwald on 2007-09-20
will@will-linux:~$ sudo mkdir /media/sdf1
Password:
will@will-linux:~$ 
will@will-linux:~$ sudo mount -t ext3 /dev/sdf1 /media/sdf1
will@will-linux:~$ sudo chown username:username /media/sdf1
chown: `username:username': invalid user
will@will-linux:~$ sudo chown will:will /media/sdf1
will@will-linux:~$ sudo chmod a=w /dev/sdf1
will@will-linux:~$ sudo chmod a+r /dev/sdf1
will@will-linux:~$ 

am not ashamed to admit I had to be told to put in my actual username in place of "username" !

okay...

holy moley!

it seems to have worked - at long last, I can write a file to that drive!

this is the first time I have gotten something to work in terminal for me - and to think it only took 89 posts from you guys!

thanks again!

love that linux!

w

---

