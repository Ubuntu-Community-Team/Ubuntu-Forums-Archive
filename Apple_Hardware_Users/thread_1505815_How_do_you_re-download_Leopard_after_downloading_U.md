---
title: "How do you re-download Leopard after downloading Ubuntu?"
date: 2010-06-09
forum: Apple Hardware Users
---

### Post by EvCrock on 2010-06-09
Alright, let me explain my situation.  I have a Macbook from about three years ago (a black one, if that helps) and I wiped my entire hard drive downloading Ubuntu to the last ten gigs of the hard drive.

:-(

BUT!!! I love Ubuntu, but miss all of my Mac stuff, specifically being able to run Netflix and my built-in iSight camera.  So, I'm wanting to download Leopard to my hard drive and be able to switch between Ubuntu and Mac OSX at will.  Can anyone either send me in the right direction or give me EXTREMELY DETAILED directions?  I am an absolute beginner, as indicated by my losing all of my info.  These forums are great!!

---

### Post by Frobber on 2010-06-09
This procedure is for a PPC. Yours is most likely is an Intel, some of the info may not be exactly verbatim (one I can recall is for PPC we use yaboot and Intel uses another boot screen).

The concept is there and may work for you.

**How to share Linux and OSX Operating Systems on an IMac  PPC**

This procedure contains information useful for installing Linux and OSX operating systems on an Imac PPC. The procedure is not all inclusive, it provides concepts and ideas that resulted from installing the two operating systems many times. Much of this information was provided by others on the Internet. Thanks to those whom have taken time and provided the information. 
Concept
- partition the Macintosh HD with 3 or more partitions. 
- make some partitions non-journaled.
- install the operating systems. 
- copy (NOT move) the entire OSX 'home folder' to one of the non journaled HFS+ partitions. 
- set the home directory for the user to the new partitions home. 
- reboot to the Linux side.
- change the directory location of /Downloads, /Documents, /Music, /Video ... to the location of the OSX home (easy with ubuntutweak). 
- make an entry in the /etc/fstab for the new partition (If /mnt is used, the partition will not appear as another drive) 
- reboot to the Linux OS and to OSX. 
- if everything works you can delete the old OSX home, which should now look like a normal folder instead of the home icon. 

How to do it
Before doing anything, backup the system stuff we want to maintain. I've used iBackup for the Mac OS. Backup the system settings, application settings, and stuff from the home folder. Use a second disk to backup software; iBackup, and other programs that are to be retained. For temporary storage a usb flash drive may be used.
Partition the hard drive. This is accomplished by booting from the OSX install CD and select disk utility. Create your partition scheme. The first partition is formated HFS+ (Mac OS Extended non-journaled) and is planned for Linux OS. The second partition is formated Mac OS Extended (journaled) and is for MacOSX. The remaining partitions are formated HFS+ and are for user discretion, 'data', 'music', pictures and movies, blah, blah, blah. 

With this style formating most operating systems can access, read, and write to the HFS+ partitions for 'owner' files.
Note
A Linux OS install will create yaboot in the boot sector of the hard drive. Yaboot is used to select what OS is to be 'booted'. OSX install will clear the the boot sector for its own use; therefore, OSX must be installed first. 

Install OSX and any additional application software on the second partition but do not execute the program.
Use the Mac OSX Software Update ensure your system is up to date.

Restore data from the backup disc. Restoring this way will create preferences, and application support files in the home library. This also restores the Address Book, iCal, Mail, All the preferences for web browsers, all other user data.  After this procedure, applications may be started. When the applications are started it will appear as if we never left.

Copy (not move) all your 'home' files to the reserved HFS+ partition you selected for data.

Open system preferences, Select Accounts, unlock the window that opens. Right-click on your user, select advanced. At the entry for location of home select browse and locate home to your new location. Exit out. Notice the HOME Icon moved to the new partition.
 
Install the Linux operating system on the first partition. If using the Ubuntu Live CD, before starting install open the disk partitioner. Remember, during the MacOS install you had only x number drives. In the Linux disk partitioner more drives will be displayed. Mac inserts 128Mb 'buffers' between partitions; Linux displays these as additional drives. Don't fool with these buffers. Delete the bigGB partition that was planned for the Linux install. The disk partitioner should now show this bigGB as free space.
 
Start installation. When you get to the partitioning section, select 'use available free space' for Linux. Doing it this way we can allow the installation media to suggest how to partition for the OS. Of course if experienced or you want a different file system you may use manual partitioning.

About Editors
The following procedures are written for using (single user) console mode. I choose this because some editing I have done requires not being in graphics mode. Also, I am comfortable using console mode (it also reminds me that I'm editing and not playing). The following editing doesn't care about graphics mode, so you may use your editor of choice. I choose the nano editor because it works in Linux and OSX.
 
To enter console mode:
Key &#8211; control+alt+F1  (or F2, or F3, or F4, or F5, or F6, your choice)
To exit console mode:
Key &#8211; control+alt+F7 
Dual Boot Configuration
The dual boot capability is managed under the Linux OS. A list of three options will be presented when you turn on or restart the computer. During initial install Linux is set to be the default OS. Yaboot is the application that controls this list and the list will look something like this (Note: there will be variations determined by what operating systems are installed on your computer): 
 l - linux
 x - macosx
 c - cdrom

If you wait a few seconds, the default OS 'Linux' is automatically selected. The default OS can be changed by configuring /etc/yaboot.conf. This file is located in the linux partition of the hard drive.

To configure yaboot. Boot into linux.

Enter console mode.  

Type &#8211; cp /etc/yaboot.conf /etc/yaboot.conf.backup

Type &#8211; sudo nano /etc/yaboot.conf (enter password when prompted)
 
Find the entry: 
	macosx=/dev/hdxn

	Where x (this x refers to the x in hdxn, not in macosx) is a letter (usually a, b, c or s) and n is a number, 	likely between 9 and 12. 

Insert a new line below macosx=/dev/hdxn: 
	defaultos=macosx

Save the file and exit. 

Key &#8211; ctrl-x to exit nano. Key &#8211; y. Press &#8211; return. 

If there isn't a macosx=/dev/hdxn entry, determine which partition contains the Mac OS. Exit the editor and  Type &#8211; sudo mac-fdisk -l. Look for a partition that has a line like this:
 
/dev/hda3 Apple_HFS Apple_HFS_Untitled_2 20709376 @ 262208   (  9.9G)  HFS

Obviously, the data after Apple_HFS Apple_HFS will be different, this is your Mac OS partition. 

OSX is on /dev/hda3 so you would need to add a line "macosx=/dev/hda3" to your yaboot.conf. 


Make these changes permanent by running the ybin application. 

Type &#8211; sudo ybin -v (enter password if prompted)

logout, exit console mode. 

The bootloader should now be configured. Restart the computer and wait briefly (<30 seconds). If Mac OS (X) boots, then you did things right. If it doesn't, chances are you'll boot into linux anyway. 

Match Linux and OSX user IDs
Sometimes, after updating Linux or a fresh install of Linux, we are presented with 'Cannot mount volume &#8211; you are not privileged to mount volume' while attempting to access some partitions of the hard drive. This is caused by file ownership and possibly the /etc/fstab file.
To access OSX partitions from the Linux side, the UID and GID must match the OSX UID and GID. During OSX install, the first user and OSX administrator is assigned UID 501 and GID 20. When a Linux system is installed, the user IDs start at 1000. 
We can change our user IDs to match the IDs for the MacOS from the Linux side.
To verify our UID and GID on the Mac side, login, open a terminal and Type &#8211; id. The response will display the required information.
The UID and GID cannot be changed for a user that is logged in. With Ubuntu we need to create a 'Temp' user with administrative privileges, and perform the procedure while logged in as the 'Temp'. The 'Temp' user will use sudo -i to change to root user. 
The following procedure is written for a system that has 'Root' user capabilities, and nano is the editor.. 
Note
All we are doing is changing the ID numbers and nothing else.
1.At the login screen, Key &#8211; control+alt+F1. Observe that we have entered console mode.
2.Log in as root, or the Temp user.
Edit the file /etc/login.defs.
Type &#8211; nano /etc/login.defs
Find the value UID_MIN. Change it from 1000 to 501.
Find the value GID_MIN and change it to 501.
Save the file and exit. 
Key &#8211; control+x. Key &#8211; y. Press &#8211; return.
Edit the file /etc/group.
Type &#8211; nano /etc/group
Find the line that displays dialout:x:20:(username); change the value 20 to be 99.  
Find the line that displays (username):x:1000: and change it to (username):x:20:
Save the file and exit. 
Key &#8211; ctrl-x to exit nano. Key &#8211; y. Press &#8211; return. 

Edit the file /etc/passwd.
Type &#8211; nano /etc/passwd
Find the line that displays (username):x:1000:1000:(real name),,,,/home/(username):/bin/bash and change it to be (username):x:501:20:(real name),,,,/home/(username):/bin/bash
Save the file and exit. 
Key &#8211; control+x to exit nano. Key &#8211; y. Press &#8211; return.
Change file permissions of the home folder.
Type &#8211; cd /home
Type &#8211; chown -R 501:20 (username)
Exit console mode.
Key &#8211; control+alt+F7
Reboot. 
If this did not work and you received a message stating that one of the files could not be changed, it is likely that you are still logged in as (username) somewhere on the system. Try rebooting and logging as temp at the Login Screen. 

If this procedure was performed using Ubuntu the 'Temp&#8221; user may now be removed from the system.

We should now be able to access user files from either OS.

---

### Post by EvCrock on 2010-06-12
So I finally get around to being able to do this, and Mac OSX won't seem to download.  I partitioned the disks as instructed, one for Ubuntu, one for Mac OSX and one for... other stuff.  I set it to "GUID Partition table" because the installer told me it wouldn't work unless I did that, does anyone know where I'm going wrong?

I knew I'd run into problems, but I just didn't think it would happen already.

---

### Post by Neds Moar Salt on 2010-06-13
> **EvCrock said:**
> So I finally get around to being able to do this, and Mac OSX won't seem to download.  I partitioned the disks as instructed, one for Ubuntu, one for Mac OSX and one for... other stuff.  I set it to "GUID Partition table" because the installer told me it wouldn't work unless I did that, does anyone know where I'm going wrong?

I knew I'd run into problems, but I just didn't think it would happen already.

Don't expect a detailed solution if you can't give a detailed explanation of the problem.

---

### Post by EvCrock on 2010-06-13
I hope I didn't come across as rude when asking for help, I'm just extremely new to all of this.  As far as my experience goes, I thought I was giving detailed explanations of my problems.

Can you tell me what else I should include?  I'll try to find it out.

---

