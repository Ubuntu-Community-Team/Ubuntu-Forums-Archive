---
title: "Allocate drive space by dragging the divider below"
date: 2011-07-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jiri2 on 2011-07-28
Hi,
My first impression of Ubuntu can't be very good when I can't understand this. It's under 'Install Ubuntu alongside Windows 7'.

It just doesn't make any sense, guys.

One side of this 'drive' space is 'Files (3.2gb) /dev/sdb2 (ntfs). The other side says 'Ubuntu /dev/sdb3 (ext4)

Under each of the options it says 125.0 GB!!!

Are the files the ones extracted and consisting of Ubuntu? If so, why are they separate from the 'Ubuntu' to its right? Why would these 'files' take the place Ubuntu does not and vice versa?

I'm not going to go forward because god knows what could happen.

---

### Post by jiri2 on 2011-07-29
Sorry for the BUMP, or for sounding arrogant in the thread. But I really wanna know what each part of the installation screenshot I described is saying.

---

### Post by WinterMadness on 2011-07-29
the ntfs drive is not ubuntu, it looks like its your windows drive.

to put it simply, ubuntu is going to install its self along side windows so that you can choose one or the other when you first start your computer. In order to do this, it has to resize the amount of space windows takes up so that it has room as well.

i would make sure windows has more than 3.2 gigs, drag the divider thing to give it at least 15-20 gigs id say.

---

### Post by grahammechanical on 2011-07-29
First, a screen shot would be nice. Then we can see what you are seeing.

Second, sdb tells me that that is a second hard drive that you are looking at.

Third, ntfs is a Windows format. So, the 3.2GB of files are most probably something to do with a Windows Installation or part of some files that you have backed up you another drive/partition.

I am guessing. Is this second hard disc 250GB in size. Then it would be my guess that when you selected Install Ubuntu Alongside Windows 7, the installer then gave you its recommendation to partition this 250GB drive in a way that would create two 125GB partitions. One of which would be a NTFS partition that had the label Files (of which there were 3.2GB). The other would be formatted with the Linux ext4 format and into which Ubuntu would be (with your agreement) installed.

This is just my guess.

Regards.

---

### Post by jiri2 on 2011-07-29
I think my confusion rises from the fact there are a number of hard drives in my laptop and I just dunno which one Ubuntu is referring to.

Also from the fact that in the main hard drive, most of it was covered by files inside of the Win7 OS, so i'm worried about this partition drilling through my previous OS's space.

Maybe one of the hard drives was completely empty, that would explain the 250gb symmetry there. Ubuntu says two 250Gb Filesystems exist, I dont know what it means by that. Is it referring to my extra hard drives?

To make matters more confusing, I'm not sure if i actually had two or three extra hard drives. If i had three, and one was moderately filled with stuff, that might explain why there are only 'two filesystems'.

I guess, I can ask you guys if i install ubuntu in one of these filesystems, as they're for the most part empty, will they:

be a separate hard drive and not under risk of being erased by the new factory install of Win7 because they're on a separate hard drive?

Ditto for if it installs and is referring to being in another partition instead of hard drive?

I'm looking to minimize risk in dragging my old OS's files to this new OS. 

If Ubuntu says there are 3.32 gb of files of my old OS, then it just worries me because I don't know what it's talking about. 

For example, 'alongside my Win7', and yet I only consider, or am only supposed to consider the main hard drive as the master hard drive. There I can assure there were not only 3.32 gb of files but a lot more.

To make matters worse, i'm not 100% positive there were different hard drives in this pc. All i remember is there were different drives and lots of empty space in these HDs or partitions, that I wasnt using. 

Am i supposed to guess how much space my previous Win7 was holding so the new Ubuntu doesn't eat anything up? Or is the install manager being intelligent and installing itself in one of these hopefully slave hard drives?

I wouldnt want to erase anything of the old OS, and at the same time want lots of space in my new Ubuntu to drag the old files into it. How to be positive, though that the new Ubuntu is being installed in one of the most empty hard drives/partitions or whatever they were, and not that it's going to enter a fight with Win7 for space and eat up my files?!

Any thoughts, guys? thanks

---

### Post by psusi on 2011-07-29
You almost certainly only have one hard drive.  It is very rare for a laptop to have more than one, and the installer won't give you the automatic side by side option if you do.

As for the meaning of the divider, it is pretty clear:  you drag it back and forth to choose how large each of the two partitions should be, the left one being windows, and the right one being ubuntu.

---

### Post by ajgreeny on 2011-07-29
There are two main ways you can help us here:-

1.  Run the live ubuntu cd and go to System->Administration->Gparted (if it's 11.04 you will have to find gparted yourself, as I have no idea how you start it).  Now go to each disk, sda, sdb, sdc, etc etc in the drop down menu, top right, and get a screenshot of each disk which you can save to the live session and then paste as attachments to your answer back here.

2.  Again using the live CD run the command in terminal ```
sudo fdisk -l
```(lower case L at the end) and report the output back here.

Once we have that info it will be a lot easier to help, but there are a few comments I will make without waiting for that, as I think they are important.

Firstly I strongly recommend that you shrink your Win7 partition using its own disk management utility, not the Ubuntu installation program, and not gparted;  it is much safer that way.

Once we have got to the information on the current partition arrangement, and you have shrunk Win7, I would also strongly recommend that you make partitions using gparted, in the free space from the Win7 shrinking, into which you can install Ubuntu by using the "Something Else" ie, manual partitioning, choice at disk preparation stage.

However, let's see that information on your current disk setup before we go any further.

---

### Post by jiri2 on 2011-07-29
> **ajgreeny said:**
> There are two main ways you can help us here:-

1.  Run the live ubuntu cd and go to System->Administration->Gparted (if it's 11.04 you will have to find gparted yourself, as I have no idea how you start it).  Now go to each disk, sda, sdb, sdc, etc etc in the drop down menu, top right, and get a screenshot of each disk which you can save to the live session and then paste as attachments to your answer back here.

2.  Again using the live CD run the command in terminal ```
sudo fdisk -l
```(lower case L at the end) and report the output back here.

Once we have that info it will be a lot easier to help, but there are a few comments I will make without waiting for that, as I think they are important.

Firstly I strongly recommend that you shrink your Win7 partition using its own disk management utility, not the Ubuntu installation program, and not gparted;  it is much safer that way.

Once we have got to the information on the current partition arrangement, and you have shrunk Win7, I would also strongly recommend that you make partitions using gparted, in the free space from the Win7 shrinking, into which you can install Ubuntu by using the "Something Else" ie, manual partitioning, choice at disk preparation stage.

However, let's see that information on your current disk setup before we go any further.


Thanks a lot for the help.

I finally managed to get internet working on ubuntu, it was extremely simple, i dunno what i-d  been thinking. Ok here-s 1 in attachments

for 2, if you could plz explain to me what -in terminal- means, where i should be running the command in.

---

### Post by ajgreeny on 2011-07-30
Terminal is in Applications->Accessories->Terminal, and you just open that and type in the command I gave and press return, then type your password (nothing will show on screen, but the system will accept it), and the putput will show all partitions on the disks, though we now can see them all from gparted.  It may still help to have that output, so go ahead and do it please.

You have two disks, sda which has windows OS on it, I assume, of 116.44GB with the boot flag needed by windows, and an extended ntfs data partition.  There is also a Recovery partition at the front of the disk, and a small ignorable unallocated space at the end.

The second disk, sdb has two identical sized partitions of 232.88GB, both possibly unused at present, apart from a usual tiny amount of system space shown as used.  This is definitely not Ubuntu, as both partitions are ntfs.

In your original post you said:-
> It just doesn't make any sense, guys.

One side of this 'drive' space is 'Files (3.2gb) /dev/sdb2 (ntfs). The other side says 'Ubuntu /dev/sdb3 (ext4)

Under each of the options it says 125.0 GB!!!Where did that information come from?  I don't see where you got the "Files (3.2gb)", and you do not have an sdb3 at all as an ext4 partition, so you certainly don't have Ubuntu installed anywhere at the moment, and I a wondering if you have simply been running it as a live CD/USB version.

Much more clarification and info needed in order to take this further, please.

---

### Post by jiri2 on 2011-07-30
> **ajgreeny said:**
> 

In your original post you said:-
Where did that information come from?  I don't see where you got the "Files (3.2gb)", and you do not have an sdb3 at all as an ext4 partition, so you certainly don't have Ubuntu installed anywhere at the moment, and I a wondering if you have simply been running it as a live CD/USB version.

Much more clarification and info needed in order to take this further, please.


[This]("http://ubuntuforums.org/attachment.php?attachmentid=198897&stc=1&d=1312065898") comes up when I try to install Ubuntu on the hard drive. You're right in that I dont yet have Ubuntu installed, but that's because I don't know where to install it as I'm confused with all this talk about partitions, it's gotten me to think I could accidently wipe out my Win7. In the above picture, for instance, I can drag the size of each of the two whatever they are in either direction, but I wouldnt know what I'm doing. I think this is why I'm still at a loss as to what to do exactly.

[This]("http://ubuntuforums.org/attachment.php?attachmentid=198896&stc=1&d=1312065898") comes up when I do the sudo fdisk -l in the terminal as you told me to.

I'm not sure how I could go about shrinking win7 with the Windows7 shrinking utility because I cant even boot it in safe mode, as you tell me not to use gparted or the Ubuntu shrinker for this.

Is there any other way I can help you to help me?

---

### Post by ajgreeny on 2011-07-31
For safety's sake, and as I have not used the "Install alongside" option for several years, I suggest you stop the installation, and go back to the desktop of the live CD.   Using that, check what the files are in the 3.2GB of files on sdb1,  (at least I think it is sdb1, as there is a difference in what the installer says and what fdisk says).  However, check any files that show in both partitions currently on sdb and backup any important files, if you recognise them to a usb flash drive.

Having done that, open gparted from the System->Administration menu, and delete both partitions on sdb.  Make sure you get sdb from the drop down menu top right and do not delete any on sda, or your windows may be gone.

Now go back to the installation, and when you get to the disk preparation (partitioning) stage, choose "Something Else", ie manual partitioning, usually the third option, I think.

Now sdb will show as 500GB unallocated.  Using all that space make an extended partition of the full 500GB, as Linux is quite happy to have the OS in a logical partition, unlike windows.  That will show as sdb1.  Now within that partition you need to make a new logical ext4 partition of about 10 -15GB with mountpoint /, (root), a swap partition of 2 -4GB with no mountpoint, and a separate partition of perhaps another 10GB ext4, with mountpoint /home.  All the remaining space can be made into a new logical partition for data, formatted as ntfs, which can be shared between ubuntu and windows.  At this stage do not give it a mountpoint;  we can deal with that later after installation.  You should now have potentially the following partitions ready to be made:-

sdb1   extended 500GB.
    sdb5   logical  ext4  10-15GB  mountpoint /.
    sdb6   logical  swap  2-4GB.
    sdb7   logical  ext4  10GB  mountpoint /home.
    sdb8   logical  ntfs  all remaining space about 470GB for data, no mountpoint.

If all is well go ahead and install.  Along the way you will be asked for username and password, your timezone etc etc which should all be very obvious to answer, and at the end you will be asked to reboot.  Do so!

That should be it apart from the large shared ntfs partition, but let's get this bit done first and then later you can come back and we'll sort out mounting the ntfs partition at boot time, though if you want to have a stab at getting it going, just install the package **ntfs-config** after installation, and it should be very easy to run that and set up everything.

Good luck.  It may all sound very difficult and intimidating but once you have done it the first time, it is very easy to do again when needed.

PS:
I've just noticed that you say you can not boot into Win7 even in safe mode.  Is this after trying to shrink your windows partitions with gparted, or was this the case even before this ubuntu saga began?  If you have a Win7 install DVD disk it may be worth trying to get windows running properly first.

I'm afraid that not having windows in the house, I can't really help on that.

---

### Post by jiri2 on 2011-08-03
Hi ajgreeny,
Thanks a lot for your help on this matter. Unfortunately I've had to park this project for some time because my hands are tied 24/7. I transfered my files to another PC and gave up on learning to save the registry to save the installed programs this time. However, having a second OS set up and knowing where to install and the partitions is something im interested and will bookmark this page for the future. Maybe a week, but maybe a month. thanks, again.

---

### Post by sea-geek on 2012-05-30
> **psusi said:**
> You almost certainly only have one hard drive.  It is very rare for a laptop to have more than one, and the installer won't give you the automatic side by side option if you do.

As for the meaning of the divider, it is pretty clear:  you drag it back and forth to choose how large each of the two partitions should be, the left one being windows, and the right one being ubuntu.

I understood what it was for but this answer was most helpful to me as I couldn't figure out which side was supposed to indicate Windoze and which side was Ubuntu!

---

