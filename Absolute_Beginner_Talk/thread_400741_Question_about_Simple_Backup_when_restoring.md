---
title: "Question about Simple Backup when restoring??"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-04-03
I have installed Simple Backup and have configured it how I like, am ready to backup but then from the Ubuntu page I see this in the Restore part:

**"Note:- By default Restored Files and Directories are owned by root this is because of sbackup will runs with root. You need to change these files or folder permissions using chmod or just right click and select properties of the file or folder."**

This I am unsure of. What does this mean exactly? When I restore, EVERYTHING is root, and so I can't do anything without running it as sudo? Like even Firefox or whatever? Or am I completely misunderstanding this...

Any help appreciated I really need to back this sucker up ASAP! :confused:

---

### Post by bruenig on 2007-04-03
That is how it reads yes. Although realize that firefox and nearly everything else on your computer is owned by root. The only things that aren't owned by root are the things in your /home/username/ folder. So it is not really something to concern yourself with. Just have it restore and then
```
sudo chown -R username:username ~/
```

---

### Post by herbster on 2007-04-03
bruenig,

Thanks for that! As for the "username:username" part, if mine is "joe" I just put "joe:joe" ??

And yeah, it just clicked for me that root is the same as "filesystem", which is what I'm used to it being called when I browse my drives and partitions in the window browser, lol.

---

### Post by Ptero-4 on 2007-04-04
I think it`s username:groupname instead of username:username. So it would be joe:users.

---

### Post by bruenig on 2007-04-04
True it is username:groupname, but by default the groupname is the same as the username. So you would be user joe in the group which is also called joe.

So joe:joe.

---

### Post by dannyboy79 on 2007-04-04
I just did a restore less than 1 week ago and the folders and files within my /home dir are still owned by ME. All I do is use the sbackup config option and set it to run thru that. I have it run daily or whatever. Howerver, if some folders or files do get changed to root and you want it owned by YOUR username and YOUR group, than yes, it's joe:joe. At least that's what mine is. I may be part of the users group, but I also have my own group. At least that's the way the default Dapper Install was.

I would like to point out that after 1 year, I was finally able to "test" (restore) a full backup using this program's backed up file (files.tgz). It WORKED!!!!

Ok, say for whatever reason your whole entire system went down and there was no way possible to get anything back!!! You have your backup files.tgz tucked away on a seperate hard drive or cd or wherever (I would never use the default sbackup folder of /var/!!!). Well what if you didn't want to have to futz around and reinstall Ubuntu and then reinstall sbackup so that you can use it's "restore-option". This method will work for you!!!! I didn't want to try sbackup-restore option within my real install and then if it didn't work (bad archive or whatever) I'd be without my laptop, so I figured i'd take a minimal amount of space and create a new partition to test out the backup system. 

Step by Step (these steps are for a normal linux user and who has familarity with the "normal" linux commands/operation):
(NOTE: always make a backup copy of any file you edit, sudo cp /folder/file /folder/file-backup or just sudo cp file file-backup if you're in it's base folder.) This is done from within your "real" system.

1. create a new partition thru gnome partition editor. make sure you give yourself more than what the current install states. Mine stated it was 2.6gb thru **df -h** so I created a 4gb partition to be sure that when I extracted it and ran the system, there was enough room for temp files and whatnot.

2. mount this partition to wherever you'd like (my example is /mnt/hdb5 so be sure to adjust throughout the entire guide)

**sudo mount /dev/hdb5 /mnt/hdb5**

3. I had my files.tgz sbackup file on another computer within my network. What's also nice about sbackup is that it also creates a file which contains each and every package that you have installed. I mounted the network share that contained my backup file using cifs as I feel that is faster than smbfs. (you could use a cd or dvd or whatever but I don't have a dvd-rom on this laptop and my backup is obviously larger than 650mb) I use 
**sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777**
(NOTE: you can also use ip address instead of netbiosname if your name resolution isn't setup or working. Full credit goes to dmizer. [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534))

4. Then I simply cd into the network shares mount point where the files.tgz is and type this in the terminal
**tar xvpfz files.tgz -C /mnt/hdb5/** ***_SEE NOTE_***
(NOTE: this may take awhile depending on your network speed. I'll be honest here, I am not sure if I used sudo or not. SORRY!!!! Don't know if this will help but I just checked some of the files and folders that were restored and they are still owned by me so does that mean I didn't run the tar command as root??? I wish I would've documented it better. try it first without sudo)

5. After it's done, you should be able to **ls -la** the /mnt/hda5/ folder and see /bin, /etc, /home, /usr and whatever else you chose to backup. I have attached my sbackup.conf file so you can see exactly what works with the include and exclude option. A "0" means exclude it (don't back it up)  and a "1" means include it in the backup. I have attached a txt file because I am at work on my lunch break doing all this thru ssh and I merely opened the sbackup.conf file in nano and copied everything out of it for this guide. To make it easy. Just open your sbackup.conf and paste in what you cut from my file. Don't edit this file if you have simple backup config open!!! I would like to point out that I did chose to backup /dev but when I restarted it it failed or whatever so I believe I did have to mkdir that folder as well!

6. At this point we need to recreate any "main" folders that didn't get backed up which means they didn't get restored. The ones that I had to **sudo mkdir** are listed right below. These are the ones that I chose to NOT backup. You may also have chosen to NOT backup stuff in your /home folder or whatever else but I would say that these at a minimum need to be remade. I would like to point out that I did chose to backup /dev but when I restarted it it failed or whatever so I believe I did have to mkdir that folder as well! VERY IMPORTANT, make sure that you create these folders WITHIN /mnt/hda5/!!!!

/proc
/media
/mnt
/cdrom
/var/cache
/lost+found
/tmp
/var/tmp
/sys

7. After you have remade all those folders it's now time to edit the fstab of the backup system. **sudo gedit /mnt/hda5/etc/fstab** and change the     /     line so that it calls for your new partition. (NOTE: make sure you don't accidentally open your "REAL" fstab. Notice we are opening the fstab within /mnt/hda5/etc/!!!!) you can also comment out any other partitions that you don't want mounted. Now, I only wanted to check to see if the backup system worked so I couldn't mount my real /home partition because then I wouldn't know if the entire backup works all by itself so I commented out my /home line as well. You do need to leave proc swap cdrom and floppy if you have them. Remember, if you were to go to /mnt/hda5/home/ you'll see all the users folders and then within that everything will be there based on what you backed up and restored. So we want to modify the fstab so that we can fully check that if you had to do a full restore it would work!! Make sure you save your changes and exit!!!!

8. Now it's time to modify the menu.lst of the backup system. sudo **gedit /mnt/hda5/boot/grub/menu.lst** and change every single location that used to reference the old partition. So I went around and looked for everything that said (hd0,2) and changed it to be (hd0,4) and also went around and changed everything that said    hda3   and made it say hda5. Don't forget about the #groot and #kopt lines!!! This will ensure that your backup system boots from grub. Make sure you save your changes and exit!!!!

9.  Last but not least it's time to update your real menu.lst. **gedit /boot/grub/menu.lst**. Simply add an entry like this

title           Ubuntu, 2.6.15-27-386 backup
configfile (hd0,4)/boot/grub/menu.lst

(NOTE: What this will do, is that when your real ubuntu is loading, your grub menu will appear, then within the list is this backup boot option which will then simply take you to a new grub boot menu which will boot up your "backup" system.) Make sure your (hd0,4) is calling for whatever partition your backup's grub files are. Mine are on hda5 so in grub, that is (hd0,4). That means hard drive 1 and partition 5. grub starts at zero. as I said above, make sure you add it after the automagic update and you'll be fine. well really this is only temporary and chances are that you won't be updating your kernel while your testing out your backup system but that's up to you. Oh, I changed the timeout option from 1 to 15 so that I would have enough time to chose the backup option, it's in seconds. Make sure you save your changes and exit!!!!

10. That's it. Shutdown and or restart and try to boot up this backup system by chosing it within the grub menu. If it works than you know you have a safe backup tucked away that you can count on!!!!!!

If anyone finds something incorrect with this please pm me or post here and I'll fix it. I feel this is an invaluable way to make sure your backup works!!! I have had my backup system running now for over a week and I have I verified that the system is "working" I have tryied various things, like browsing, mousepad, gaim, ssh, and other stuff that I can't think of right now.


*_Fdisk for refernce_*
/dev/hda1               1          32      241888+  82  Linux swap / Solaris
/dev/hda2             758        1299     4097520    f  W95 Ext'd (LBA)
/dev/hda3   *          33         497     3515400   83  Linux
/dev/hda4             498         757     1965600   83  Linux
/dev/hda5             758        1299     4097488+  83  Linux

hda3 is my real /, hda4 is my real /home and hda5 is my test partition. i know you're going to ask what hda2 is, well that's merely the extended partition, I always like making an extended partition right away in case I need another partition as I have done here by creating hdb5. So apparently ubuntu can boot from logical partitions and not just primary partitions!!

---

### Post by herbster on 2007-04-10
dannyboy79,

Wow, thanks for that post man!!! I have printed it and pinned it to the bulletin board for reference when I restore. I just made my first backup the other day with Simple Backup and burned it to DVD-RW.

BTW, Did you include /dev in your backup? What exactly did you EXCLUDE so I can see how close my own config is to yours??

---

### Post by dannyboy79 on 2007-04-10
not to be rude but I posted a very long thread so that I could include all the details neccessary and I did within the thread inform you what should and shouldn't be included within the sbackup gui. I even attached my sbackup.conf file so that other users could compare it against mine. but maybe you didn't see it or you have dial up and can't download I don;t know. here's what I included (everything that has a 1 within the sbackup.conf file I attached):

/initrd.img.old
/usr/
/opt/
/lib/
/vmlinuz
/home
/bin/
/etc
/sbin/
/root/
/boot/
/initrd/
/initrd.img
/var/
/dev/
/vmlinuz.old\

NOTE: yes I did notice that some of the directories have the trailing slash and the /etc dir doesn't. Not sure how that happend but my backup IS working using these exact settings!!!! here is what I exluded (don't forget that sbackup also will exlude anything that meets the criteria. ie; regex = \.mp3,\.avi,\.mpeg, blah blah blah
which is within the /etc/sbackup.conf file as well:

/proc
/media/
/mnt/
/cdrom/
/var/cache
/lost+found/
/tmp
/var/tmp
/sys

NOTE: yes I did notice AGAIN that some of the directories have the trailing slash and the /sys dir doesn't. Not sure how that happend but my backup IS working using these exact settings!!!! Also, note that you may want to include your media folder. That's a user decision and there are no system files within it.

---

