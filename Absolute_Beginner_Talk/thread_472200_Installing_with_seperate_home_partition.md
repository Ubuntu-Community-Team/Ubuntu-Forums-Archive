---
title: "Installing with seperate /home partition"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-12
I have found a lot of guides that deal with making the home folder AFTER you install and then change your mind, but how do you make one during install?

what is the min size my / should be? and is having them on different HDs have advantages or disadvantages? I have a 80gig and 250gig currently. COuld I possible set up a backup partition, cause I do not need all that space...

---

### Post by FleetAdmiral74 on 2007-06-12
I found some guides, some said to make an extended and logical partition, and put a partition in there with a mount point of /home. Is this correct? So it will automatically put the home folder there, not the /?

---

### Post by BirdZerk on 2007-06-12
I have also been thinking about separating my /home directory out and also creating a separation partition for all my data.  I think all of that can be created during the partition management section by choosing manual setup, during the installation process.  As for partition sizes, I am going with 10 GB /, 10 GB /home and the rest for my data partition (about 140GB), and I was going to have them all primary partitions, since it is just the three.  I hope this helps and if I am wrong please let me know.

---

### Post by starcraft.man on 2007-06-12
> **FleetAdmiral74 said:**
> I have found a lot of guides that deal with making the home folder AFTER you install and then change your mind, but how do you make one during install?

what is the min size my / should be? and is having them on different HDs have advantages or disadvantages? I have a 80gig and 250gig currently. COuld I possible set up a backup partition, cause I do not need all that space...

> **FleetAdmiral74 said:**
> I found some guides, some said to make an extended and logical partition, and put a partition in there with a mount point of /home. Is this correct? So it will automatically put the home folder there, not the /?

Ok. Minimum size your root should be is 6 GB. 3-4 is the basic root install with nothing else. I recommend 8 GB for root, room for expansion and lots of large apps like installing KDE/other WMs later.

Your root can only be on one drive, it should be your fastest internal drive, home should be on the same drive too since it is accessed very frequently and stores many user config files. Any other data partitions/folders you feel like making can go on any other drives/partitions you want but they are extra and not essential. 

Yes, you can set up a back up partition/drive. It is a good idea, you can then use an application/script to image or move backups to it on a regular basis. I always store back ups external to the drive with all my OS, in case it should fail they are safe.

Now for logical and primary. Windows and Mac partitions I believe have to be Primary to boot. Linux actually doesn't I believe. But I still make it a primary partition, I don't use that many anyway. Home and your swap file can both (and should be) extended/logical drives.

Now to further explain all this I will refer you to some guides to read. I could write it all out but it would seriously take me time... The bottom line though is you want to manually partition your drive when you install. Thats the only way your gonna get custom sizes and a home folder. It's not too scary and you can do it.

[On planning partitions.]("http://www.psychocats.net/ubuntu/partitioning")
[This section of the desktop install shows how to partition.]("http://www.psychocats.net/ubuntu/installing#partitioning")
[GParted Documentation, talks about partitions in general and explains many things.]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")


[For Backups, try partimage a good solution I've heard.]("http://www.psychocats.net/ubuntu/partimage")

Advice:

This is what I think you should do. Feel free to do something different if you disagree.

80GB drive
Partition Name - **Mount Point** - Format - **Type** -       Size
Root                       **   / **                      Ext3       **Primary**  10 GB
Home                       **/home**               Ext3      **Logical**     69 GB (or X for whatever is left)
Swap-file                **N/A**                    swap-file **Logical**  1 GB
(Unknown) 
If you want to install another OS for a dual boot, make it primary and give it space from the home partition.

250 GB drive
Partition Name  - Mount Point   - Format  -   Type  -  Size
Data                         /media/Data    Ext3             Logical  Y GB
Back Up                 /media/Backup Ext3           Logical    Z GB

(I put Y and Z in the second drive cuz its up to you the size of each. I'd give Data 200 GB and Back Up the last 50 GB that will give you plenty of space for media and lots of room for a few back ups.)

Thats it. All the best, post back if you need help.

Edit: Har, just remembered that my spaces don't hold on the two semi-tables I made. I don't really have time to make a table, quote them and you'll see how I intended them to be as advice.

---

### Post by FleetAdmiral74 on 2007-06-12
I am going to follow those instructions to do a backup, but how can I automate this as you imply with a script of some kind? That would be nice...

And is it any better to backup the image to a different HD than the same HD?

And one more question. So using the above method, it does not really install PartImage so every backup I would need to go back to the LiveCD and do this all over?

---

### Post by starcraft.man on 2007-06-12
> **FleetAdmiral74 said:**
> I am going to follow those instructions to do a backup, but how can I automate this as you imply with a script of some kind? That would be nice...

And is it any better to backup the image to a different HD than the same HD?

And one more question. So using the above method, it does not really install PartImage so every backup I would need to go back to the LiveCD and do this all over?

Backup to a seperate HD, it makes it more secure IMO. I modify my internal one often and there is always the chance I render it unbootable or accidently wipe it (I do a lot of serious modification). Since all my data and backups are on an external usb drive I can't lose anything important and can restore my computer to operation in under 30 minutes from my images I store there. I use Acronis rather than partimage but its the same thing really.

Now, partimage is more of a manual solution IMO, just like other Disk Imgaing Suites. I like these products because they make a bit for bit copy (called image or snapshot) of the drive and store it where you specify and compress it for longterm storage and restoration. By doing this, you have a copy of your drive that will always be good tucked away and if you mess up your install you can restore it and have your computer operating in under 30 minutes. Oh and if you really want to automate it, I believe you'll need to bash script it manually.

Now, for more automatic back ups of data (say like office files you save to your home partition daily) I would direct you to the [simple backup suite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"). It is GUI and friendly to making back ups to and from anywhere you like. I haven't used it much but it seemed very good from what I saw and was recommended.

So, this is what I suggest. Use partimage to make an initial backup of your clean install of everything and how your partitions are set up, including MBR. Then install all the programs you want/customizations and image a second time. This one label it with a date and you will know to use it to restore your computer perfectly. Now you have a clean install to fall back to if there is ever need for that and a complete one for instantaneous restore. Then once these two are done, use the simple backup suite for folders and other files you use daily to be synced/back up to wherever you like.

Thats it. I think I answered all questions. Best of Luck, and remember to point to the Zerg when spotted :p.

---

### Post by FleetAdmiral74 on 2007-06-12
sweet! thanks for answering.

omg another question, sorry! i really appreciate all your time.

so if the HD i am backing up to has less space then the partition backing up from, will it be ok untill is actually FILLS up, or will the image take the full partition size automatically? Cause my other drive hsa like 73gigs, my home partition is 100gigs, but i wont reach that for a while.

---

### Post by starcraft.man on 2007-06-12
> **FleetAdmiral74 said:**
> sweet! thanks for answering to both posts haha, figured this one would get more attention  :D

omg another question, sorry! i really appreciate all your time.

so if the HD i am backing up to has less space then the partition backing up from, will it be ok untill is actually FILLS up, or will the image take the full partition size automatically? Cause my other drive hsa like 73gigs, my home partition is 100gigs, but i wont reach that for a while.

Imaging only backs up the actual data, so if your drive is 100 GB big and only actually uses 10 GB it only backs up those 10 and records info on the partition and how large it was. Also, I'm pretty sure partimage compresses the archives well. I get 60% compression (by that I mean a 10 GB archive down to 4 GB out of my acronis image suite, its paid though and not partimage). The image does not as you said occupy the entire space, its just a blob of data to be restored at a later time.

I wouldn't image all your data in home though, rather its probably best to just create a daily back up of anything thats important in it to the data partition you make on the big drive with the simple utility.

If you do run out of space in your partition though you will have a problem. I doubt it though, just remember to limit partimage to your root and empty home partition and back up any media and other unimportant data with the simple suite. That should be it.

Your really welcome, I don't mind spending the time it took to write all that out :p.

---

