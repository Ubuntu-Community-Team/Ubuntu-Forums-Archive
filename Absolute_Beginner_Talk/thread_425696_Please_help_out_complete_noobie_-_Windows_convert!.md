---
title: "Please help out complete noobie - Windows convert!"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-04-27
Ok, please be gentle with me here! I am an absolute complete newbie, a "windows convert", if you will, & I am trying desparately to try to learn to get aroung in ubuntu (7.04), but failing at my attempts. 

Did a fair amount of searching, but all I am doing is ending up in endless threads & getting more confused than before. There is surely a wealth of information on here, but since I can't understand even "Linux 101", the most basic tasks are eluding me. 

I need a "beginners beginners" guide to start me off. For example, I don't even know where/how to type in "code" . *example* (sudo apt-get update
sudo apt-get dist-upg) That is completely foreign to me... where do I type that in at - the terminal? See, told you I am a completely lost newbie! 

But hey, we all have to start somewhere, & I am willing to take instruction & learn. 
 just need a bit of assistance to get "off & running", & from there I am sure things will get much easier.

A couple of pressing problems; 

1. I have XP on a partition, ubuntu on a part, swap, & storage. Someone told me that the mount point of sda2 be root. Instead, my storage volume is set to root. How do I change that?

2. Trying to read/write to the windows (NTFS) storage partition - was told to download & Install ntfs-3g and ntfs-config. Downloaded them, now what? No installer to run, as in windows, I am lost as for what to do next, How to install them?

3. How does one get permission to access the new volume/drives? 
I can't do anything with them, such as create folders, etc.

I am sure these are all very "noob" questions to you experienced linux users, but as I stated, I am at square one!

Thanks very much, discmaster :)

---

### Post by antoz on 2007-04-27
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

You can find all your answers in the above links.

---

### Post by supersonicdarky on 2007-04-27
terminal - look in applications or press alt-f2 and type **gnome-terminal**

1. (not smart enough to answer)
2. you could open synaptics manager, search for ntfs, select ntfs-3g and ntfs-config, click apply to install, then go to applications > system > ntfs config and click the appropriate checkbox
3. you have to do it in admin mode. (dont ask me how, because i use terminal for everything and there you just type **sudo** and the the command to run as admin)

---

### Post by tadcan on 2007-04-27
Here is some useful info 

[http://www.psychocats.net/](http://www.psychocats.net/)

You can also buy a book, do a search for ubuntu book in google. Haven't read it myself, anuy comments from people who have. The Ubuntu site has some tutorials, but the main documrntation is for the previous version. There is a wiki site as well. I have been reading the forums for the past week to learn what I can. Look for link at the bottom of some posts, some link to more detailed information.

---

### Post by bobplano on 2007-04-27
> **discmaster said:**
> 
I need a "beginners beginners" guide to start me off. For example, I don't even know where/how to type in "code" . *example* (sudo apt-get update
sudo apt-get dist-upg) That is completely foreign to me... where do I type that in at - the terminal? See, told you I am a completely lost newbie!
yes you put these lines in the terminal. it can be found under applications>accessories if you run ubuntu. for kubuntu i think the konsole is under system files 
> **discmaster said:**
> 
1. I have XP on a partition, ubuntu on a part, swap, & storage. Someone told me that the mount point of sda2 be root. Instead, my storage volume is set to root. How do I change that?
 what do you mean by storage? I'm not sure about the remounting, i know you need to use the live cd but thats about it from me. 
> **discmaster said:**
> 
2. Trying to read/write to the windows (NTFS) storage partition - was told to download & Install ntfs-3g and ntfs-config. Downloaded them, now what? No installer to run, as in windows, I am lost as for what to do next, How to install them?
 if you got it from the repositories (by way of synaptic, apt-get, aptitiude, or add/remove) then it's installed. ubuntu's "exes" are .deb files and the only other files you are going to download that don't automatically install are some kind of zip file(tar.gz or tar.bz2) or .rpm, but you need alien or something for .rpms
> **discmaster said:**
> 
3. How does one get permission to access the new volume/drives? 
I can't do anything with them, such as create folders, etc.


sudo allows to to get access to mostly anything. read this [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by discmaster on 2007-04-27
Thanks to all for taking the time to answer! I will go over the links & the suggestions carefully, & try to apply the knowledge. Being a windows user for many years, I can glide around that OS with ease, but as you can tell, I am in unfamiliar territory here! (But I'm trying)

Thanks again! :)

---

### Post by thegreenman on 2007-04-27
Hey discmaster we're all in this together. One day we learn and the next we teach. 

I believe you will have to reinstall ubuntu to change the root/home/etc... partitions. 

Just be very careful which partitions get formatted.....

---

### Post by psionyk on 2007-04-27
> **discmaster said:**
> 1. I have XP on a partition, ubuntu on a part, swap, & storage. Someone told me that the mount point of sda2 be root. Instead, my storage volume is set to root. How do I change that?

By this do you mean that root ( / ) is mounted to the partition that you wanted to use as your storage instead?

---

### Post by discmaster on 2007-04-27
Ok, here is what I have (confused)

At Places/Computer; 24.4 GB Volume sda1 This drive says "root" under owner, in the properties/permissions tabs. This is my win xp partition. 
Next I have "New Volume", the data partition 191 gb, says "unknown" under owner.

Last is the drive partition which has ubuntu installed on it. This one is named "Filesystem", & says unknown under owner in the permissions tab. I hope that isn't too confusing!

Also, the "Filesystem" drive is not shown on the desktop with the others, should it be?

---

### Post by jerrylamos on 2007-04-27
There's lots of good stuff in "The Official Ubuntu Book" ISBN 0-13-243594-2 from Barns & Noble or Amazon (cheaper) or Borders ...  I'd suggest any newbie get one.  The troubleshooting section is good.

Cheers, Jerry

---

### Post by AAM on 2007-04-27
g'day discmaster!

Am I right in thinking that you have an Ubuntu Feisty LiveCD disk and a PC which has already been partitioned into 2 partitions (one windows, one ubuntu)?

Are you on the net with a different computer or are you flicking between Windows (for internet access) and the Ubuntu install (trying to fix one step at a time)?

---

### Post by discmaster on 2007-04-27
Partitioned 250 gb drive;

25 - win xp
15 -  linux 
3 - linux swap
191 data (NTFS) partition

ubuntu is installed, I am on the net w/ it, haven't been back to windows for a day or so. 

Problem is, since the terminology is all new to me, I don't know if I have it installed correctly, what to do next, etc... The prev. posters have included some good links, I will go thru them to try to get a feel for what is going on.

I don't want to go too far on installing pgms., etc., until I am certain that I have the install right.

---

### Post by bobplano on 2007-04-27
it seems you have it right, but you don't have a /home partition which can make updating from a cd a pain, if not impossible to keep all your data without backing up the info. you can probably get gparted and make a home. just make sure to mount it to /home

---

### Post by AAM on 2007-04-27
that news about using Ubuntu on the net already is good. 

I'll tell you what you should end up with and you can decide if you go back and re-install or move on from where you are. The linux partition is a good size and the swap is also a good size, but your home directory is currently sitting in the linux partition. You want it out of there because when you re-install (with the Gibbon 7.10 version in 6 months?) you will lose your home directory in the over-write. You need to decide on what you are going to do with the 191G unassigned partition - keep some for future Windows data, or all for Ubuntu?

At the end you should have:
linux (15G)      called "/"
swap (3G)       called "swap"
home (191G?) called "/home"

any thoughts?

---

### Post by discmaster on 2007-04-27
> The linux partition is a good size and the swap is also a good size, but your home directory is currently sitting in the linux partition. You want it out of there What do I need to do? How do I fix?

At the end you should have:
linux (15G) called "/"
swap (3G) called "swap"
home (191G?) called "/home"

As far as the 191G, I guess I will part. it a bit farther for audio/video editing, & it will be accessible from both XP & linux. It is already formatted NTFS.

 

any thoughts?

---

### Post by AAM on 2007-04-27
I would suggest that for now you set this up:

linux (15G) called "/"
swap (3G) called "swap"
home (90G) called "/home"
winXP (25G) (Drive C:\?)
NTFS partition (100G) (Drive D:\?)
That way you will be OK for the foreseeable future.

With respect to the first question, if the net access was easy to set up, then re-install the OS again paying attention to the partitioning part and making sure that you have the 3 linux partitions set up and named properly. In the PartitionManager, you will keep the 15G partition and call it "/" (no inverted commas though!) and reformat it, keep the swap, and take another 90G out of the 191G partition, and call it "/home".

As a side issue, Ubuntu will allow you to access (read and write) to the NTFS partition, so whatever you have there is available from Linux (not the other way though).

How does that sound?

---

### Post by discmaster on 2007-04-27
I have the live cd, thought I would reinstall again using the method outlined in this [link.]("http://www.psychocats.net/ubuntu/installing")

> linux (15G) called "/"
swap (3G) called "swap"
home (90G) called "/home"
winXP (25G) (Drive C:\?)
NTFS partition (100G) (Drive D:\?)

I would say that looks good. Do I delete all partitions & start from scratch? Do I delete them when running the live cd, or at another time? Gosh, I must sound sooooo noobish here! :redface:

---

### Post by AAM on 2007-04-27
the link you posted uses the LiveCD.

the bit that is important is that you choose the "Manually edit partition table" option, when the view appears called "Prepare partitions" reduce the size of the NTFS partition and then assign the part that becomes orphaned to a linux filesystem (ext3 or reiserfs is OK).

Just so you don't get too disturbed, the link has images from earlier Ubuntu LiveCDs, so don't be phased if the screen views are slightly different.

So, if you are going to go ahead now, put the LiveCD into the drive and reboot and re-install. The idea to remove all the linux partitions, reduce the NTFS to 100 and then start again sounds OK too. Feeling confident?

---

### Post by discmaster on 2007-04-27
Thanks for the lead, AAM! Surely appreciate you taking the time to walk thru this with me. As you mentioned, I want to have everything set up properly first before I go mucking around adding pgms., etc. 

However, I must bow out for now & call it a night; Up for work early in the a.m., & I'm up past my bedtime already! I will do this tomorrow & post back with the results!

Cheers, discmaster :-)

---

### Post by Rotaj on 2007-04-27
[http://ebookspyder.net/index.php/200...nux-bible.html]("http://ebookspyder.net/index.php/200...nux-bible.html")

This is a free resource andI hope you will find this helpful.

P.S. The password for the zip file is ebookspyder.net

---

### Post by discmaster on 2007-04-28
ok, working from post #16 here; but I goofed already - I deleted all the partitions except the xp part., thinking that I had to start over with all new parts. I am at the "prepare partitions" screen now, ready to create  new partitions in the free space. 

what type? Primary - logical? location beginning-end? use as? (ext3, I assume?

thanks all :)

---

### Post by discmaster on 2007-04-28
Update - 

to make it easy (that I could follow) I ran GParted & took care of the partitions from there. For me, it seems more easy to do that way. Anyway, back up & running - all looks good! Thanks to all for the good information.

cheers, discmaster :)

---

### Post by psionyk on 2007-04-28
Glad to hear that you were able to get things set up... hope you're enjoying yourself in Ubuntu!

I swear by gparted, I always use it to set up all partitions ahead of time for any distro I install, since I use multiple partitions for each of my installs, such as /boot, / , /var, /tmp, /home, /usr.  It's not necessary to do it that way, but I prefer having things organized and separated out, and it allows for additional security over just having everything under the / partition.  

Let us know if you need any other help! :)

---

### Post by AAM on 2007-04-29
good to hear that the problems have been solved. I have found many frustrations in learning to use linux, but also a profound sense of achievement in finally getting it right. I just love going to the local LUG and actually understanding what they are going on about. Increasingly I am finding that I now have answers for others - which is also a warm fuzzy feeling!

---

### Post by discmaster on 2007-04-29
@psionyk > I prefer having things organized and separated out, and it allows for additional security over just having everything under the / partition. Makes good sense, security wise :) Similar to having windows on a small part., with data on other (protected) partitions.

@AAM > Increasingly I am finding that I now have answers for others - which is also a warm fuzzy feeling! :)

Being immersed in a windows environment for so long has dulled my "command line" skills, but I am learning new things about how to use the terminal.

Not really as hard as it seems, once you get a few of the basics down. :)

---

### Post by psionyk on 2007-04-29
> **discmaster said:**
> Makes good sense, security wise :) Similar to having windows on a small part., with data on other (protected) partitions.

Funny you mention that, as I don't even have a seperate data partition for my Windows installation, but seeing as I'm only using it for games now, it's not a big deal.  Beyond just having a separate isolated (and therefore "protected") partition for data, the security options go far beyond that.

For example, the /var and /tmp directories are where log files and temp files are written in Linux respectively, so it makes sense to keep them on a separate partition in the event that an errant process starts writing to a lot of log files, and same for something writing a lot of data into the temp directory.  If these directories were contained under your root directory, and they started to clog up, they could end up filling up all the space in root, which would bring your system to a quick halt.  Having a separate /tmp also allows you to mount that directory with the 'noexec' flag in your fstab.  Since any user can access the /tmp folder, if a cracker was able to infiltrate your system and plant an executable in /tmp, they could then run that file, but the noexec mount option prevents anything from being executed from temp.  

You can even go as far as using different filesystems that would be better suited for the types of files that are being stored on each of these separate partitions, such as XFS on a video/music data partition, since that FS handles large files very well, or ReiserFS for /var since it would fly through all of the small log files in that folder.

Lots of great information that you can find if you google for "linux partitions" and something to consider down the road if you want to reinstall and customize a little more.

---

### Post by Happy_Man on 2007-04-29
Incidentally, while everyone's here.... how do you create a logical partition manually using Gparted? I've always wanted to do that, (I reinstall often), but nowhere in GParted can I find a way. It's been bugging me, but I decided to ask here. Any ideas?

---

### Post by psionyk on 2007-04-29
> **Happy_Man said:**
> Incidentally, while everyone's here.... how do you create a logical partition manually using Gparted? I've always wanted to do that, (I reinstall often), but nowhere in GParted can I find a way. It's been bugging me, but I decided to ask here. Any ideas?

Great question, and it's very easy to do.  The type of partition that Windows requires is a primary partition, but if you need a lot of partitions on your hard drive, primary is not useful, as you can only have a maximum of 4 on a drive.  However, Linux does not care what partition type it is, so logical works very well since you can create a lot more of them on your disk.

You have to start by creating an 'Extended partition', which is essentially like the drawer of a filing cabinet.  The extended partition does not itself hold any data, but rather is a place where you insert invidiual folders (or partitions in this case) and those partitions that you create inside the extended partition are called logical.

Let's say you were setting up a dual-boot, and you had your windows partition taking up half your hard drive, and the other half you have empty for Linux.  Using gparted, you would first create an extended partition using up all of the free space on your disk.  Then, inside that extended partition, you would create whatever/how many new partitions you needed (i.e. /home, / , /boot, etc.) and when you are editing each partition, you would select the 'logical' type.

If you decide to run multiple Linux distros like I do, you can create several extended partitions for each individual distro, and then make the logical partitions for each distro as above.  That way, each distro is it's own contained "drawer" in your file cabinet, and if you choose to delete one and reinstall something else, all you need to do is delete the logical partitions inside the extended block, and then set up the new ones, while leaving your other OS's completely untouched!  Works beautifully! :)

---

### Post by Happy_Man on 2007-04-29
Oh sorry, maybe I wasn't clear... I can't find a way to MAKE an extended partition using Gparted, that's what I need help with...

---

### Post by psionyk on 2007-04-29
My bad, I explained how to make the logical but not the extended... ;-)

Assuming my previous example, and you are looking to use any free space on your drive for the extended partition, all you have to do is select the free space in your hard drive layout, and then pick "New" to create a partition.  From there, when the dialog comes up with the options, under type you would select Extended, and then you would apply that change.  That creates the extended partition on the drive, and then you can select that Extended partition and fill it with your logical partitions from there.  

Hope this makes sense!

---

### Post by Soccrmastr on 2007-04-29
read the whole ubuntu desktop guide thats provided byd efault in Ubuntu. It helps you get all the basics down.

---

### Post by Happy_Man on 2007-04-29
> **psionyk said:**
> My bad, I explained how to make the logical but not the extended... ;-)

Assuming my previous example, and you are looking to use any free space on your drive for the extended partition, all you have to do is select the free space in your hard drive layout, and then pick "New" to create a partition.  From there, when the dialog comes up with the options, under type you would select Extended, and then you would apply that change.  That creates the extended partition on the drive, and then you can select that Extended partition and fill it with your logical partitions from there.  

Hope this makes sense!
Ummm.... it won't give me that option. I started GParted like you said, but the choice to make an extended is grayed out. I do have another extended, though, that Ubuntu automade for swap. Perhaps that's why?

---

