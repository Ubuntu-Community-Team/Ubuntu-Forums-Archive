---
title: "Honest Honey! It wasn't me!!!"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-04-20
:rolleyes: 
OOPS!
I re-installed win XP in my wifes system, and tried every stinking thing I found to  get the ubuntu working on the dual boot system. I even loaded the Live CD and deleted the ubuntu partition. Then I tried to install ubuntu, and it won't go because it is finding 'old' ubuntu files, and won't overwrite them... What am I supposed to do? I have XP on hda1, a fat32 partition on hda2, with a partition for ubuntu, and a swap partition...  I just need to re-install ubuntu into the partition, and I can't...:confused:

---

### Post by cleverselfreferentialname on 2006-04-20
You can tell the Ubuntu install CD to format the partition beforehand.

---

### Post by htinn on 2006-04-20
If you are lucky, you may only need to do this:

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

I'm doubtful that you actually deleted the partition.

---

### Post by Mustard on 2006-04-20
If it's finding 'old files' then something mustn't have gone right when you deleted the ubuntu partition.  If the partition was deleted, then no files should exist.  The logical implication seems to be that the partition was not actually deleted.

The above suggestion, by cleverselfreferentialname,  sounds like a good one.  I take it you never got the hang of how to install grub from the previous thread we were discussing this in. :)

---

### Post by catlett on 2006-04-20
If the partition shows up on XP you can format it with windows. If it is there when you go to My Computer right click on it's icon and go to properties. It will give you a drop down box and one of the options will be to format the disk. Format it as Fat32 again and your partiton will be clear. Throw the install disk back in and you should be fine.

---

### Post by Papa-san on 2006-04-20
[QUOTE=Mustard]

The above suggestion, by cleverselfreferentialname,  sounds like a good one.  I take it you never got the hang of how to install grub from the previous thread we were discussing this in. :)[/QUOTE]

Hehehe... (grins sheepishly)   Ummm. no I didn't quite get it down...

I had to weed between several possible methods, and I guess the one I chose was not the right one! When I tried the next one, something was frogged!
But... she has her XP, and I have her info saved on the second drive in its own partition, so should eventually be recoverable!:rolleyes:

---

### Post by Papa-san on 2006-04-20
[QUOTE=catlett]If the partition shows up on XP you can format it with windows. If it is there when you go to My Computer right click on it's icon and go to properties. It will give you a drop down box and one of the options will be to format the disk. Format it as Fat32 again and your partiton will be clear. Throw the install disk back in and you should be fine.[/QUOTE]

XP is reading the ubnyu and swap partitions as 'Free space' This is selectable to format? When I do so, then ubuntu should install OK?

---

### Post by Papa-san on 2006-04-20
I'm not finding an option to use XP to format the 'free space'

---

### Post by catlett on 2006-04-20
I apologise I sent you the wrong way. You need to get into Disk Management. You do that by (in Windows) Start<Control Panel<Administrative Tools<Computer Management<Disk Management (and people say Linux is hard to get around). When you get there you will see your hard drive much like you see it with gparted. Right click on the secondary drive and a drop down box appears. It will have the option format. If format is not highlighted and delete partition is, delete and go back in and format. This should solve your problem. Formatting clears all data. Ubuntu should install like it did before.

---

### Post by Papa-san on 2006-04-20
As I sit here trying to decide how to re-install ubuntu (I don't have anything in the partition worth saving) I don't understand the partitioning menu. Why did it 'find' free space on my primary hard drive? That is where windos xp is...
I didn't save the changes, so hope it is ok... the menu choices are as clear as mud when I don't know what things mean...

---

### Post by Papa-san on 2006-04-20
Great...now I try to reboot into XP, and get grub error 22... That's it... Wheres windows?

---

### Post by catlett on 2006-04-20
The free space is the area in the windows partition with no data on it. You can have 20 gigabytes on your Windows partition but only 7 gigabytes have data on them. Therefore you have 13 gigabytes of free space. What Ubuntu will do is see how much of the partition Windows is using is free of space. It will then take some of that free space and make the partitons for Ubuntu. When you install it should give you a list of options during partitioning. If your drive already has a second partition that is where you want the Ubuntu install to be. If you only get the option to erase the drive and install choose manual partitioning. When you go there you should see the partition. Choose the option to use that partition for the install.
If the partition isn't there, and you only have the one Windows partiio, then choose the option to resize the drive. This is where it will say it foung free space. Put in 10gb if you have the space, if not you need at least 3gb. Then it will say it making the following changes. Say yes and sit back and let the install happen.

---

### Post by Papa-san on 2006-04-20
Anybody have a guess as to what happens when ya hand a loaded revolver to a monkey?!?](*,)

---

### Post by catlett on 2006-04-20
You now have a Grub problem. You can do 2 things that I know will work (there might be others but I never had luck with Grub editing).
Either put in the XP install disk and boot into recovery mode. When in recovery mode enter in the command line C:\ ```
fixmbr
``` This will get rid of grub and reinstall the windows boot manager.
The other option is to go forward with the Ubuntu install. Grub will be re-installed at the end of the process.

---

### Post by Mustard on 2006-04-20
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

---

### Post by Papa-san on 2006-04-20
OK   thanks! I'll try the format in windows

Naw...It wants to format the whole drive... The fat32 partition (9 gigs) is where I have all my saved information) The free space (20 gigs) is where I want a nice, fresh ubuntu...

(Most of XP is on my primary drive, which is all fat32) That's the first DNFW  the other is my secondary drive's 9 gig fat32 partition)

---

### Post by catlett on 2006-04-20
So you booted back into windows?
Isn't your hard drive partitioned from the previous install? The formatting I mentioned was for the partition that had Ubuntu but you deleted. I thought you were trying to install onto that drive but it was seeing old Ubuntu files. The disk manager would see that partition if it is there and only format that partiton. It would leave your windows partiton alone.
But it appears you want space from your windows partition.
You can install to the partition with windows but how is it seeing old Ubuntu files on the windows partiton?

---

### Post by Papa-san on 2006-04-21
This is what frustrates me so much about computers... The things that should make sense, just do not...
I have two hard drives: The first one is a 10 gig. It has one partition... all windows, and I want to keep it that way. The second hard drive is a 30 gig. It has about ten gigs partitioned for what I call 'Windows overflow'. This is a requirement, as my wife (Her system!) needs the space for her business information. (Currently, much of her vital information is zipped and sitting in that partition. I saved it to be able to re-install a messed up windows installation.. {It's own long story}) This re-install has happened, and the windows seems to be OK. 

Now, here is the other issue... I had ubuntu installed on the second hard drive. (The remaining 20 gigs was partitioned as such:
10 gigs for ubuntu.
1 gig for swap files 
9 gigs of free space.

It was a fresh install with nothing irreplacable contained in it. I attempted to fix grub, and blew it. so I deleted the ubuntu partition via the live cd. Then, upon attempting to re-install ubuntu, it didn't want to do it because it was finding pre-existing ubuntu files, and didn't want to overwrite them. I don't know why this happened... I can't explain why this is... it just is. Computers confuse me.

---

### Post by Mustard on 2006-04-21
I feel your pain, Papa-san. :)

I wish I had an answer really.  As you say, sometimes they just drive you nuts. :D  I think that's why when I have something set up the way I want it, I am very hesitant to change anything.  The process of tracking down the cause of obscure errors is tedious and demoralising at times.

My first speculation on what might have happened when you deleted the partition with gparted was that you had made the choice to delete the partition, which was then reflected in graphical view of the partitions shown in gparted, but might have forgotten to hit the 'commit' or 'apply' button, which would make the proposed changes permanent.  Not being there and sitting right in front of the screen, these lingering doubts about what actually happened are always going to be in the back of my mind. :)

---

### Post by Papa-san on 2006-04-21
Yeah, You're probably right. I'm not going to make a huge issue of it. I'll try to guage which partition is which based on size, and just re-partition with ubuntu disks. It may take some time, and some trial and error, but I should be able to hammer it out. I wish I took better notes when I mess with stuff like this, so I could track down where I went wrong.

Don't let it rent any space in your head! If I figure it out, I'll let you know what it was. I probably had some other program running in background that was keeping track of these partitions or something... Who knows! (Not I!) lol

---

