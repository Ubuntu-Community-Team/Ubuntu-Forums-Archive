---
title: "[SOLVED] For Backup HD, need extended and linux-swap? Or only ext3?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-13
I have a dual-boot computer Win98/Feisty, and just shrunk the Win partition on my backup hard drive and added a second partition of type ext3 for the Feisty back-up. Do I need to add another partition of type "extended" (and another of type "linux-swap")? Or is it that since this backup HD is only for storage and not for running an OS, then there is no need for these?

---

### Post by jw5801 on 2007-09-13
No you won't need a swap partition on a backup harddrive. In fact you don't really need a second partition at all. It is possible to read and write to an ntfs partition in linux and to an ext3 in windows, so you only really need the one partition.

---

### Post by swarup on 2007-09-13
> **jw5801 said:**
> No you won't need a swap partition on a backup harddrive. In fact you don't really need a second partition at all. It is possible to read and write to an ntfs partition in linux and to an ext3 in windows, so you only really need the one partition.

I didn't know that. So what is the best way to do it? 

(I should also just mention for clarity that the Windows partition on my Ext HD is fat32, not NTFS. Don't think win98 can use NTFS.)

On another thread a few months ago I had asked the following:

> I had been using an external hard drive to back-up my Win XP system for years. Now that I've switched over to a dual boot (Feisty/XP), is there a way to continue to back up my data on the same hard drive? I guess if I keep the external HD as a Fat 32 disc, it should be able to accept files from both the XP and the Feisty partitions, right? Is there anything more special I would need to do in order to get this working? Can the files from both XP and Feisty be stored side by side, or do they need to be separated somehow in order for the XP OS to be able to see the disc properly?


And I got the following reply:

> you should be able to maintain the partition on the removable as fat32. I'd prefer to make another partition on the removeable as ext3, just to keep it in sync with the many utility programs available in ubuntu. That way there is no problem of mixing non-windows bits with unix bits and you can always have ubuntu read/write .zip files in the fat32 if needed.

It was because of this that I embarked on the project of creating a second partition yesterday.

(By the way, I ultimately got success-- and just in the way you suggested, using gparted on my Feisty and dismounting the Ext HD but keeping it connected. I couldn't get it to work earlier, as I reported to you. But then when I tried it on another computer [a newer one], it worked. And later on after removing a lot of un-needed files on the Ext HD and defragging it, then it worked on my original computer as well. Go figure. -- But thanks so much for all your help yesterday!)

---

### Post by jw5801 on 2007-09-13
All good for the help in the other thread! Glad it ended up working, you had me confused for a bit there! The extended & linux-swap partitions are there as a swap partition, which is what I believe Windows calls page files. ie. this is the point where the operating system stores data when it runs out of physical RAM. It's also where it will write an image if you hibernate or suspend you computer. Therefore if you're only using the disk to store files on, not running an OS on then a swap partition is a bit of a waste. Even if you have several Linux installs on different partitions or even different drives you can still tell them all to use the one swap partition since none of them can be running while any of the others are.

As for your external drive, if it's in FAT32 then you won't need to do anything at all! FAT32 is a format that is well supported in both Linux and Windows so it should just be plug in and go for both. I'm not entirely sure what "utilities" that other post is referring to... FAT32 is a filesystem, the only difference is in how it references data on the disk... what format a filesystem is in is only relevant at driver level, any app can read/write to any filesystem, provided the OS has driver support for it. The only limitation being that FAT filesystems have a limit to the largest file that can be stored on them, but this is several GB for FAT32 and it's unlikely you'll be affected by it unless you plan to back up large disk images or isos or other archives.

As for the NTFS support in Linux, it has read support by default, but if you want to write to the partition you'll need to install the drivers ```
sudo apt-get install ntfs-3g
```and then mount the partition with the type as "ntfs-3g." For EXT3 support in Windows I know there's a driver, but I've never used it so I can't tell you where to find it. I'd imagine google or the forum search engine would be most helpful though.

---

### Post by swarup on 2007-09-13
I see. So is there any benefit to having a separate partition for Windows files in fat32 and Linux in ext3? Any benefit at all? 

Or on the other side, is there any benefit to having the whole backup disc as one fat32 partition for both Windows and Linux backup?

If you were going to set up a backup HD, how would you do it?

Now I have this backup HD sitting here with two partitions--one fat32 and one ext3. Should I leave it like that, or switch back to one fat32 partition? Which is better for the long run-- or does it make any difference?

-----------------------

Also, I have another computer which I'll be setting up a backup HD for. That computer is dual boot XP/Feisty. So what would you recommend for the backup HD's file system there? -- One partition or two. And if one partition, then which should it be: NTFS, FAT32, or ext3? And if two partitions, then what should they be?

Thanks!

---

### Post by swarup on 2007-09-13
Anyone who has experience with setting up a backup hard drive for a dual boot computer have suggestions for the above?

---

### Post by jw5801 on 2007-09-13
Sorry, went to sleep! The only benefit from having a FAT32 partition and an EXT3 partition, is that you can keep some files separate if you so choose, or if you need to store a large iso then you can on the EXT3 partition. Other than that, not really no! It all comes down to personal preference, in the long run.

For the XP/Fiesty setup, once again, there's not one setup that's "better" for your drive. If you want 2 separate partitions to keep files from Windows separated from Linux then EXT3 and NTFS would work. Or if you just want one partition that can be read from both I'd probably go with FAT32 again, because that way you can plug it into your Win98 machine if you ever need to access anything on there. But it's really just personal preference, once you set it up they're all going to work the same anyway, it's just whether you want the external to be seen as one drive or two.

EDIT: Are you backing up specific files? Or are you wanting to use this external drive to put a copy of your OS partitions on, so you can do a complete restore if something goes wrong? If it's the latter, then I'd probably stick with separate partitions for each OS, and if you're doing that then you may as well have each partition as the OS's native filesystem (FAT32 for Win98, EXT3 for Linux, NTFS for Windows). I know there's software out there written for just this sort of application that can take an image of your partition for you to restore later if something breaks, so that might be worth looking into if that's the application you're after. There's Norton Ghost (?) on Windows, and then Ghost for Linux on Linux. Someone else will know more about that though.

---

### Post by swarup on 2007-09-14
> **jw5801 said:**
> Sorry, went to sleep! The only benefit from having a FAT32 partition and an EXT3 partition, is that you can keep some files separate if you so choose, or if you need to store a large iso then you can on the EXT3 partition. Other than that, not really no! It all comes down to personal preference, in the long run.

For the XP/Fiesty setup, once again, there's not one setup that's "better" for your drive. If you want 2 separate partitions to keep files from Windows separated from Linux then EXT3 and NTFS would work. Or if you just want one partition that can be read from both I'd probably go with FAT32 again, because that way you can plug it into your Win98 machine if you ever need to access anything on there. But it's really just personal preference, once you set it up they're all going to work the same anyway, it's just whether you want the external to be seen as one drive or two.

EDIT: Are you backing up specific files? Or are you wanting to use this external drive to put a copy of your OS partitions on, so you can do a complete restore if something goes wrong? If it's the latter, then I'd probably stick with separate partitions for each OS, and if you're doing that then you may as well have each partition as the OS's native filesystem (FAT32 for Win98, EXT3 for Linux, NTFS for Windows). I know there's software out there written for just this sort of application that can take an image of your partition for you to restore later if something breaks, so that might be worth looking into if that's the application you're after. There's Norton Ghost (?) on Windows, and then Ghost for Linux on Linux. Someone else will know more about that though.

No problem about sleeping, everyone has to do it! And I apologize for my delay in reply, as I had to go out after that, for the rest of the day.

My tendency is to want to maintain two separate partitions on the backup, just with an idea that it may be more convenient to keep the files for the two OS's separate. I am not planning on setting up a mirror copy of the entire OS for restore, no. I just want to keep my personal data files backed up.  

I do have two questions. These pertain to the use of the sbackup utility (although if you are not familiar with that one, then I would still very much like to hear your reply with regard to whichever backup utility you do know or use).

1. Can sbackup have in its "files to include for backup" list, files from both native partitions-- and maintain two separate destination locations for allocating files of the respective OS's? That is, can it in one command, backup Win98 files to a designated location on the Fat32 partition, and Ubuntu files to a designated location on the ext3 partition? Or if not, then could I maintain two separate copies of sbackup one for each partition?

Actually on my computer I hardly use the Win98 partition any more, so this really isn't so much an issue for me. The two or three Win98 files I do have, I could just copy and past to the Fat32 backup without issue.

But my brother, using his XP/Feisty computer, still keeps a lot of files on the Windows side. So he is going to want to have an backup algorithm which includes files from both partitions and designates the files to the appropriate backup partition. Can sbackup accommodate this? If not, then for his machine at least, it may make most sense to just have one fat32 partition on the drive. So he can smoothly backup files from both partitions.

2. In sbackup, under the options for backup algorithm, the "recommended" option includes daily incremental backups and weekly full backups. But if I instead choose the "manual" option, I don't see any place where I can determine whether the backup I'm going to carry out on a given day is going to be "incremental" or "full". I would like to have that option, as once I have done a full backup of all my personal data files, I don't think I'll need to do a full backup each time. --Rather, just a backup of the files that have changed since the last backup. Is there any option for that if I am doing my backups manually? (rather than according to the utility's "recommended" option, where the backups are done on a daily schedule predetermined by the utility.)

---

### Post by jw5801 on 2007-09-14
I generally don't use a backup program. The only thing of any particular value to me is my largish music collection (backed up on iPod) and all my Uni work (backed up on a flash drive, as well as the Uni servers), so I've never found a use for one. I keep my /home partition separate to my / partition, so if anything goes wrong in my system all I need do is wipe the root partition and reinstall, none of my actual data is affected.

That being said, I had a quick look over the sbackup utility and:

1. It would appear not. There's only one destination directory that you can set. One would think there would be a "profile" type option somewhere to save different backup schemes, so you could have a "profile" for each set of files you wanted to backup. The program does appear to compress and archive everything for you which could be useful or not depending on the amount of data to be backed up and the size of the external drive.

Correction, upon delving a bit deeper there is apparently a configuration file somewhere, so you could write a couple of them and direct the program to different config files for each partition, but that doesn't sound particularly convenient.

2. I would assume that the manual backup would be a full backup. Incremental implies that it will backup a small portion of the files you wish it to each day, rather than simply synching the backup with any changes to the original files, which is rather difficult to do with an archive.

Ok, well I started a backup so I could check it out and give impressions. It would appear like there isn't an easy way to abort the backup other than killing the background process, which is rather annoying. Also, upon having a look at the backup it was storing, it appears to have stored it as one massive .tgz archive (it was up to two and a half GB by the time I stopped it). That doesn't sound particularly promising since the maximum size for a single file on a FAT32 system is slightly less than 4GB. Although if you don't need to backup too much data then this won't be an issue.
Lastly, it requires you to run it as root, which I'm always wary of, especially for an application like this where there's no good reason for it to need to run as root, other than that it's default backup directory is owned by root. Something like a partition manager I can understand as needing to be run with root permissions, but not a simple backup utility.


For an alternate suggestion, I'd have a look at grsync (a gnome frontend for rsync). It's designed as a program to synch files and directories over a network, but can also be used within the one computer. It's incredibly useful if you only want to synch one directory, but it doesn't have any provision for synching multiple directories at once. There is a "profile" type option (I think they refer to it as "session") however, so if you only had a couple of directories in each OS partition that you wanted to backup then it would work quite nicely. It won't compress the backup for you though.
```
sudo apt-get install grsync
```

It all depends what you're after in the end, that's my input though!

---

### Post by swarup on 2007-09-14
You have given some very interesting food for thought here.

Perhaps the most critical point for me which you've brought up, is the fat32 GB limit and how it relates with the production of a single, massive sbackup .tgz archive file.

> **jw5801 said:**
> I generally don't use a backup program. The only thing of any particular value to me is my largish music collection (backed up on iPod) and all my Uni work (backed up on a flash drive, as well as the Uni servers), so I've never found a use for one. I keep my /home partition separate to my / partition, so if anything goes wrong in my system all I need do is wipe the root partition and reinstall, none of my actual data is affected.

It is interesting that you have chosen not to use a backup program. It seems like the system you have adopted for your /home partition would save you from any problem, up to the point that the hard drive itself goes bad and stops working. Anything short of the hard drive going bad, and it sounds like you'd be fine.   ...But if the hard drive goes bad?

Nonethless, it is interesting. Maybe I should do that too. Regarding the /home partition what did you do? Did you create an entire separate *partition* for your /home folder?

> **jw5801 said:**
> That being said, I had a quick look over the sbackup utility and:

1. It would appear not. There's only one destination directory that you can set. One would think there would be a "profile" type option somewhere to save different backup schemes, so you could have a "profile" for each set of files you wanted to backup. The program does appear to compress and archive everything for you which could be useful or not depending on the amount of data to be backed up and the size of the external drive.

Correction, upon delving a bit deeper there is apparently a configuration file somewhere, so you could write a couple of them and direct the program to different config files for each partition, but that doesn't sound particularly convenient.

Yes, there is a config file. I guess it could be done somehow using it. I have opened and looked at the config file. Just for my understanding, would one have to create an entire duplicate config file for the second set of backup orders, or would use the one config file and just duplicate certain lines in it, like creating a duplicate destination line and duplicate another set of inclusion criteria? The more I think about it, the more it seems like one would need to have two entirely separate config files, and would have to go into the utiliy's link to the config file each time and redirect it to the config file one wanted to use at that moment. If it is like that, then it does sound a bit inconvenient.

> **jw5801 said:**
> 2. I would assume that the manual backup would be a full backup. Incremental implies that it will backup a small portion of the files you wish it to each day, rather than simply synching the backup with any changes to the original files, which is rather difficult to do with an archive.

Are you sure? I used to have a backup program in Windows which was quite old and very nice. And in that program, "incremental backup" meant a backup of all the files in a fullbackup, but only bringing changes to those files which had been changed since last backup. It used an internal flag system for this. As soon as one of the files were changed in the course of normal work, then that file would receive an internal flag by the backup program. So when time came for an incremental backup, then only flagged files would be backed up. In this way the entire backup remained current, but took only a minute or two to update if few files had been changed since the previous backup. This was quite useful. And the backup archive, similar to that in sbackup, was one single compressed file.

> **jw5801 said:**
> Ok, well I started a backup so I could check it out and give impressions. It would appear like there isn't an easy way to abort the backup other than killing the background process, which is rather annoying. Also, upon having a look at the backup it was storing, it appears to have stored it as one massive .tgz archive (it was up to two and a half GB by the time I stopped it). That doesn't sound particularly promising since the maximum size for a single file on a FAT32 system is slightly less than 4GB. Although if you don't need to backup too much data then this won't be an issue.

This is a critical point you have uncovered. I hadn't thought about that. You are right, that the archive file is one massive .tgz archive. So that means that if you have enough files to backup--even though they may be mainly text files--at a certain point the archive file may get larger than 4GB. If it is like that, then fat32 is a highly problematic format to use.

> **jw5801 said:**
> Lastly, it requires you to run it as root, which I'm always wary of, especially for an application like this where there's no good reason for it to need to run as root, other than that it's default backup directory is owned by root. Something like a partition manager I can understand as needing to be run with root permissions, but not a simple backup utility.

Could you educate me a bit more on what the problem is with having it run as root? I would have thought such a program as this is very careful in its dealings-- so that there wouldn't be any danger that it would mess with the OS. Or is there?

> **jw5801 said:**
> For an alternate suggestion, I'd have a look at grsync (a gnome frontend for rsync). It's designed as a program to synch files and directories over a network, but can also be used within the one computer. It's incredibly useful if you only want to synch one directory, but it doesn't have any provision for synching multiple directories at once. There is a "profile" type option (I think they refer to it as "session") however, so if you only had a couple of directories in each OS partition that you wanted to backup then it would work quite nicely. It won't compress the backup for you though.
```
sudo apt-get install grsync
```

Sounds like an interesting and useful utility.

When you use the word "synch", does that mean what I mean when I use the term "incremental backup" (as I described above)? 

> **jw5801 said:**
> It all depends what you're after in the end, that's my input though!

I just want to be able to conveniently backup my files. Now that I understood (I think from you, earlier in this thread), that files and folders from the native NTSF Windows OS can be pasted right into the native Linux ext3 partition, I told my brother that the easiest thing is just to copy and paste all his word documents and folders right into his Linux home folder. And just do backups from there. Then he won't need to deal with backing up both partitions. All his data will be in ext3 on the Linux side. And he can use the sbackup (or grsync if he likes) to backup everything onto an ext3 backup HD. We can still make it a dual partition backup HD with a small NTSF partition and a much larger ext3 partition. The small NTSF partition would be for just copying and pasting a very few files which may not be able to be kept on the linux side--like MS Access data base files. Or could those also be kept on the Linux side?

---

### Post by jw5801 on 2007-09-14
> **swarup said:**
> It is interesting that you have chosen not to use a backup program. It seems like the system you have adopted for your /home partition would save you from any problem, up to the point that the hard drive itself goes bad and stops working. Anything short of the hard drive going bad, and it sounds like you'd be fine.   ...But if the hard drive goes bad?

Nonethless, it is interesting. Maybe I should do that too. Regarding the /home partition what did you do? Did you create an entire separate *partition* for your /home folder?
Yeah it's a completely separate partition, I just tell Linux to mount it at /home. Have a look as aysiu's tutorial on it: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). If the hard drive goes bad then yes I will lose the majority of my data. It just so happens that I use all the vitally important stuff on here in other locations as well, so anything that's not easily replaced actually is backed up somewhere else (or the file on here is the backup, however you want to look at it). So the data I need to back up, I effectively back up simply by the way I use it.

> Yes, there is a config file. I guess it could be done somehow using it. I have opened and looked at the config file. Just for my understanding, would one have to create an entire duplicate config file for the second set of backup orders, or would use the one config file and just duplicate certain lines in it, like creating a duplicate destination line and duplicate another set of inclusion criteria? The more I think about it, the more it seems like one would need to have two entirely separate config files, and would have to go into the utiliy's link to the config file each time and redirect it to the config file one wanted to use at that moment. If it is like that, then it does sound a bit inconvenient.

Yes you would need to create a second config file, although you could let the program do that for you if you just renamed the config file as it would create a new one from scratch.

> Are you sure? ...
No not really, if that is the accepted meaning of incremental in backup utilites then yeah that probably is how it works. I'd take your experience over mine in that one!

> Could you educate me a bit more on what the problem is with having it run as root? I would have thought such a program as this is very careful in its dealings-- so that there wouldn't be any danger that it would mess with the OS. Or is there?
It's incredibly unlikely that it would do anything bad or malicious. But anything run with root permissions is a potential security risk, and since this application has no real need for it, why would it take the risk?

> When you use the word "synch", does that mean what I mean when I use the term "incremental backup" (as I described above)? 
Yup. Synchronize a remote file with a local one.

> I just want to be able to conveniently backup my files. Now that I understood (I think from you, earlier in this thread), that files and folders from the native NTSF Windows OS can be pasted right into the native Linux ext3 partition, I told my brother that the easiest thing is just to copy and paste all his word documents and folders right into his Linux home folder. And just do backups from there. Then he won't need to deal with backing up both partitions. All his data will be in ext3 on the Linux side. And he can use the sbackup (or grsync if he likes) to backup everything onto an ext3 backup HD. We can still make it a dual partition backup HD with a small NTSF partition and a much larger ext3 partition. The small NTSF partition would be for just copying and pasting a very few files which may not be able to be kept on the linux side--like MS Access data base files. Or could those also be kept on the Linux side?

You can store whatever you like on the Linux partition (or on the Windows partition for that matter)! The OS need not have any idea what a file does in order to share a partition with it. There's absolutely no limitation as to the type of file you can store on any filesystem, only to the size on some filesystems. The only difference between one filesystem and another is the way it references the physical location on the disk, the file itself is the exact same combination of 1s and 0s though.

You don't even need to copy the files across to the first partition to do this though. Linux will mount the Windows partition anyway once you have read support for it (which you have by default)! So you effectively have the entire drive (both partitions) at your disposal from the Linux OS. Once you know where it's mounted to you can do whatever you'd like to the Windows partition from Linux, including run a backup utility on it's files. A filesystem is only a way of referencing the physical location on the disk, it has no bearing whatsoever on the data itself and how the data is read by the OS beyond that. You can copy whatever you like to and from whatever filesystem you want, without the binary sequence that is the data changing even slightly (unless there's an error while copying :P). So just add the location on the FAT32 or NTFS partition as Linux sees it to the list of files you want to backup and you're good to go.

EDIT: I apologize if this is a bit badly written, I just got up and am about to head out for the whole day, so if you don't understand anything I've written post back and I'll reply when I can.

---

### Post by swarup on 2007-09-15
> **jw5801 said:**
> You can store whatever you like on the Linux partition (or on the Windows partition for that matter)! The OS need not have any idea what a file does in order to share a partition with it. There's absolutely no limitation as to the type of file you can store on any filesystem, only to the size on some filesystems. The only difference between one filesystem and another is the way it references the physical location on the disk, the file itself is the exact same combination of 1s and 0s though.

You don't even need to copy the files across to the first partition to do this though. Linux will mount the Windows partition anyway once you have read support for it (which you have by default)! So you effectively have the entire drive (both partitions) at your disposal from the Linux OS. Once you know where it's mounted to you can do whatever you'd like to the Windows partition from Linux, including run a backup utility on it's files. A filesystem is only a way of referencing the physical location on the disk, it has no bearing whatsoever on the data itself and how the data is read by the OS beyond that. You can copy whatever you like to and from whatever filesystem you want, without the binary sequence that is the data changing even slightly (unless there's an error while copying :P). So just add the location on the FAT32 or NTFS partition as Linux sees it to the list of files you want to backup and you're good to go.

Fascinating. I didn't realize there was so much flexibility. So one can put a given file on the partition of a given OS, even if that OS has no idea whatsoever what to do with that file. 

Actually, it just occurred to me as I read your post, why it is that when my brother opens MS Word docs in the NTFS partition using OO Writer in Ubuntu, then they open as read-only files. Because in order to write to that file, we have to install that utility which I believe you gave the link to in a previous post. So that problem should be easy to solve. :)

And on the basis of what you have explained above, our backup issue is also solved. Because we can do backups of files on both partitions using sbackup, and just use the one destination of the ext3 partition on the external HD. Even if XP can't read the files there (although I think you referenced a link which would allow it to do so?), but still if we ever had to do a restore, the sbackup in Ubuntu could get the files out of the archive on the backup HD, re-expand them to their uncompressed state, and place them on the XP NTFS partition in the location we request. Right? So backups and restores for both partitions can all be managed from the Feisty side. And archive files of all types from both partitions can be stored without difficulty in the ext partition of the backup HD. Sounds really good to me.

---

### Post by jw5801 on 2007-09-15
Yup! Got it in one.

There's a tutorial [here](http://www.psychocats.net/ubuntu/mountwindows) if you're looking for one on how to enable read/write to an NTFS partition. And [this](http://www.fs-driver.org/) looks like an installer for an EXT2/EXT3 driver in Windows, I've never used it though so you might want to have a search around the forums first.

---

### Post by swarup on 2007-09-16
> **jw5801 said:**
> Yup! Got it in one.

There's a tutorial [here](http://www.psychocats.net/ubuntu/mountwindows) if you're looking for one on how to enable read/write to an NTFS partition. And [this](http://www.fs-driver.org/) looks like an installer for an EXT2/EXT3 driver in Windows, I've never used it though so you might want to have a search around the forums first.

Thanks for the tutorial references. I checked out the one for enabling write permissions to NTFS. It is very good and clear. This should pretty decisively solve the last of the file partition issues that I've had. Thanks again.

Oh-- one last thing-- you know how neither Win98 nor XP even realize or acknowledge that there is a second partition on the hard drive? They don't seem to see it at all. If one loads the EXT3 driver, then will that make the second partition appear in the Windows Explorer window?

                                                                                                 -  -  -  -  -  

By the way, I heard Gutsy will be coming out in October. Is that correct? And if so, then will the same limitations for read/write likely hold there? If in October I want to switch over to Gutsy, then will it be a simple upgrade? Or will I have to save my personal data, uninstall Feisty, and then install Gutsy? There are a variety of sticky points with Feisty such as difficulties with my wireless network, and some bugs with Feisty and OO Base, which I am hoping Gutsy will have solved.

---

### Post by jw5801 on 2007-09-17
Yeah, once you install the EXT3 driver Windows will be able to see and mount the Linux partition. It works exactly the same way from Linux, there would be no indication that there was a second partition on the driver if you didn't have a driver that let you read an NTFS partition by default.

As for Gutsy, it is due for release on October 18th last I heard. I doubt it will have read/write abilities for NTFS by default though, as NTFS is a proprietry filesystem (as far as I'm aware anyway), so it goes against the Ubuntu ethos.

It should be a reasonably simple upgrade, provided nothing goes wrong. I'll probably opt for a fresh install, my home partition will remain with all my settings so all I'll have to do is reinstall the apps I installed. It should be something as simple as changing the repositories over and running an upgrade I think (I've never done one myself) but I'm sure the forums will be filled to the brim with howtos once it's released :)

---

### Post by swarup on 2007-09-17
(repeated below by mistake)

---

### Post by swarup on 2007-09-17
I see. That's all great info.

Don't think I can even think of any other questions to ask you at this time-- I'm all questioned out. You've answered them all.

Thanks again for all your help. :)

---

### Post by jw5801 on 2007-09-17
No probs! Glad to be of help.

---

