---
title: "[SOLVED] Low disk space problem"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by HareBall on 2007-10-08
I keep getting low disk space messages. I ahve done a search and didn't come up with an answer to this.
I know I have disk space, but how do I view how much I have in each partition?  I have a separate drive for windows and Ubuntu. They are each 160 Gb. I am trying to free up space in my home partition by moving my music and other space eating things to another partition.
I may just have to burn my music to some DVD's, but that would make it annoying every time I wanted to listen to something:(

---

### Post by Dr Small on 2007-10-08
Did you check and see how much disk space you actually have,  by looking in Gparted ?

---

### Post by HareBall on 2007-10-08
> **Dr Small said:**
> Did you check and see how much disk space you actually have,  by looking in Gparted ?
Here is what I get when I check. How do I change /dev/sdb3 and add it to /dev/sdb1?

---

### Post by e_james on 2007-10-08
Your Gparted display is a little strange. You seem to have your largest partition mounted as "/" and the smaller partition (almost filled) seems to have no mount point but, from your comments above, I think this is "/home".

Before you make any changes I suggest you have a look at these links
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)
[http://linuxplanet.com/linuxplanet/tutorials/3174/5/](http://linuxplanet.com/linuxplanet/tutorials/3174/5/)

If you choose to split up a large drive like 160GB, it is common to allocate about 10-20GB for "/" and a large partition for "/home" which is the one most likely to fill up rapidly. As suggested in the first link, if you have a large collection of data files such as music, it may be an advantage to make a special large partition for these e.g. "/data". A similar argument can be made for splitting a Windows system into 2 or more partitions e.g. 30GB for system (C:\), 30GB for "My Documents" and 100GB for special data. A quicker way than Gparted to get a view of your disc usage is available from System - Administration - System Monitor. You might have to install it first.

In principle you can use Gparted to resize your two main partitions; shrink one and expand the other. I am not sufficiently knowledgeable about linux to say for sure that resizing the "/" mount point will not corrupt your ubuntu installation. you may find that Gparted refuses to resize the partitions. Apparently this depends on the drivers installed with the underlying linux distro. It may be an advantage to use the Gparted CD. If the newest version won't boot properly, try this one "gparted-livecd-0.3.4-2.iso". It uses a different boot process (I think).

---

### Post by HareBall on 2007-10-09
> **e_james said:**
> Your Gparted display is a little strange. You seem to have your largest partition mounted as "/" and the smaller partition (almost filled) seems to have no mount point but, from your comments above, I think this is "/home"..Yes, that is /home. When I partitioned the drive I obviously didn't know what I was doing. Now I need the space and don't seem to have access to it. I would like to swap the sizes of these 2 partitions. I will read the stuff on the two links you gave me and see what I can figure out.
Any other help would be appreciated.
Thanx

---

### Post by e_james on 2007-10-09
Just a few additional comments at this stage. You need to ask yourself some key questions and be comfortable with the answers.

1. What partitions do you want and why?
2. What sizes should these partitions be and why?
3. How important is the data currently stored on the drive?

Depending on the answers, the next question is how to adjust the partitions to what you want. If you have access to an external drive with at least 50GB of spare capacity, there are more options and less risk of losing important data.

For myself, I have resized Windows partitions on about 10 occasions in order to instal linux (mostly ubuntu). Once or twice I have made small adjustments to linux partitions but all my linux installations are experimental and I don't mind reinstalling. On the most recent occasion Windows XP didn't like what I had done but I was able to change the plan and fix the problem. It helped that I had a backup image of the Windows C drive. That's where the external drive is useful.

---

### Post by HareBall on 2007-10-09
> **e_james said:**
> Just a few additional comments at this stage. You need to ask yourself some key questions and be comfortable with the answers.

1. What partitions do you want and why?
2. What sizes should these partitions be and why?
3. How important is the data currently stored on the drive?

Depending on the answers, the next question is how to adjust the partitions to what you want. If you have access to an external drive with at least 50GB of spare capacity, there are more options and less risk of losing important data.

For myself, I have resized Windows partitions on about 10 occasions in order to instal linux (mostly ubuntu). Once or twice I have made small adjustments to linux partitions but all my linux installations are experimental and I don't mind reinstalling. On the most recent occasion Windows XP didn't like what I had done but I was able to change the plan and fix the problem. It helped that I had a backup image of the Windows C drive. That's where the external drive is useful.Just ordered a 60GB external hard drive. Hopefully I will get back to this next week.
Thanx for all the help. I will have to put this on the backburner while I wait for my drive to come in.

---

### Post by e_james on 2007-10-09
I have a subscription on this thread so I should notice when you come back. Bye for now.

---

### Post by HareBall on 2007-10-17
OK, I'm back. I have my external drive now. It is only 60Gb. I need to know how to backup my stuff so I can change my partition sizes.

---

### Post by e_james on 2007-10-18
I should be sleeping right now but I'll take a few minutes to get you started. I shoud be back online in about 8 or 9 hours.

There are two different procedures I would recommend.

For the /home partitionyou can simply copy the files into new partition on your external drive but, as i found out for myself earlier today, you have to take account of the way nautilus handles hidden files and folders. This means you have to do the copy in many pieces. Probably a neater alternative is to copy the entire partition to the external drive using Gparted. You simply copy and paste, but the destination area on the external drive must be unused space - not a partition, and it must be at least as big as the source partition.

If you want to backup your system partition the best way is to make a partition image. The program called partimage will do the job nicely but it takes a little bit of practice. It's only when you get to the last step that you realise the significance of some of the earlier steps. The most important point about partimage is that the image file is compressed and only contains data from the used space so your image will be about 4 to 5GB. The basic rule I use about the settings is to only change the ones I know I want to change and otherwise leave the defaults as they are. The trickiest part is that the source partition must be unmounted and the image file can only be written to a mounted partition. If you start from an installed linux system you can't copy the system partition because it can't be unmounted so you can either work from a live ubuntu CD (you have to download and install partimage using synaptic every time you use the CD) or you can use a special utility live CD such as the Gparted CD.

Have a think about my suggestions. If you think you understand enough, have a go. The worst that can happen is you have to wipe the external drive and start again. Just make sure that the data is going from the internal drive to the external drive. The reverse procedure comes after you rearrange your internal partitions and then only if you lose the internal drive data.

---

### Post by HareBall on 2007-10-18
OK, I have installed partimage.I am going to give it a try. I will let you know later how it goes and if(when) I need help.

OK, I have tried to figure Partimage out. I can't figure out how to get it up and running using the GUI. I already know I can't figure out the command line;)

Thanks,:)

---

### Post by e_james on 2007-10-18
Partimage step 1
Make a suitable partition on the external drive. I suggest about 10GB. Other people may have different preferences, but I would probably make it ext3 unless I wanted it to be accessible from Windows, in which case I would use fat32. Then make a folder in this partition. Any name you like but it will minimise complications if you don't use spaces or underscores "_". If you want separators use dashes "-". You will need to type the name in partimage so think about case. File and folder names are case sensitive.

Step 2
To start partimage you open a terminal window and type "partimage". If you are not working as "root" it will warn you. To start it as "root" in a normal ubuntu installation you type "sudo partimage" and then your password when asked. If you are using 7.04 as I am, it probably won't work because the source partition can't be easily unmounted.

More to follow soon.
------------------------------------
Back again

I am now running the ubuntu 7.04 live CD and I have just completed a backup image of my /home partition. It's only 1.9GB and the image file is 1.3GB. It took 3.5 minutes.

First. I had to install partimage

Second. I started Gparted to check the partition names. This had the undesirable side-effect of mounting all the available partitions and opening a browser window for each one. I immediately closed most of them and used one to make sure I was looking at the right partition. A right click on the name or the file area shows the option "unmount" which I used.

Third. I started partimage ("sudo partimage")
Using the up and down keyboard arrows I selected sda9 (ext3 1.9GB). The "tab" key moves the cursor to the file name.
The name I used was "/media/SEA_DISC/recovery/linux-home-image-181007"
"/media" is the mount point used by ubuntu for non system partitions; "SEA_DISC" is the name of my external drive partition; "recovery" is the folder name I made earlier.
Next "F5". On the next page I decided not to change the defaults. "F5" again. Description text for the image file. "tab", OK, One more OK and about 4 minutes later the job is complete.

The partition selection, unmounting etc. is a bit fiddly but the rest of the procedure is quite straightforward.

---

### Post by HareBall on 2007-10-19
I am trying to create a partition on my external drive and have found it to already be formatted for ntfs. It has one partition. I was thinking I could use GParted and add an  EXT3. But, it shows it to be locked and will not let me do anything to it. What next?

---

### Post by e_james on 2007-10-19
I think I had the same problem some months ago but, at that time, it wasn't convenient to investigate further. Information on the internet suggests that Microsoft has modified the NTFS specification as an "improvement" for the benefit of Vista. My provisional conclusion is that if a drive is formatted as NTFS by Vista then any partition manager which predates Vista could have problems.

It is a continuing annoyance in my relationship with PCs that software is often too helpful (Windows and linux). I think this is one of those occasions. I think you want to delete this partition but the software won't let you do something that "foolish".

The best solution that comes to mind at this moment is to connect the drive to a Vista PC. Apparently the Vista partition manager can resize partitions as well as create and delete them. I am assuming at this point that your Windows installation is not Vista. I have no experience of Vista but I suspect that deletion may be the only option because a resized partition will still have a Vista marker in the partition table and this may be enough to block the operation of other partition software.

Edit

I just had another thought. There is a utility on the XP install CD (Pro?) which lets you edit the partition table byte by byte even via a USB connection. I used it once about a year ago to repair a weird partition fault (30GB dive with 2 x 29GB partitions). At this time I can't recall its name. You would also need details of the structure of a partition table. I had that too but I have misplaced it.

---

### Post by HareBall on 2007-10-19
I don't have Vista. I have XP Media Edition. I will try later to see what I can do about this. I may take it to work and see what our tech guys can do with it. They may have Vista installed on a machine there somewhere.
I'll let you know later tonight.

---

### Post by HareBall on 2007-10-20
OK, I'm back. I tried to create an image of my partition, but it kept telling me there were errors in it and it would stop.
I finally gave up and just rebooted using a GParted live CD and resized my partitions. I just figured there wasn't really anything I was all that worried about losing. Well, it worked.
Noiw I would like to look at my partitions and see what is in each of them. According to what I see in GParted, there is about 15Gb of stuff in sdb3. But I don't know how to open it to see what it is :confused:

---

### Post by e_james on 2007-10-20
Hello again. I'm a bit puzzled by some of your comments. I thought you had a working ubuntu system. Are you saying it now isn't working? If it is working I would expect you would have no problem checking the contents of your partitions. I have also found that Administration - System Monitor is a quick way to get an overview of used and free space.

I am a bit concerned about the error messages you seem have seen when you were creating a partition image. So far I have used partimage on at least 4 different PCs and I don't remember that sort of error.

---

### Post by HareBall on 2007-10-20
Hello, I do have a working Ubuntu system. I have tried to do a search for sdb3, which is the partition I am trying to see the contents of. I looked under computer and it only shows the file system, my external drive and my other drive that has XP on it.
I am a little puzzled about it not showing sdb3. I think it only where I had tried in the past to re-install Ubuntu without losing my files under/home. I didn't manage to get it up and running like that back then. Now that I have had more time to think about it, I am pretty sure that is what is in that partition and why it was as large as it was before today.
I am not at my computer now(work), so I don't have a way of trying anything for about 5 1/2 more hours.
I really appreciate the help you have been giving me. :guitar:

Addition - The reason I ended not rebooting with the Ubuntu live CD is that I wrote it to my last CD-R and when I  rebooted the computer, I discovered that I had burned GParted Live to it instead of Ubuntu:(
I didn't feel like going out at that time to get more CD-R's. So, I took a chance and it worked out for me:)

---

### Post by e_james on 2007-10-20
I understand about the CD-R's. The Gparted CD is a working linux system but it is targeted at partition management. By design, a lot of the GUI frills are left out. My personal strategy is to try a variety of live CDs until I find one which does the job I want in a way which I can understand. In this case I think I favour the ubuntu live CD. Its behaviour is familiar and it's running separately from the hard drive installation. Have you bought more CD-R's yet?

Looking again at the attached Gparted image, it seems I may have misunderstood more than I thought. According to the picture, sdb3 is mounted as "/". That means, unless you specified additional partition mount points during setup, it contains the whole linux system. Presumably you specified sdb1 as "/home" and sdb5 as swap. I have found myself asking the question "Which partition holds '/home'?" etc. and I just discovered a simple answer. It's all in System Monitor (File Systems). The Directory column shows the mount points and the Devices column the partitions. I'm thinking now that you'll find you can already see the contents of sdb3 - you just didn't realise you were looking at it. 

What's misleading for people like me who are more familiar with Windows, is that non-system partitions and external drives are mounted in a distinctive way which makes them easily identifiable. There is at least one way in which Windows can do a similar trick to linux / unix. You can reassign the location of "My Documents" to a different partition and when you save your Word file in "My Documents" you don't notice the change.

If the above speculation is rubbish, let me know and I'll try and think of something else.

---

### Post by HareBall on 2007-10-20
> **e_james said:**
> I understand about the CD-R's. The Gparted CD is a working linux system but it is targeted at partition management. By design, a lot of the GUI frills are left out. My personal strategy is to try a variety of live CDs until I find one which does the job I want in a way which I can understand. In this case I think I favour the ubuntu live CD. Its behaviour is familiar and it's running separately from the hard drive installation. Have you bought more CD-R's yet?

Looking again at the attached Gparted image, it seems I may have misunderstood more than I thought. According to the picture, sdb3 is mounted as "/". That means, unless you specified additional partition mount points during setup, it contains the whole linux system. Presumably you specified sdb1 as "/home" and sdb5 as swap.
My wife is getting some CD-R's while I am at work tonight.

I would not be surprised if it is a whole OS hiding in sdb3. I would like to reclaim that space if that is what it is. How do I find out what is there? I haven't been able to figure out how to look at the contents yet. When I get home I will run GParted again and post another screenshot of what I have now.
I am still at work, but I will be home in about 3 hours from now. I understand if you have to quit. I see that you are 5 or 6 hours ahead of me.
If you have to go, I'll "see" you tomorrow.

---

### Post by HareBall on 2007-10-20
Thank you for telling me about System Monitor:) I was able to open the sdb3 partition and I discovered that everything that is in it is also in sdb1. I checked some folders and saw they had the same files in each of them. Can I delete the stuff in sdb3? And then use GParted again and just delete that partition, then use the space to add into sdb1?

---

### Post by e_james on 2007-10-21
3 comments

Linux has ways in which the same file can appear in 2 different folders. Not a copy, but the same file. I suggest you experiment with one or two of the least important files first before deleting in bulk. If you are copying / moving files between the "/" partition and the "/home" partition, you need to be aware of all the permissions involved.

From your recent comments I suspect you didn't read much of the two links I suggested. Have you a partitioning strategy in mind? For instance, if you put everything in one partition, it makes upgrading or repairing the OS a much more risky proposition. It also makes backing up more difficult.

If sdb1 is currently the partition for "/home" and sdb3 for "/" then deleting either one would probably break the existing ubuntu installation even if all the files are correctly copied. When the system boots up it expects certain files to be found in certain folders in certain partitions. I'm sure this can be adjusted but it is well beyond my level of expertise. If you look through these forums you should see many problems about systems not booting properly. I estimate about 20% are related to files in the wrong places and the usual solution to be tried first is a reinstall. That's the reason I suggested an older version of Gparted CD. On my laptop the newer versions won't boot because they can't find the correct files.

---

### Post by HareBall on 2007-10-21
> **e_james said:**
> 3 comments

Linux has ways in which the same file can appear in 2 different folders. Not a copy, but the same file. I suggest you experiment with one or two of the least important files first before deleting in bulk. If you are copying / moving files between the "/" partition and the "/home" partition, you need to be aware of all the permissions involved.

From your recent comments I suspect you didn't read much of the two links I suggested. Have you a partitioning strategy in mind? For instance, if you put everything in one partition, it makes upgrading or repairing the OS a much more risky proposition. It also makes backing up more difficult.

If sdb1 is currently the partition for "/home" and sdb3 for "/" then deleting either one would probably break the existing ubuntu installation even if all the files are correctly copied. When the system boots up it expects certain files to be found in certain folders in certain partitions. I'm sure this can be adjusted but it is well beyond my level of expertise. If you look through these forums you should see many problems about systems not booting properly. I estimate about 20% are related to files in the wrong places and the usual solution to be tried first is a reinstall. That's the reason I suggested an older version of Gparted CD. On my laptop the newer versions won't boot because they can't find the correct files.
I went back and read the two links, in fact I printed the one from linuxplanet. Very good stuff.
I have decided that I will leave things as they are for now. From the looks of things, it is probably as good as it needs to be.
I do have 2 more questions though. First, do I need a biggewr swap file? Mine is 1.41Gb. I have 1.5Gb of RAM. From what I was reading, the swap should be about twice the size of the RAM.  It didn't really come out and say that, but I got that impression. Seems kind of excessive, but I want it to run as fast as I can.

---

### Post by e_james on 2007-10-21
With regard to the swap partition, I have read many comments but no very clear recommendation. The usual comment seems to be that 2xRAM applies to older PCs with 256 or 512MB. Current opinion seems to be that 1GB is plenty. On the other hand, if you have plenty of drive space 2GB won't hurt. 

It might help if I mention an experience some years ago with Windows. I was working with an image scanning application and, at first, it would work with adequate speed and then it would slow down dramatically. The slow-down occurred when I had 2 or 3 images in memory for merging etc. It was my conclusion that the application ran out of ram and started paging to the hard drive. Hard drives are significantly slower than ram although most of them have their own ram buffer these days which complicates the calculations. I suppose my point is that the swap file extends the effective ram of the PC but it contributes nothing to speed. If you need more speed, add more ram.

What was the second question?

---

### Post by HareBall on 2007-10-21
> **e_james said:**
> 
What was the second question?I was wondering if I should rename the / partition to /home or does it really matter as long as I know what it is?
I really do appreciate the help you gave me. Even if I didn't do it exactly the way you said to. It still helped.

---

### Post by e_james on 2007-10-21
If I know something which is helpful to someone else I am happy to pass it on. This seems to be one of the key ideas of Open Source Software. 

I am sure that you can't rename "/" to "/home". Think of the Windows file system on drive C. There is a tree structure starting with "\" with folders and subfolders. Other drives have their own tree. Unix / linux separates the tree structure from the drives / partitions so that the partitions are simply parts of the one tree starting with "/" or "root". Significant branches of the tree such as "/home", "/var", "/usr" etc. can be assigned to their own partitions but it is not a requirement. During installation a partition can be mounted as "/home" if desired, one must be mounted as "/". Other partitions can be mounted at various branches of the tree but, if they have no special significance within linux, ubuntu usually mounts them in the branch called "/media". In other words the name "/home" is part of the filesystem and not the name of the partition as such.

I mentioned permissions earlier. The linux system is organised so that the ordinary user can't change the important parts of the tree including the files. If you try, it will say that you don't have permission or similar. You can only create, edit, delete files in the branch "/home/<your username>" (and the "/media" branch), which protects other users' file as well. Sometimes you need to edit system files so you precede the edit instructions with the command "sudo" and you will be asked for your password. The idea here is that you shouldn't use "sudo" unless you are confident that you know the consequences of your actions. When installation instructions say "become root", in ubuntu terms it means use "sudo".

---

### Post by HareBall on 2007-10-21
Thanx again. I guess we can call this solved. I will watch for you here and read your responses. Maybe I will be able to help one day and pay it forward.

---

### Post by e_james on 2007-10-21
You're welcome. One last comment. Read your signature line. I think it doesn't quite say what you intended.

---

### Post by HareBall on 2007-10-22
> **e_james said:**
> You're welcome. One last comment. Read your signature line. I think it doesn't quite say what you intended. Thanks, I had to look about 4 times to see the missing word:redface:

---

