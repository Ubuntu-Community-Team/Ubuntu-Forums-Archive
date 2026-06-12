---
title: "Formatting a SATA drive"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-07-29
Ok...I have a 300g SATA drive, that *was* being used in windows. It is now Empty, and I would like to make it available to write to through linux (to hopfully being the process of almost completely eliminating my need for Windows.) I am assuming that the best way to do this would be to format that drive to a file format that will be compatible with linux (as in, not ntfs like it currently is) Being very new with Linux, but very interested, and eager to learn, I am unaware of how to do this. Anyone care to help?

---

### Post by kinematic on 2006-07-29
go to system>administration>disks.
click on the partition and select to format it(ext3 is reccomended).
i don't know if it'll be added to /etc/fstab automatically because i've never added a disk afterwards.
if it isn't added open a terminal and do:
sudo mkdir /media/sda1(will probably be sda1 if it's the only sata drive)
sudo mount /dev/sda1 /media/sda1
sudo gedit /etc/fstab
the last command will open gedit as root and let you add it to your fstab file to add a mountpoint for it so it'll be mounted automatically on boot.
put this in your fstab:
/dev/sda1       /media/sda1     ext3    defaults        0       2
you could change the last 2 to 0 to prevent the file system from being checked on boot but the speed gain is to little to notice.

---

### Post by catlett on 2006-07-29
Was the drive installed when you installed ubuntu? Have you installed ubuntu? Is it internal or external?

---

### Post by bladefallcon on 2006-07-29
> **catlett said:**
> Was the drive installed when you installed ubuntu? Have you installed ubuntu? Is it internal or external?

Yes the drive was there when I installed Ubuntu, yes Iv installed Ubuntu (ok...that seemed redundant) and it is an internal Drive. Basically, i was using it with my windows xp installation...as an extra drive..There is nothing left on it, as It's all been backed up, in preperation for re-formatting it. All I need is how to do the formatting.

---

### Post by catlett on 2006-07-29
Go to System<Administration<Gnome partition editor
That is gparted, it is the partitioning application for gnome. If for some reason it is not installed, open a terminal and enter this command. Then go back to the menu.
```
sudo apt-get install gparted
```
When it opens it will have your master drive displayed as a bar graph. Go to the upper right and hit on the drop down box. It will list your other dives.
Select the 300gb sata drive. First operation is to select "unmount". Drives have to be unmounted to be partitioned. Then select "format to" and select ext3. That is the current linux filesystem that Ubuntu uses. There are others but ext3 is the one Ubuntu uses by default.

The next issue is changing the fstab file. If you had it installed when ubuntu was installed then there will be an entry for that drive in fstab.
The problem is it will be listed as ntfs. You have to change the entry to ext3. So enter this command to open up the file ```
sudo gedit /etc/fstab
```

This will not be your entry (obviously) but you should get the idea of what you have to do.
Find the entry for the sata drive. I'll use this one for an example.
> /dev/hdb2       /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
You need to change everything from ntfs on. So it will look like this
> /dev/hdb2       /media/hdb2      ext3    defaults        0       2
Make sure to hit save after you change the document.

If you do not know what the sata drive's label is, go back ionto gparted and it will show the drive's correct label. In gparted if you are unsure of which drive it is, look for the drive with 300gb.

This assumes you had the drive installed when you installed Ubuntu and that ubuntu has recognised it and mounted it (meaning you have been able to access the drive from ubuntu already but as read only)
If not you will have to use the directions in the above post to create a mount point and an fstab entry.

Post with any questions or errors, it is hard to think of everything that could be an issue.

---

### Post by kinematic on 2006-07-29
> **kinematic said:**
> 
/dev/sda1       /media/sda1     ext3    defaults        0       2


that's for your sata drive.

---

### Post by bladefallcon on 2006-07-29
> **catlett said:**
> Go to System<Administration<Gnome partition editor
That is gparted, it is the partitioning application for gnome. If for some reason it is not installed, open a terminal and enter this command. Then go back to the menu.
```
sudo apt-get install gparted
```
When it opens it will have your master drive displayed as a bar graph. Go to the upper right and hit on the drop down box. It will list your other dives.
Select the 300gb sata drive. First operation is to select "unmount". Drives have to be unmounted to be partitioned. Then select "format to" and select ext3. That is the current linux filesystem that Ubuntu uses. There are others but ext3 is the one Ubuntu uses by default.

The next issue is changing the fstab file. If you had it installed when ubuntu was installed then there will be an entry for that drive in fstab.
The problem is it will be listed as ntfs. You have to change the entry to ext3. So enter this command to open up the file ```
sudo gedit /etc/fstab
```

This will not be your entry (obviously) but you should get the idea of what you have to do.
Find the entry for the sata drive. I'll use this one for an example.

You need to change everything from ntfs on. So it will look like this

Make sure to hit save after you change the document.

If you do not know what the sata drive's label is, go back ionto gparted and it will show the drive's correct label. In gparted if you are unsure of which drive it is, look for the drive with 300gb.

This assumes you had the drive installed when you installed Ubuntu and that ubuntu has recognised it and mounted it (meaning you have been able to access the drive from ubuntu already but as read only)
If not you will have to use the directions in the above post to create a mount point and an fstab entry.

Post with any questions or errors, it is hard to think of everything that could be an issue.



Thank you for your help..this worked perfectly..

---

### Post by catlett on 2006-07-29
Great:!:  See you around the forum.

---

### Post by kinematic on 2006-07-29
i'm just curious if a directory in /media was created automatically after formatting or did you have to follow the steps i gave you or did you use the directory in /media that was used by your ntfs partition as a mountpoint?

---

### Post by bladefallcon on 2006-07-31
> **kinematic said:**
> i'm just curious if a directory in /media was created automatically after formatting or did you have to follow the steps i gave you or did you use the directory in /media that was used by your ntfs partition as a mountpoint?

There was already a /media directory, that I had previously created when trying to mount my other drives..

---

### Post by tehnad on 2006-07-31
I too have a curiosity about the mounting points. I was taught that you mount extra drives in the /mnt directory. This is how I have always done it without giving it a second thought.  Live cds will usually mount any drives that they see there also. Do you add extra drives to the media directory for better user file structuring purposes or is it because it is a bad idea to use the /mnt directory that is provided to add mounting points?

---

### Post by bladefallcon on 2006-07-31
> **tehnad said:**
> I too have a curiosity about the mounting points. I was taught that you mount extra drives in the /mnt directory. This is how I have always done it without giving it a second thought.  Live cds will usually mount any drives that they see there also. Do you add extra drives to the media directory for better user file structuring purposes or is it because it is a bad idea to use the /mnt directory that is provided to add mounting points?

I used the /media directory to mount drives because thats what it said on the information i found on here..Thats the only reason I did it. I wouldnt think it would make a difference one way or another, as long as you know where they are being mounted..

---

### Post by kinematic on 2006-07-31
doesn't really matter wich one of the 2 you use....you could even mount a drive in your /home/user directory or create a new directory.
it only serves as an access point for the OS to be able to read/write the files/folders on the partition.

---

### Post by bladefallcon on 2006-07-31
Ok...I have to ask this one question. One of the thing you asked me to do was to shange the fstab file...now as I understand it (and please correct me if im wrong) but each time the OS loads, it uses this file to find and mount each drive, and device (such as cd-roms) am I correct?

If the above is correct, then I would like a slight explanation of the file..specifically this:

```
/dev/sda1       /media/sda1     ext3    defaults        0       2
```

In the above section (copied from my fstab) I know the first 3 columns, and what they do/m,ean. But the rest, I dont know. What is the 'defaults' column for? how about the 0, and then the 2? what do they mean? What purpose do they hold? 

(forgive if this seems an odd question...I am trying linux out because one: i hate windows, and two: I love computers, and learning more about them, so being something i dont know about, linux was my next thing to learn..and when i learn, i liek to learn everything about it, down to the small details..)

---

### Post by kinematic on 2006-07-31
take a look at these 2 links:
[http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained](http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained)
[http://en.wikipedia.org/wiki//etc/fstab](http://en.wikipedia.org/wiki//etc/fstab)

---

### Post by catlett on 2006-07-31
I use /media because it (usually, lately when I help someone mount with live cd it isn't working) puts an icon on the desktop.I have alot of partitions and Ubuntu mounts them all in /media and I have icons on my desktop.
As already said, you can mount anywhere but I use /media for the desktop icon capability. (now that I think of it, the "show volumes" may not be enabled in the configuration and that is why it isn't working in the live cd)
Those 2 links were great. This is one that I stumbled upon before and it gave me my first understanding of /etc/fstab [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bladefallcon on 2006-08-02
ok....iv got myself a problem...The drive is formatted as a ext3...like was advised earlier in this post...but i cant write anything to the drive...it just keeps telling me i dont have permission...this permission thing is really starting to aggrevate me...Why wont it just let me use my computer???? Everytime i try to save a file, i dont have permission...its my damn computer...not Ubuntu's...

---

### Post by catlett on 2006-08-02
I'll just givce you an easy fix. Then I'll explain why.
Enter this in the terminal ```
gksudo nautilus
```This launches the file browser as root. Browse to the media folder where you mounted the drive/partition. Right click on the folder. The option menu will come up. Select "properties". When that window opens, select the "permissions" tab.
You will see that root owns the file. Under that is something like this
```
Oxner    Read    Write  Execute
Group    Read    Write  Execute
Others   Read    Write  Execute
```
As you can see in the window only root can "write". Check off the write box for others anf you might as well do it for group since you are the only one.
You can do this to any file or folder. Just launch with gksudo nautilus and then bring up the properties window. Select permissions and check off the boxes you want enabled, Read, write, execute or all of them.

A quick explanation. Linux comes from a server background where you would be one of possibly thousands of users on a system. The server is set up that your home is yours. Do whatever you want wqith it. No other user can go into your home and change things.
But you can't change anything in the root of the system. That is a base setup that every user is using. You can't have every user changing the root directory when the user base is large.
If something needs to be changed the system administrator logs in as root and makes the changes.
This is kept in the desktop version. It is still a good security feature because a virus or trojan etc cannot change your system unless it new the root password.

There are command line ways to change ownership but this is the easy way. Just remember you are opening up the file/folder to all users.

---

### Post by bladefallcon on 2006-08-02
thank you..that worked just fine for me...And thank you also for the explanation..with that in mind, It does make much more sense now.

---

