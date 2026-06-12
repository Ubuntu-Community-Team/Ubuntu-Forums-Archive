---
title: "HELP! Recover overwritten files on ext3"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by r76 on 2007-06-06
I have had a major disaster - I went to save a file (from avidemux) into a folder on an external hard drive, to an ext3 partition.  When I double-clicked on the folder to save into, 'videos' it had a blank page icon rather than a folder icon like all the other folders on the disk.  The program then started saving the file as 'videos' itself rather than into the folder!

I cancelled the save but 150MB had already been written, although the folder videos previously contained >50GB of movie files (all .mpgs).  Now all that shows in its place is an mpeg file called videos :(

Please can someone help me recover any of my precious mpgs?

---

### Post by Sef on 2007-06-06
Check out [TestDisk.]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by r76 on 2007-06-06
I could try that, I have SystemRescueCD, which includes the TestDisk package, but do you have any idea how I would use it to recover overwritten files?  On the TestDisk site there is a companion package, PhotoRec, although it's maybe not on SystemRescueCD would that be more useful?

---

### Post by vanadium on 2007-06-06
It is very strange how this could happen. The normal behaviour in a "Select file to save" dialog is that if the filename existed as a directory, then the dialog would open that directory rather than creating a file and replacing the directory.

---

### Post by r76 on 2007-06-06
Exactly - I stopped it as soon as I saw what was happening.  Like I say, I did notice that the icon had changed from being a folder, but I thought that was because the external drive was just slow to wake up.  There was no 'are you sure you want to overwrite the existing file?' type dialog box so when I double-clicked it started saving immediately rather than opening the folder...

---

### Post by r76 on 2007-06-06
OK I found an earlier thread [here]("http://ubuntuforums.org/showthread.php?t=442749&highlight=photorec") which suggests PhotoRec could be helpful - .mpg is one of the file extensions it recognises.  Apparently it is a part of the TestDisk package according to [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)

So I could run it from the SystemRescueCD... or it should be in the [repos]("http://packages.ubuntu.com/feisty/admin/testdisk")

Which means even I should be capable of installing it.  My concern now is with that reference to debian-administration.org:

> 5. Run PhotoRec: 'PhotoRec' is your best choice when trying to recover data from damaged partitions. Basically, it doesn't care about the file system. It simply ignores it. To run 'PhotoRec', just type:

$ photorec

I will remind you that 'PhotoRec' has been automatically installed with 'TestDisk'.

The program's interface is just like 'TestDisk'. Select your device, the partition type (Intel, Mac, etc.), and use "Search". 'PhotoRec' will then make a thorough search of the partition to find files in it and [COLOR="Red"]**recover them to your home directory**[/COLOR] (Into numbered "recup_dir" directories, like "recup_dir.1", "recup_dir.2", etc.). This may take some minutes, or hours, if the partition is very big.

Note that if you are recovering from an Ext2/Ext3 partition, you have to activate the ext2/ext3 mode in "Options".

After search has been completed, quit, take a look at your restored files, and use the command

$ hip hip hooray

which may or may not work.

If you need a more general program for recovering files, you can try the 'recover' and 'e2undel' packages, but these only work with ext2 partitions, and we are assuming that the partitions are not damaged. Basically, you can use these tools after you have used 'TestDisk' to repair a damaged partition or recover a lost one, but some of your files are still lost.

What worries me is what happened in [this thread]("http://ubuntuforums.org/showthread.php?t=339062&highlight=photorec") - photorec will recover too many files into my /home and my system will go down.  Can I specify PhotoRec to restore files to a specific place e.g. another partition on the external drive?  Bear in mind I am trying to recover more Gigs of files than I have free space on my internal HD.

---

### Post by r76 on 2007-06-07
OK, I installed TestDisk through Synaptic, opened a terminal and typed photorec.  This ran in a terminal window and gave me more options than I had expected  - I managed to select to back up on another partition of the external drive - leaving me no worries about having room in my /home folder.  It took hours to run (overnight) and recovered a lot of files, about 2/3 of what I expected to be there - the major problem for anyone considering using this approach is it didn't recover anything in a fragment bigger than 1GB :(

There were 25 .mpg files of 1Gb and then loads of files of varying sizes all the way from 1MB to 982MB.  And some of the larger .mpg files contain part of one video and part of another.

In many cases I reckon it will be quicker to go back and re-edit my source video (I have backed up on data DVD) as it can be difficult trying to put all the pieces back together.  Still a good recovery rate, and hopefully some stuff I didn't have backed up can be salvaged - avidemux will help me stitch the pieces back together I'm sure ;)

How do I file a bug report for the original filesystem error?

---

### Post by r76 on 2007-06-07
THIS IS SO MESSED UP!!!

I decided that the recovered files were no good, too corrupted - just have to begin again.  Thinking I can safely work on that disk again, don't want to try and salvage anything now, I went back to the external hard drive and deleted the FILE 'videos' (a >100MB .mpg if you are following this).  Tried to create a FOLDER 'videos' but the folder cannot be created - error message says name already in use.

Unmount the drive and try again, but this time a folder called videos has appeared AND it contains (as far is I can see) all my original edited videos that I had lost!!!

This is so f***ed up it's not funny, but I can hardly complain, I thought it's take me weeks to edit these files back again :D :D  :D

So, post mortem, what happened there then? :p

---

