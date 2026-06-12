---
title: "Getting Linux to read/write on my NTFS..."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-06-30
Getting Linux to read/write on my NTFS...

I followed this tutorial with no luck: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
I also tried what someone told me they did on theres (other forum). Also no luck.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      484521   244198552+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       23943    89923837+  83  Linux
/dev/sdb3           23944       24321     3036285    5  Extended
/dev/sdb5           23944       24321     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19079   153252036    7  HPFS/NTFS
/dev/hda3           19080       19457     3036285    5  Extended

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS
```

Could someone tell me exactly what I should write for this setup?

---

### Post by catlett on 2006-06-30
First of all. Aysiu's how to you posted the link to isn't about read/write capability. This is the sentence about Ubuntu and ntfs from that link
> Now, we need to edit the /etc/fstab file to make the Windows partition mount with the proper permissions [COLOR="Red"](NTFS is read-only in Ubuntu).[/COLOR] First, let's make a back-up copy of the /etc/fstab file:

If I was going to risk my ntfs partition, this is where I would go for the driver  [http://wiki.linux-ntfs.org/doku.php?...he_ntfs_driver](http://wiki.linux-ntfs.org/doku.php?...he_ntfs_driver)

---

### Post by T700 on 2006-06-30
Let me hightlight something catlett said:

[quote=catlett]**[COLOR=Red]If I was going to risk my ntfs partition[/COLOR][COLOR=Red]....[/COLOR]**[/quote] 
I have seen more than one instance of data loss from trying to write or delete (another form of writing) files on a NTFS partition under Linux.  Please understand that it is an experimental process.

Good luck,
Paul

---

### Post by IDontKnow9998 on 2006-06-30
[QUOTE=T700]Let me hightlight something catlett said:

 
I have seen more than one instance of data loss from trying to write or delete (another form of writing) files on a NTFS partition under Linux.  Please understand that it is an experimental process.

Good luck,
Paul[/QUOTE]

... So 2 be safe I should only read?

---

### Post by Kilz on 2006-06-30
[QUOTE=IDontKnow9998]... So 2 be safe I should only read?[/QUOTE]
Yes, in this case experimental can best be thought of as "I just made an experimental airplane from tissue paper who wants to fly arcoss the atlantic?" 
In other words Dont Even Try It. It could fubar the whole drive.
You can on the other hand create a fat32 partition to transfer files between the OS's and its completly safe. Or just read/copy files over from ntfs.

---

### Post by catlett on 2006-07-01
NTFS (New Technology File System) was created by Microsoft. The inner workings of the file system are a "trade secret" of microsoft. The drivers you are referring to that will let you write to ntfs were made without these "secrets".
What they do is take a "snapshot" of the file system. They then make a change and take another snapshot. They compare the 2 and look for differences. They do this over and over again in many different ways to try and see how the system is recording and storing data. While this reverse engineering may give them a basic understanding of ntfs they do not know the entire system.
Here is wikipedia's summary of it 
> Internally, NTFS uses B+ trees to index file system data. Although complex to implement, this allows faster access times in some cases. A file system journal is used in order to guarantee the integrity of the file system itself (but not of each individual file). Systems using NTFS are known to have improved reliability compared to FAT file systems.

Details on the implementation's internals are closed, so third-party vendors have a difficult time providing tools to handle NTFS. You really shouldn't gamble when there are alternatives.
One alternative is to make a fat32 partition which you use to keep data you want both OSs to access.
The other is to use this ext2 driver to access linux from windows [http://www.fs-driver.org/](http://www.fs-driver.org/)  This will allow you to read and write to linux. So anything you want linux to have from windows you can trasnsfer to the linux partition from the ntfs partition. And anything youi want windows to access from linux can now be achieved with that driver.

---

### Post by IDontKnow9998 on 2006-07-01
How well does fat32 work?

Two of my HDDs are simple movies. But my third one has lots of important data. This HDD even has programs on it.... Can windows handle them the same as NTFS?

Reason why I am asking all this is because windows doesn't want me 2 make a fat32 partition (its not a option when you right click and format on a drive).

---

### Post by T700 on 2006-07-01
[quote=IDontKnow9998]How well does fat32 work?[/quote]

Windows has no problem with FAT32.  The reason that Microsoft doesn't encourage you to use it is that for reasons far to boring to go into, it is limited to 32G in size, per partition, and is less efficent in its use of space to store files.

Paul

---

### Post by Intangir on 2006-07-01
newb!

---

### Post by IDontKnow9998 on 2006-07-01
[QUOTE=T700]Windows has no problem with FAT32.  The reason that Microsoft doesn't encourage you to use it is that for reasons far to boring to go into, it is limited to 32G in size, per partition, and is less efficent in its use of space to store files.

Paul[/QUOTE]

So I cant use fat then?

My HDD is 250 GB.... And I have files that are over 4 GB (over 10GB even)...

---

### Post by IDontKnow9998 on 2006-07-01
[QUOTE=Intangir]newb![/QUOTE]
l0l… didn’t even recognize you till I looked at your avatar :P

Going to read the wiki entry tonight (fat32 is before my time :P I only started learning about comps in win xp (had win 98 on my first comp for only about 6 months))

---

### Post by joshrobinson on 2006-07-01
[QUOTE=IDontKnow9998]So I cant use fat then?

My HDD is 250 GB.... And I have files that are over 4 GB (over 10GB even)...[/QUOTE]

thats the only downsize for me is the whole 4gb file limit.. sucks for large iso's and things along that line... the 32gb partition size is something i dont get.. i have one right now thats a 250+ fat32 partition, an 80gig fat32 and a 190gb fat 32

---

### Post by RRS on 2006-07-02
[QUOTE=joshrobinson]thats the only downsize for me is the whole 4gb file limit.. sucks for large iso's and things along that line... the 32gb partition size is something i dont get.. i have one right now thats a 250+ fat32 partition, an 80gig fat32 and a 190gb fat 32[/QUOTE]

You probably used Linux to create the partitions. I believe the 32g size limit is only if created from windows.

Unfortunately the 4g file size applies to both.

Another alternative that I've seen recommended is to use ext3 for your shared partitions and install FS-Driver in windows to access it.

---

### Post by IDontKnow9998 on 2006-07-02
Couple "facts" from wiki:

[quote="Wiki"]In theory, this should support a total of approximately 268,435,438 (< 228) clusters, allowing for drive sizes in the range of 2 terabytes. However, due to limitations in Microsoft's scandisk utility, the FAT is not allowed to grow beyond 4,177,920 (< 222) clusters, placing the volume limit at 124.55 gigabytes, unless "scandisk" is not needed.[/quote]

[quote="Wiki"]Windows 2000 and Windows XP can read and write to FAT32 filesystems of any size, but the format program on these platforms can only create FAT32 filesystems up to 32 GB.[/quote]

Apparently MicroS did it on purpose (the 32G)...

---

### Post by catlett on 2006-07-02
Fat32 will work fine. The only issue is the 4gb limit on file size.
This is another example of microsoft forcing you to do things theiir way. They don't even give you an option. They just decide and that's it.
I use Gparted Live to make my partitions.  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a live cd. Download it (it's only 30mb) and burn it to disk, then boot to it. The great thing is your partitions are not mounted so the changes can take place right there and then.
I thought I would repost the ext2 driver for windows [http://www.fs-driver.org/](http://www.fs-driver.org/) I havn't had any issue with this driver. This is what I would use for your 4gb+ files that you want dual access to.
The only issue with the ext2 driver is that it doesn't retain the permissions it has in linux when accessed from windows. This is a security risk but if it is you personal computer it isn't a big deal. This is their explanation of it
> What limitations arise from not maintaining access rights?

The current version of the Ext2 file system driver does not maintain access rights. All users can access all the Ext2 volumes that a drive letter is created for. For example, if a drive letter has been created for an Ext2 volume, which is the root volume of a Linux installation, you can simply read and modify files such as /etc/passwd and /etc/shadow. User names are readable and passwords of these users can be quite easily cracked and modified!

Therefore the current Ext2 file system driver does not fit for installations which require restrictive rights policies. It should be sufficient for your computer at home, which is used by one or a few users only. Furthermore, you should create drive letters for a root volume of a Linux installation only if you know exactly what you are doing. 

---

### Post by RRS on 2006-07-02
Catlett, thanks for the link to fs-driver. I'd wanted to include it but I'd "missplaced" it.

The security issue is why I had suggested a seperate ext partition for shared data instead of simply accessing the Ubuntu partitions directly. This would provide protection from outside access thru Windows and IE.

---

### Post by IDontKnow9998 on 2006-07-04
Ok im back working on linux (took a 48 hour break of a site free dl week)....

Couple question about ext2:

1# I know computers are basically layers (hardware, os, etc)... Does this ext2 in windows mean every single application on my whole pc will work the same as ntfs (ex: I can still give the drive letter Z and let Azereus save directly 2 it?)?

2# What is negative about using this filesystem (in other words why wasn’t it suggested in the first place)?

---

### Post by dougmwpsu on 2006-07-04
i've heard of captive ntfs before for getting safe write access in linux... anyone know more?

---

### Post by catlett on 2006-07-04
[QUOTE=IDontKnow9998]OK im back working on linux (took a 48 hour break of a site free dl week)....

Couple question about ext2:

1# I know computers are basically layers (hardware, os, etc)... Does this ext2 in windows mean every single application on my whole pc will work the same as ntfs (ex: I can still give the drive letter Z and let Azereus save directly 2 it?)?

2# What is negative about using this filesystem (in other words why wasn’t it suggested in the first place)?[/QUOTE]
Ext2 isn't the greatest filesystem. It is the last generation filesystem for linux. Ext3 is the new one. Ext2 to ext3 is kind of like fat32 to ntfs. Even though your linux partition will be ext3 , it will act like ext2 in windows. (it's a backwards compatable type of thing. kind of like putting a USB2 device in a USB1 port)

It is not advisable to make any other partition ext2. You will be able to give your linux partition a drive letter and it will act like any other xp partition.

Which brings up RRs's point. Your linux partition is now as vulnerable as the rest of your windows partition. If you have your root partition mounted in xp with the fs driver then that partition will be as accessible as any other partition you have. There will not be any "root" only access. It will be running under xp administrative rights and is accessible.


As for the captive question again 
> I've heard of captive ntfs before for getting safe write access in linux... anyone know more? It's the same issue. The source code is closed. The driver is reversed engineered. Look at it this way. Would you fly in an airplane that was built without blueprints? What if the pilot said "we found an airplane and we took it apart real careful and built another one from the knowledge we learned." I ain't flying in it as long as there is an alternative.
My XP data is crucial but my need to immediately access to it isn't. Personally I have a 40gb external hard drive formatted to fat32. Anything I want dual accessible to I keep in there. If I am in linux and think I want something in xp as well, it gets saved to the external. Vice verse with XP.
It is an easy and relatively cheap solution. When I upgraded my hard drive I put the old one in an external enclosure., It actually solves all my problems. I keep my xp backed up to it. I keep ubuntu backed up to it and I use it as a a place to keep anything I want accessable between the 2.

---

### Post by IDontKnow9998 on 2006-07-05
So a HDD that is ext3 will work fine using the Ext2IFS_1_10b.exe in wondows?

---

### Post by xtacocorex on 2006-07-05
[QUOTE=catlett]Look at it this way. Would you fly in an airplane that was built without blueprints? What if the pilot said "we found an airplane and we took it apart real careful and built another one from the knowledge we learned." I ain't flying in it as long as there is an alternative.[/QUOTE]

That analogy doesn't work too well, but it does in this sense. 

Otherwise, if you just took an airplane apart, you wouldn't know it's aerodynamic and stability aspects if you hadn't flown it, so even making an exact copy could result in disaster, under an inexperienced pilot, if the original design was flawed. (Sorry, I'm an Aerospace Engineer)

That being said, it's safe to assume that NTFS write support isn't good. I don't recommend it to anyone.

---

### Post by catlett on 2006-07-05
[QUOTE=IDontKnow9998]So a HDD that is ext3 will work fine using the Ext2IFS_1_10b.exe in wondows?[/QUOTE]
Yes. The driver is ext2 based but it works with ext3. What happens is your ext3 partition will act like an ext2 partition. The best way I can describe it is like using a USB 2 device in an USB 1 port. The USB 2 device will still work but it will be held to the limitations of USB 1. Nothing gets hurt or corrupted you just do not get the extra performance that is possible with the usb 2 device because it is interfacing with a usb 1 port.
Same thing with ext2 and etx3. You are interfacing with the ext3 partition with an ext2 driver. It will work but you will not get the extra performance outy of the ext3 (you loose the journaling ability of ext3)
It is probably to let the driver's writer explain 
> The Ext3 file system is the Ext2 file system which has been extended by journaling. Ext3 is backward-compatible to Ext2 - an Ext3 volume can be mounted and used as an Ext2 volume. Just as older Linux Kernels which do not know the Ext3 file system can mount Ext3 volumes (as Ext2 volumes), the Ext2 file system driver ext2fs.sys for Windows incorporated in this software package can do it without any problems, too. Of course you do not take advantage of the journaling of the Ext3 file system if you mount it as an Ext2 file system.

>  	
Quote:
Originally Posted by catlett
Look at it this way. Would you fly in an airplane that was built without blueprints? What if the pilot said "we found an airplane and we took it apart real careful and built another one from the knowledge we learned." I ain't flying in it as long as there is an alternative.

That analogy doesn't work too well, but it does in this sense 
I know that isn't a great analogy. I was trying to think of an example of reverse engineering and all I could think of was the Japanese fighter plane that was recovered during WW2 that they reversed engineered.
The point I was trying to make was even if you are careful reverse engineering, ther are issues that you still do not know. It may appear fine but there is still some guessing and there are always "exceptions to the rule" that noone is aware of until the issue comes up.
In the end I do not think it is worth risking writing to ntfs when there are other alternatives.
1. create another partition formatted as fat32. both OSs have full read and write support to that type of filesystem.
2. use the ext2fs.sys driver to access linux partitions from windows and then let windows copy the data from the ext3 partition to the ntfs partition
3. external hard drive formatted to fat 32. If your hard drive is not large enough for another partition you can always use an external hard drive formatted to fat32. The prices are coming down for externals. If you wanted to keep the price down even further, you can buy a pulled 10 to 15gb hard drive off ebay or a local computer shop for arounf $20. Then buy an external hard drive enclosure for the drive for $30 to $40 dollars. Then for $50 to $60 dollars you do not risk anything. Plus you can back up critical data to that drive as well.

---

### Post by Intangir on 2006-07-05
nm

---

### Post by IDontKnow9998 on 2006-07-06
When I go to the terminal and type in "ls" I see desktop or examples. But when I type <cd desktop> I get a no such file or directory found.... :\

edit: OK, I mounted the ext3. My problem was with the <cd> command....

---

### Post by Browser_ice on 2006-07-06
What would be your recommandations for having Ubuntu **reading** Windows's partitioned disks ?

I have files on Windows that I used for personnal projects but want to use them on Ubuntu and I'm too lazy to burn them because of the amount.

---

### Post by crystal on 2006-07-06
> What would be your recommandations for having Ubuntu reading Windows's partitioned disks ?

I have files on Windows that I used for personnal projects but want to use them on Ubuntu and I'm too lazy to burn them because of the amount.
I dont think there's a problem there. Linux has no problems reading from NTFS partitions.

---

### Post by IDontKnow9998 on 2006-07-06
ok a couple question before I change my two important NTFS into ext3:

1# gparted delete the NTFS, then makes a new ext3. It does not do a full format, is that a problem?

2# How safe is this? 

3# Is it possible to defrag these ext3?

4# What is lost&Found folder?

---

### Post by crystal on 2006-07-06
> Is it possible to defrag these ext3?
Generally you wont need to, since ext3 (and NTFS, from what I've heard) is less likely to lead to fragmented partitions.

> What is lost&Found folder?
Could take a look at [What Goes Where on a Linux System?](http://www.lesbell.com.au/Home.nsf/0/87cd60bdf18a2a75ca256caf001594b4?OpenDocument)

---

### Post by Browser_ice on 2006-07-06
Crystal, I haven't done any setup/installs related to Windws<->Ubuntu.

So are you relating to the out of the box Ubuntu or to the installation procedure stated in this thread ?

If it is with the out of the box Ubuntu, I can't read any XP partitions.
error: device /dev/hdb4 is not removable

error: could not execute pmount



p.s. : I'm doing forum searches but there are so many links found which titles don't necessarly mean they contain my answer. Besides, the search only gives the thread link and not the thread AND page of the searched string.

[added]
I think I may have found a good link. I'm on to read it.
[[howto] Gnome 6.06 - Accessing windows files from Ubuntu 6.06]("http://ubuntuforums.org/showthread.php?t=188590&highlight=%22accessing+windows+files+ubuntu%22+6.06")  ==>> **scratch that. It just says its been moved to the HOWTO but I have no indications as where this is.**

---

### Post by crystal on 2006-07-06
> So are you relating to the out of the box Ubuntu or to the installation procedure stated in this thread ?

If it is with the out of the box Ubuntu, I can't read any XP partitions.
error: device /dev/hdb4 is not removable

error: could not execute pmount
Out of the box, using the Alternate CD installer. I dont think that matters though, since it appears that NTFS is perfectly readable from Linux, but writing to an NTFS filesystem is asking for trouble.

---

### Post by Browser_ice on 2006-07-06
Crystal, I didn't use the Alternade CD.

I'm reading a link "[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO%3A+windows+partition+ubuntu+6.06")"

Am I on the right track ?


p.s. : gota go now, got an interview.

---

### Post by IDontKnow9998 on 2006-07-06
[QUOTE=crystal]Generally you wont need to, since ext3 (and NTFS, from what I've heard) is less likely to lead to fragmented partitions.[/QUOTE]

Logic tells me it impossible to complete remove fragmentation. Especially for someone who usually has over 95% full HD... As for NTFS, yea, you do not need 2 defrag as often as FAT32, but nevertheless, it helps 2 do it every once in a while...

---

### Post by catlett on 2006-07-06
I am a little confused. What are your goals. What files are you putting on ext3?

Linux can read ntfs. I attached a png file (a picture of a flag) That picture was in my ntfs window's partition. I opened the partition from Ubuntu and copied it over to my home directory. Then I uploaded it here.  The point is your window's partitions don't have to be ext3 to be read by ubuntu. You can access ntfs and copy the data to your ubuntu partition if needed. 
You don't have to convert. If you need to view something you can just view it. If you have to work on it, copy it over to your home directory and work on it. When you boot into windows again, assuming you installed the ext2 driver, you can keep it in ubuntu's partition and work on it  or you can copy it back to it's former location.
NTFS and Ext3 are the new filesystems for windows and linux. You want to keep linux on ext3 and windows on ntfs. If you make an ext3 partition and use it in windows with the ext2 driver, the partition will act like ext2. Kind of like having an ntfs partition but it has fat32 characteristics.

Unless there is something I don't understand about your needs, I wouldn't change anything. Just install the ext2 driver so windows can read and write to ubuntu. Then just mount windows read only in ubuntu (the installer will do this automatically). This way your data is on the best possible filesystems and it is safe. The only thing about it is it adds a step. If you want to work on something in ntfs while in linux, you have to copy the data over to an ext3 partition..

---

### Post by IDontKnow9998 on 2006-07-07
> **catlett said:**
> I am a little confused. What are your goals. What files are you putting on ext3?

Movie files, windows file, etc. From what I understand ext3 is 100% the same thing as ntfs right (as far as I can tell?)... My goal is to have a file system that can be read and written in both linux and windows.

BTW: I have 4 HDDs. 1 has both linux/windows while the other 3 id like to be able to read-write with linux.

---

### Post by IDontKnow9998 on 2006-07-08
Well am I scary? Or is it a good idea to have a fiel system that both OS can use?

---

### Post by catlett on 2006-07-08
It is fine to have a filesystem that both can read and write to. My choice would be fat32. The one draw back is the 4gb file size limit. 
Ext3 with the ext2 driver is an option but in windows it will not have the characteristics of an ext3 partition. It will act like an ext2 partition which basically means there will not be journaling on the partition.
So take a pick and go ahead.

---

### Post by IDontKnow9998 on 2006-07-08
> **catlett said:**
> It is fine to have a filesystem that both can read and write to. My choice would be fat32. The one draw back is the 4gb file size limit. 
Ext3 with the ext2 driver is an option but in windows it will not have the characteristics of an ext3 partition. It will act like an ext2 partition which basically means there will not be journaling on the partition.
So take a pick and go ahead.

Well... 2 of my 3 HDD's have files over 4GB so I cannot use fat32... What is journaling? I just basically need 2 know if its as stable as NTFS...

---

### Post by catlett on 2006-07-08
> Journaling keeps the file system of a volume consistent, even though the volume has not been cleanly dismounted in the past (for instance because the computer has crashed)

That's a comment on it by the ext2 guy.

> A file system journal is used in order to guarantee the integrity of the file system itself (but not of each individual file)

That's wikipedia's comment.

You can make a fat32 partition bigger than 40GB. Just not with windows formatting app. The limit that does exist is the 4GB file size.

Fat32 is definitely safe and will not have any issues. Ext3 is safe in Linux because it is a standard type of journaling. Ext3 in windows is totally dependent on the ext2 driver. Which appears to be safe. The drawback is the filesystem acts like an ext2 filesystem. If you do basic things with your data then there shouldn't be an issue. There might be some minute speed issues etc. I have the ext2 driver but i use my external hard drive as a go between for writing stuff.

If I an just viewing something then I access the partition directly. If I want to write data to the other type of fs, I move the data to the external drive. Work on it, and then copy it back to the original partition when I am through. That way only windows is writing to ntfs and only Linux is writing ti ext3.

I can't commit further than that because I never converted a large amount of data to ext3 and used the ext2 in Windows to run applications etc off of it. So I can't give an informed decision about the practicality and reliability of doing what you are about to.

---

