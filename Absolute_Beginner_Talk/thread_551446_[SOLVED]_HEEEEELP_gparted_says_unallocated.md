---
title: "[SOLVED] HEEEEELP: gparted says unallocated"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by wakeboarder on 2007-09-15
To make a long story short I copied a 60GB disk with 2 partitions WinXP/NTFS and a FAT32 to a 100GB disk and then added Ubuntu /etx3 + swap. So far all is well.

Then I deleted the WinXP partition from the original disk thinking that I wouldn't need any more, I would copy the files I need from the new 100GB disk.

However it turns out I would like to restore the WinXP partition back to the 60GB disk.

So I tried running gparted again, but no matter what combination I tried it refused to copy the partition to the other disk.
So I booted WinXP and tried running Partition Magic which never failed on me so far and it said something about a missing drive letter on the 100GB disk. 
Ok, back to the Ubuntu again, started gparted. 
BUT, now it says "partition unallocated" for the 100GB disk. Even though I have several working partitions here both Windows and Ubuntu.
The 60GB disk with the remaining partition seems to be ok.

What should I do to be able to use gparted again?

---

### Post by julian67 on 2007-09-15
I think you have a broken partition table on the new drive. This doesn't seem to be unusual after using Partition Magic (or an older version of parted) on a disk with both MS and Linux filesystems. 

If you still have enough room on the 60 GB drive I would back up all my data on to that one. 

**Then physically remove the good 60GB disk from the PC so only the faulty disk is in there.**

Next to repair the 100 GB disk:

try to delete all the partitions with Partition Magic CD. There's a chance that this will fail with an error. If you find that both PM and GParted fail to recognise the disk there's other stuff to try if you have a Windows CD. Boot from the Windows CD and start the install process. When you get to the partition stage delete **all** the partitions. Do not create any. Now quit out of the install and reboot with GParted disk and you should get the disk recognised as a raw unpartitioned disk ready to be partitioned, formatted etc. Once you're happy the disk looks normal again you can now install Ubuntu in the normal way. 

This has worked for me before, I hope it works for you. 

I threw away my Partition Magic CD quite a while ago and since then I haven't had any problems with partitions or partition tables ;-)  Clonezilla-gparted is a great substitute for both Partition Magic and Norton Ghost and the similar Acronis products. I threw out my Acronis disks too :lolflag:

---

### Post by ellgor on 2007-09-15
A howto mount/access hard-drives, cd units etc. easily.
	        (for  newbies to Linux) 

   

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

### Post by julian67 on 2007-09-15
thats a nice howto about formatting and permissions but it won't help fix a broken/unrecognised partition table ;-)

OP states  > now it says "partition unallocated" for the 100GB disk. Even though I have several working partitions here both Windows and Ubuntu.

---

### Post by wakeboarder on 2007-09-15
Thanks for all help!

After some googling I did the following.

1. Downloaded the gparted LiveCD ISO and created a CD
2. Booted from the CD and ran Testdisk
3. Testdisk reported some errors in the partition table for the 100GB disk
4. Let Testdisk repair the errors
5. gparted can now "see" the entire disk again!

Linux Rocks!!!
:guitar:

BTW I think it was Partition Magic that messed up the disk.

---

### Post by julian67 on 2007-09-15
> **wakeboarder said:**
> Thanks for all help!

After some googling I did the following.

1. Downloaded the gparted LiveCD ISO and created a CD
2. Booted from the CD and ran Testdisk
3. Testdisk reported some errors in the partition table for the 100GB disk
4. Let Testdisk repair the errors
5. gparted can now "see" the entire disk again!

Linux Rocks!!!
:guitar:

BTW I think it was Partition Magic that messed up the disk.

You made the best solution :-) glad it worked

---

### Post by wakeboarder on 2007-09-15
Yeah, but now I'm back to my original problem before all this started.

gparted doesn't let me copy the ntfs partition from the 100GB disk to the 60GB disk.

I can select copy from the 100GB disk but when I switch to the 60GB disk I can't select paste.

I tried deleting the partition that was on the 60GB disk which actually was the old copy of the same partition but with most files deleted. So the size is exactly right.
I tried creating an ext3 partition to have something to "write over" but no luck.
I tried creating a ntfs partition but then the partition ends up being a little bit to small, gparted puts a small unallocated partition after the created partition.
:confused:

---

### Post by wakeboarder on 2007-09-15
I will try to make the space for the partition a little bit bigger.
Since maybe this is the reason why gparted doesn't let me paste a copy there.

---

### Post by julian67 on 2007-09-15
You're probably unable to paste because the receiving drive is mounted/in use. But anyway Gparted is not the best way to clone whole partitions and disks as it is rather slow. 

Try clonezilla live, it's great for cloning. 

[http://clonezilla.sourceforge.net/gparted-clonezilla/]("http://clonezilla.sourceforge.net/gparted-clonezilla/")

Read the docs/website first but the live CD is much easier to use than you'd think from the website, it has an easy to understand menu driven interface. 

I compared it against Acronis True Image and clonezilla was at least as fast, and certainly as capable. Using a laptop and an external USB drive (two slow drives) I can clone my disks at 1GB per minute. And it doesn't waste time copying unused parts of the drive so if your drives are not so full it is very rapid. it fully supports ntfs.

---

### Post by wakeboarder on 2007-09-16
Clonezilla sounds interesting I will give it a try.
thanks!
:)

---

### Post by wakeboarder on 2007-09-16
From reading the clonezilla website I see that both clonezilla and gparted use ntfsclone to clone a ntfs partition.
So my guess is that gparted is equally fast or slow in my case. Maybe depending on how they use the parameters to clonentfs (gparted use -f)

The main feature of clonezilla seems to be the multicast feature to clone many computers at the same time 40+.

Maybe clone all the computers in the office to Ubuntu over night?
hehehe
:)

---

