---
title: "Access files on a Mac hard drive in Ubuntu"
date: 2008-07-07
forum: Apple Hardware Users
---

### Post by tati on 2008-07-07
I'm a new emigree from Mac OS X to Hardy Heron. All my Mac files are backed up to an external hard drive, and I no longer have access to Mac OS X. How do I get these files on to Hardy Heron? I get a permissions error when I mount the hard drive and copy files in Ubuntu. Will I have to upload all my files to FTP using a borrowed Mac and download them to Ubuntu?

---

### Post by nikolaos on 2008-07-07
You can copy everything from Terminal!! 

```
cd /media
ls
```

find your hard drive. Enter and 

```
cp filename destination || cp -r directory destination 
```

then you can change the owner(in the new file which is in your hard drive) with chown

```
sudo chown user.user file
```

it is a little bit raw!!! But it works. Maybe a guru can give you a less complicated way of doing it

---

### Post by tati on 2008-07-07
I forgot to mention that I'm running Ubuntu on a PC, not a Mac. The files are on a Mac OS X hard drive, however.

---

### Post by tiresia on 2008-07-07
Have you tried to copy your files with "sudo cp filename&#8230;"?

---

### Post by kosumi68 on 2008-07-07
From the posts so far, it is not clear if

1. Your mac drive (HFS+ filesystem) is accessible from your PC somehow.

2. You have managed to connect to the drive (mount command in linux, often automatic when running ubuntu)

---

### Post by tati on 2008-07-07
I am able to mount my Mac hard drive on my PC that is running Ubuntu. It shows up on the desktop as soon as I turn it on. I am not able to move or copy files between the hard drive and PC due to a permissions error.

I'm not sure what format the Mac hard drive is; I presume it's whatever the default for Mac OS X is since these are my backed up files from my old iMac. I want to move these files (about 120GB of movies and music) to my Ubuntu PC.

---

### Post by flaggh on 2008-07-07
Since your ubuntu uid most likely is not the same as your mac uid, you'll either have to change your ubuntu uid to your mac uid if you want to continue to use these hard drives as is.  If all you're trying to do is copy the files to your ubuntu machine, I believe you should be able to just copy them as super user:

```
sudo cp /path/to/macdrives /home/user/newdirectory
```

---

### Post by tati on 2008-07-07
I'm able to copy files from my Mac hard drive to my Ubuntu desktop with that command but I still get the same error when I try to open the files:

> The folder contents could not be displayed

You do not have the permissions necessary to view the contents of "folder".

---

### Post by DonnieP on 2008-07-07
> **tati said:**
> I'm able to copy files from my Mac hard drive to my Ubuntu desktop with that command but I still get the same error when I try to open the files:
Use terminal to go to where the files are.  If they're on your desktop and your username is tati, there's only files and not directories, and there's nothing else on your desktop that's not "yours," then:

```
cd ~/Desktop
sudo chown tati.tati *
```

---

### Post by cyberdork33 on 2008-07-08
I think Donnie got it right. You get permissions errors because the files do not "belong to" your Ubuntu user, they belong to your OSX user. You have to change the permissions on the files to allow access by the new user. Since the old user no longer exists, you want to just change the ownership of the files to your new user. This can be done with the chown command as shown in the last post.

---

### Post by tati on 2008-07-10
Thanks to flaggh and DonnieP! These are the commands to copy files on a Mac hard drive to a PC running Ubuntu.

```
1. sudo cp -R /path/to/macdrives /home/user/newdirectory
2. cd ~/Desktop
3. sudo chown tati.tati *
```

---

### Post by tati on 2008-07-18
Unfortunately the laptop running Ubuntu does not have space for the 120GB of music and photos that I have on the Mac external hard drive. Is there an alternative to copying the files to my laptop and changing the owner using the previous instructions? When I try to run them on the hard drive, I get a "read-only file system" error in Terminal. I am also unable to change the permissions in Nautilus.

---

### Post by Washer on 2008-07-18
open a superuser view using "sudo nautilus" & use that for copying/moving whatever you want. Then run chown on the copied files.

I'm not familiar with that chown notation, I usually navigate to the folder {cd /path/to..} then {sudo chown tati *}. Sometimes I have to do */* etc for it to change deep into the folders.

---

### Post by cyberdork33 on 2008-07-18
> **Washer said:**
> I'm not familiar with that chown notation, I usually navigate to the folder {cd /path/to..} then {sudo chown tati *}. Sometimes I have to do */* etc for it to change deep into the folders.
the command posted changes the user and the group (both named tati).

Your HFS+ filesystem is mounted read-only. you have to disable journaling (in OS X) to get it writable under linux.
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by tati on 2008-07-19
I was able to borrow a friend's Mac and disable journaling (the non-destructive option) on my external hard drive. Thanks, cyberdork33.

---

### Post by gizzardjr on 2009-05-11
What if I don't have a friend with a macbook to disable journaling.   Then what?

---

### Post by zandrarogers on 2009-05-12
[LEFT]I installed Ubuntu in a VirtualBox machine on OS X (pretty easy and straightforward), but to access a Mac harddrive from Ubuntu was slightly more complicated.[/LEFT]

---

### Post by gizzardjr on 2009-05-12
> **zandrarogers said:**
> [LEFT]I installed Ubuntu in a VirtualBox machine on OS X (pretty easy and straightforward), but to access a Mac harddrive from Ubuntu was slightly more complicated.[/LEFT]



I'll give that a try!

Thanks

Otherwise I'm on the hunt for an exact mac model to just slap the HDD in and backup the data.

---

### Post by cyberdork33 on 2009-05-12
> **gizzardjr said:**
> Otherwise I'm on the hunt for an exact mac model to just slap the HDD in and backup the data.
? What are you trying to accomplish? you don't have to disable journalling just to copy files off the drive.

---

### Post by AndreaLynneHicks on 2009-10-13
> **kosumi68 said:**
> From the posts so far, it is not clear if

1. Your mac drive (HFS+ filesystem) is accessible from your PC somehow.

2. You have managed to connect to the drive (mount command in linux, often automatic when running ubuntu)


I am trying to do something similar - basically rescue files from a hard drive that wont boot (MacBook) using the Ubuntu Live CD - except in my case, the hard drive didn't just appear on the desktop. How do I mount it, or see if I can gain access to it (it may be completely fried...not sure at this point)? It doesn't appear in the Places tab on Desktop and no options appear when use ls in the /media directory from a terminal.

Any suggestions to figure out if the HD is accessible at all would be great...

---

### Post by oswaldkelso on 2009-10-14
This is from the archives so maybe old and out of date it relates to PPC.  ymmv.
 
[http://ubuntuforums.org/showthread.php?t=239370&](http://ubuntuforums.org/showthread.php?t=239370&)
[http://ubuntuforums.org/showthread.php?t=657225&](http://ubuntuforums.org/showthread.php?t=657225&)

---

### Post by ladysekhmetka on 2009-11-02
I'm having a similar problem.  I'm running on a laptop with Jaunty.

My old G4 iBook died a while back, and I was able to pull the hard drive out and put it in an external casing.  I want to pull all of my old files off of it, but as with everyone else, I couldn't because I didn't have permission.  I couldn't even see the files.

So I found this thread, reviewed, tried a few things, and now I can at least see each file, which I couldn't before.  I am doing this by putting "sudo nautilus" into terminal.  It popped open a window where I could see everything on this old iBook harddrive.

But I can't copy or paste; my computer still says that I don't have the permission to copy/paste these files.  I can even open some of these files (like the pictures or the rtfs) but it won't let me copy paste, which will be necessary for the files that are in an Apple format.

---

### Post by JordanL on 2010-09-17
1.Mount drive
2.Open terminal
3. type 'sudo nautilus' (this can break stuff so be careful)
Browse to drive.. you now have full permish to view/copy files.  (you may have to do this twice to have another sudo window open as the copy destination)
4. rejoice!

---

### Post by Meterman on 2011-05-06
Thanks everybody for all the tips. Ubuntu 10.10 just needed chmod 777 path..

Note that if you partition your USB drive with OS X disk utility (IE partition 1 is unjounaled HFS+, partition 2 fat32) the drive is flagged as journaled even if the HFSPlus partition on the drive is not journaled. This will cause the drive to mount as Read Only. The entire drive seems to be needed to be one partition of non-journaled. So repartition the drive as one unjournaled partition.

---

### Post by unagimiyagi on 2011-05-14
> **Meterman said:**
> Thanks everybody for all the tips. Ubuntu 10.10 just needed chmod 777 path..

Note that if you partition your USB drive with OS X disk utility (IE partition 1 is unjounaled HFS+, partition 2 fat32) the drive is flagged as journaled even if the HFSPlus partition on the drive is not journaled. This will cause the drive to mount as Read Only. The entire drive seems to be needed to be one partition of non-journaled. So repartition the drive as one unjournaled partition.


Hi, is there an easy way to mount my mac partition for read/write access in ubuntu 11?  Maybe a graphical manager?  Don't quite get the chmod and command-line based actions yet.  

Thanks!

---

### Post by ed bear on 2011-06-17
Here's a quirk: Last week, I ran into a corollary issue: while I have been able to read files from Mac external USB HDs, I found recently that I was unable to WRITE to any of the ones I tried!  The user number was 99, and since I know Mac OSX is in fact a Unix variant I tried creating a user with user number 99.  No luck - I could read files and open directories, and create directories, but not write to or copy files.  ???

Oddly, the new user never showed up in System>Administration>Users and Groups.  And despite my deleting the dummmy user's home directory, that user name still appears at time running processes... what the heck is user 99 in a standard install?

WAIT - THERE'S MORE: two days later, I passed a DOS-formatted USB memory dongle with some files on it to a guy sitting next to me on a Linux Mint (Ubuntu-derived) laptop.  And HE could read files and open directories, and create directories, but not write to or copy files!

In BOTH cases, the system insisted the USB drive was read-only.  Nothing I, my root or my root terminal - not my Mint friend's - would let us write to the external mac USB hard drive or DOS-formatted memory USB dongle could change this, and between us we must have at least two brain cells.  Remember - Mac is Unix with a lot of Big-Brother crap on top of it.  I suspect that, whatever this problem is, both these oddities are related...
ED BEAR

---

### Post by jtrag on 2011-08-19
> **ed bear said:**
> Here's a quirk: Last week, I ran into a corollary issue: while I have been able to read files from Mac external USB HDs, I found recently that I was unable to WRITE to any of the ones I tried!  The user number was 99, and since I know Mac OSX is in fact a Unix variant I tried creating a user with user number 99.  No luck - I could read files and open directories, and create directories, but not write to or copy files.  ???

Oddly, the new user never showed up in System>Administration>Users and Groups.  And despite my deleting the dummmy user's home directory, that user name still appears at time running processes... what the heck is user 99 in a standard install?

WAIT - THERE'S MORE: two days later, I passed a DOS-formatted USB memory dongle with some files on it to a guy sitting next to me on a Linux Mint (Ubuntu-derived) laptop.  And HE could read files and open directories, and create directories, but not write to or copy files!

In BOTH cases, the system insisted the USB drive was read-only.  Nothing I, my root or my root terminal - not my Mint friend's - would let us write to the external mac USB hard drive or DOS-formatted memory USB dongle could change this, and between us we must have at least two brain cells.  Remember - Mac is Unix with a lot of Big-Brother crap on top of it.  I suspect that, whatever this problem is, both these oddities are related...
ED BEAR

If the Mac Filesystem you are mounting in Linux is "Mac Journaled Filesystem" then it will only mount in Linux in "Read Only" mode.  The only way around this is to disable Journaling on the Mac Drive you're trying to write to in Linux and this must be done within Mac OS via Terminal/Terminal Commands.

I'm not sure of a way to disable Journaling on a Mac Drive from within Linux Unfortunately...

---

### Post by lolleepop on 2011-09-09
Could someone help me with file permissions? All I want to do, is to be able to read files from my OS X 10.7 partition (no write). More specifically I just want to be able to listen to my mp3s from my iTunes folder also in Ubuntu. Should I change file permissions in OS X? If yes, to what?

edit.


OK I solved the issue.

Here's what I did (for this to work I think user name and password need to be the same in OS X and Ubuntu):

1. Open terminal in Mac OS X and type
```
id
```

2. Take notice of what is your UID number (for me it was 501)

3. Boot into Ubuntu recovery mode from GRUB and change your UID
```
usermod -u TYPE_UID_NUMBER TYPE_USER_NAME
```

4. You need to reboot the computer, just type
```
reboot
```

5. That's it.

---

### Post by Piney on 2011-10-07
> **DonnieP said:**
> Use terminal to go to where the files are.  If they're on your desktop and your username is tati, there's only files and not directories, and there's nothing else on your desktop that's not "yours," then:

```
cd ~/Desktop
sudo chown tati.tati *
```

Iam trying to get data of a drive from a dead Macbook pro this resolution does not work. It keeps saying permission denied.

Any other Ideas?

---

### Post by pjoshyjosh on 2011-11-28
> **Piney said:**
> Iam trying to get data of a drive from a dead Macbook pro this resolution does not work. It keeps saying permission denied.

Any other Ideas?

I just got this to work today - not sure you are still looking for the solution?

I purchases/used a IDE/ATA/SATA to USB adapter to access the Macintosh HDD as a USB device.

Did have to use terminal.  And to copy files from Macintosh HD used command  
sudo cp -R /media/Macintosh\ HD/Users /home/(your folder/User ID)/destination

Once files are copied - then run command:
sudo chown -hR (your folder/UserID) /home/(your folder/User ID)/destination *

This changes all subfolders to have your UID as the new owner.

---

### Post by WarrenBowling300 on 2012-01-04
So after following this thread I successfully transferred all files onto a new hard drive.:D (Thanks to the 3 step terminal command provided) :D I did not want to run sudo nautilus and risk destructing the documents I need.:( But now that I have a copy of the whole hard drive I can mess with it and try whatever. I did run sudo chown WarrenBowling300.WarrenBowling300 * but everything it showing up as a blank text file. :confused:What do I do?

The directory to the file is (if it helps): Seagate/WarrenBowling300/Back-up/Backups.backupdb/(then various dates I backed up)

Thanks for the help

---

### Post by coffeecat on 2012-01-04
This is an old, old thread, started nearly 3½ years ago.

@WarrenBowling300, if you need help, please start a fresh thread, linking back to this one if necessary. You are more likely to get help with a new thread. 

Thread closed.

---

