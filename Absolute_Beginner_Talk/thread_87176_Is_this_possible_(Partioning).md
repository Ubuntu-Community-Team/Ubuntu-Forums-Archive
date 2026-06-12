---
title: "Is this possible? (Partioning)"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Pedricko on 2005-11-07
I currently have a (slightly corrupted) Ubuntu Badger install (Corrupt by my own fault, sorry codies :P) and I was wondering if I could do a partition transfer.

For example.

I have alias'd my 100+ contacts on GAIM and wont want to do it again on a new transfer.

I have a lot of music I dont want to use CDs to transfer.

And a few other bits and bobs like that.

Would it be possible to make a new partition and install, transfer over the data, and delete the old, corrupt, partition?

Where does GAIM keep its alias settings?

---

### Post by tonysathre on 2005-11-07
during the install there is an option to copy from another partition, during the partitioning , i think that is what u need

---

### Post by spizkapa on 2005-11-07
Or you could make a new partition somewhere on your disk and copy all the stuff you need to it. If the disk is full, you may need to remove/resize some partitions. Since you're reinstalling anyway, borking the system shouldn't be an issue... When you reinstall, use that partition as something like /usr/local or /download or something. Mount it but don't format it or don't mount it at all. When you're up and running, you can just copy the useful informarion across.

---

### Post by Who on 2005-11-07
If I understand you correctly, what you want to do is create a new partition in order to keep all the files that aren't corrupted and that you don't want to loose on, and then reinstall the system... Is this right - cos it is possible? 
{Though it's too late now, it may be useful for the future for you to know that many people like to keep their '/home' and their '/' on separate partitions, so that they can update system files without losing their personal files.}

Gaim's info, along with all the user information stored by other apps will be in hidden folders in your home directory (all files beginning with a '.' are hidden on Linux (There is an option in the Nautilus 'View' Menu to enable showing hidden files)). For gaim try /home/[your username]/.gaim.

As far as creating a new partiton for yourself and then copying things over goes - yes - that should be fine. You would need to create a partition, copy the files to it, then reinstall Ubuntu choosing the 'Custom Disk Partitioning' option (Choosing during the installation to mount your newly creadted partition somewhere, we will say '/backup' for now) . What _I would do_  in the custom partitioning program is create a partition for '/'  (minimum 5GB, safe minimum 8GB) and another one for '/home' (Both ext3). Finish the installation, boot the new Ubuntu and copy all the files back over from /backup to (the new) /home.

Now, I am not able to see an Ubuntu Installer at the moment, but it -may- be possible to create a new ext3 partition (on the corrupted Ubuntu, or using a LiveCD - I recomend 'gparted' as a nice graphical app to do this), and then copy the contents of '/home' on the current ubuntu system to this new partition (as before). (Now here is the clever bit that may not be possible) When doing the Ubuntu installation I think it is possible to mount a disk as /home without formating it, thus all your settings and personal files (Or everything in /home, anyway) will be kept). before you attempt to do this wait for someone else on the forum to confirm whether or not you can do this - I don't know whether the installer will just delete all of the current /home partition to make way for the new one (Not formating it...). For this to work you would have to create a user wth the same name and probably password - and even then, again, you should wait for someone to confirm this will work...

Now - the reason I bother to suggest the second one is that it doesn't leave you with a spare partition the size of all this music, that you may not want (on the other hand, if you are regularly corrupting disks than a partition at /backup wouldn't be a bad idea :P)

Hope that helps

{In case you are very new to Ubunut, or someone very new is reading this a bit confused, in Linux you can mount any partition to pretty much anywhere on teh file system - it becomes a subfolder of the root partition, such as /home - which is very powerful, but also quite confusing if you are new. What you would probably call 'mapping' a drive to a particular location on the root ('/') filesystem is called mounting a disk. if you want to have a look at how this works try opening the file /etc/fstab in a NON ROOT/NON SUPERUSER text editor.}

Who

---

### Post by Pedricko on 2005-11-07
Thanks alot, Who.

I'm not that much of a newbie, I just didnt know which forum to put this in. 

I would rate myself at 'Novice' right now, I can use linux fine, im just digging into what makes it work :P

You covered everything I needed to know, and I will download a new ISO image during the day tommorow while I'm at school, and do it in the afternoon when I get home, Or I may choose to do it all tonight, I'll post about how I did it later.

[Edit] Incase you wanted to know, I messed it up trying to configure a user account to run 'kiosk' style, so my basically computer illiterate mother could use it. I don't want to go thru the pain of showing her how to use it!

---

