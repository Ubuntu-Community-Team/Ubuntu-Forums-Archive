---
title: "Trying to copy large file to OSX"
date: 2013-05-28
forum: Apple Hardware Users
---

### Post by rlindsley on 2013-05-28
Hi there,

Apologies if this has been asked and answered.  I have searched but have not found an answer for this.

I am trying to copy a 100GB file from my Ubuntu partition to OSX.  I have a 1TB drive, with 500GB partitioned to OSX, and 500GB partitioned to Ubuntu Raring Ringtail.

I followed the instructions on this thread, which has made the drive mountable in OSX:

[http://ubuntuforums.org/showthread.php?t=1688257](http://ubuntuforums.org/showthread.php?t=1688257)

My problem is that I don't have rights to read the files in the home directory of the Ubuntu partition.  If I can get read rights to the home directory, I can copy the file I need over.  Specifically, I'm trying to read the files in disk0s5 (which is the mounted location) /home/robert.  I currently only see two files when I open that location:

Access-Your-Private-Data.desktop - this appears to be a shortcut of some kind
README.txt - obvious, but I can't open the file

Any chance anyone on the thread has a solution for this?

Thanks!
Robert.

---

### Post by TheFu on 2013-05-29
I don't know anything about OSX, however those instructions seem to be for EXT2/3 File systems.  By default, Linux installations have been using EXT4 for years.  This file system is not compatible with those older tools.

If you connect to the remote machine using the credentials of the file owner, then it should "just work".
If you connect to the remote machine using other credentials, then you need to understand UNIX/Linux file permissions [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) should help.
It is possible if you use a non-UNIX connection ... samba comes to mind ... then other program-specific permissions will be important to understand.
If you use encryption of the file systems, then you'll want to ensure decryption happens before (or as part of) your connection.

Lastly, the file systems involved could have file-size limitations.  FAT16 and FAT32 don't support files over 4G (I think), so attempting to copy any larger file will fair **every time**.

If I were trying to do this, I'd have Linux mount the OSX partition and push the files over.

Good luck!

---

### Post by rlindsley on 2013-05-29
> **TheFu said:**
> I don't know anything about OSX, however those instructions seem to be for EXT2/3 File systems.  By default, Linux installations have been using EXT4 for years.  This file system is not compatible with those older tools.

If you connect to the remote machine using the credentials of the file owner, then it should "just work".
If you connect to the remote machine using other credentials, then you need to understand UNIX/Linux file permissions [https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) should help.
It is possible if you use a non-UNIX connection ... samba comes to mind ... then other program-specific permissions will be important to understand.
If you use encryption of the file systems, then you'll want to ensure decryption happens before (or as part of) your connection.

Lastly, the file systems involved could have file-size limitations.  FAT16 and FAT32 don't support files over 4G (I think), so attempting to copy any larger file will fair **every time**.

If I were trying to do this, I'd have Linux mount the OSX partition and push the files over.

Good luck!

Thanks for your help!  There's a ton of great info here that I'll dive into.

The big issue is that both partitions are on the same machine, so there's no 'connecting to a remote machine' per se.  I'll try SMB to see if that works.  I'll also do a quick primer on file permissions, although the partition is mounted as read-only so it probably won't let me change anything to get the access I need.

I also tried to mount the OSX partition from Ubuntu and there are so many hoops to jump through, I'm not even sure if it's really possible to do what I'm trying to do. If you have a thread on that, could you post it?

The big problem is the file is so large.  If it were only 2GB or 4GB there wouldn't be a problem at all, because I would just copy it to a thumbdrive and be done.

I'll also try to mount as EXT4 and see if that works.  What a PITA!!!

Thanks!
Robert.

---

### Post by danield on 2013-05-30
> **rlindsley said:**
> I also tried to mount the OSX partition from Ubuntu and there are so many hoops to jump through, I'm not even sure if it's really possible to do what I'm trying to do. If you have a thread on that, could you post it?

If your OS X partition is journaled, i.e. formatted as HFS Extended (Journaled), you can't write to it from Ubuntu.  I've seen it mentioned that you can disable journaling, but I've never tried it.

Also, there's a thread here that mentions virtualization:

[https://discussions.apple.com/thread/4859349?start=0&tstart=0](https://discussions.apple.com/thread/4859349?start=0&tstart=0)

---

### Post by coldraven on 2013-05-30
I have never tried this so proceed with caution.
There is the "split" command which, in theory, could split the file into chunks that would fit on a memory stick.
I don't know how you would then rejoin the file, use "cat" maybe.
Be careful! My old boss made a mistake with the "split" command line and reduced an important database to over 100,000 pieces! Ooops!

---

### Post by GhettoMrBob on 2013-05-30
The easiest/safest way to do this is to disable the journaling on the OS X partition. I've done this before when I've had to mount failing OS X drives that weren't readable/mountable in OS X but are in Linux/Ubuntu.

Best/easiest way to do this is: 
Boot into OS X and fire up Disk Utility. It's under Utilities in your Applications. 
In disk utility select your OS X partition and disable the journaling through File -> Disable Journaling. (depending on which version of OS X you have you may need to hold down the alp/option key when clicking File)
Reboot back into Ubuntu and you should have read/write access for that drive.
Once you're done copying that file you can boot back into OS X and enable the journaling again.
[B]
Note:
[/B]Having journaling on is a good idea so I would not leave it unjournaled. One important thing that relies on journaling is Time Machine, for example.

---

### Post by TheFu on 2013-06-01
After reading all these complex solutions (disabling journals? Seriously?), seems like spending $40 on an external USB HDD would make the most sense.  
[http://www.pricewatch.com/price/hard_removable_drives/usb_320gb](http://www.pricewatch.com/price/hard_removable_drives/usb_320gb) shows where you can get a 320G HDD inside a USB case.  Just be sure to format it for the defacto-standard data sharing file system ... cough ... NTFS.

I would not disable journaling. There is a reason that **all** modern file systems support it.  Don't forget the days of 3 hr fscks, ok?  Journaling makes those 10-20 seconds.

Mounting EXT4 from tools that are not specifically designed for it is a terrible idea. It will lead to data corruption.  EXT4 has little to do with EXT2, EXT3 file systems.

---

### Post by GhettoMrBob on 2013-06-01
I'm not sure why you'd want to spend $40 on an external. The solution I gave you is extremely simple and requires you to boot into OS X only twice. I assure you that disabling journaling for the time it would take to copy files is **not** going to cause any harm. In fact, you can install OS X on an unjournaled partition if you really wanted to.

And OS X does not support read/write to NTFS by default. It supports read-only unless other steps are taken to enable it.

---

### Post by rlindsley on 2013-06-03
Hi Guys,

I tried to disable journaling through the Disk Utility and there wasn't an option, even after pressing the key combinations to get the extended menus on screen.  After some additional research the most recommended method was to go into command prompt to disable journaling, which looked a little out of my comfort zone.  

So I pulled a 320GB external HDD from the basement.  After formatting NTFS, I went into Ubuntu to write the file, and copied it over to OSX no problem.

Thanks everybody for your help!  I really couldn't have done it without all the help from this thread.

Thanks!
Robert.

---

### Post by GhettoMrBob on 2013-06-03
FWIW, once in Disk Utility you have to select the partition with OS X on it. THEN hold alt while clicking File. Should be near the bottom. 

..just in case you ever want a quicker way if your external isn't available.

---

