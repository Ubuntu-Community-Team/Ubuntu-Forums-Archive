---
title: "Dual Boot Questions"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-07
I have read the following about dual booting:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

my questions are:

1. I'm installing a new 250gb HD when booting up ubuntu will it see the brand new HD?

2. Will it be able to partition the original HD (XP NTFS)?

3. What is a good size partition for a FAT32 partitiong (on a 200GB HD)

4. Does this complicate things??

---

### Post by aysiu on 2005-12-07
[QUOTE=adduds]
1. I'm installing a new 250gb HD when booting up ubuntu will it see the brand new HD?[/quote] Not automatically. You'll have to specify a place for it to be mounted as a "folder" (really kind of like an alias or shortcut).

> 
2. Will it be able to partition the original HD (XP NTFS)? Yes. Read the hermanzone tutorial in full.

> 
3. What is a good size partition for a FAT32 partitiong (on a 200GB HD) As big as you can make it. XP should have at least 10 GB, and Ubuntu should have at least 6 GB. Otherwise, go ahead and put the rest as FAT32.

> 
4. Does this complicate things?? Sure, but it's not that difficult. Of course, if you don't partition, it's a lot easier, but the hermanzone tutorial walks you through it all step by step with screenshots.

---

### Post by adduds on 2005-12-07
[QUOTE=aysiu]Not automatically. You'll have to specify a place for it to be mounted as a "folder" (really kind of like an alias or shortcut).[/QUOTE]

I'm sorry, I don't understand

---

### Post by aysiu on 2005-12-07
[QUOTE=adduds]I'm sorry, I don't understand[/QUOTE] There's this thing called "mounting" in Linux. Basically, it's a way of letting you access the files on a device or partition by making it seem as if the device or partition is part of the larger filesystem--it appears as a folder.

For example, if I plug in my wife's iPod, the iPod itself is located at /dev/sda1, but I can't just go to the /dev folder and click on sda1 to open it. Ubuntu will automatically create a "mount" point for the iPod and /media/ipod, so if I browse to the /media folder and click on "ipod" the iPod's contents will appear in that folder called "ipod."

Well, actually, I don't even have to browse to the /media folder. External media just shows up on the desktop automatically.

Are you familiar with the Mac term "alias" or the Windows term "shortcut"?

When you have a hard drive installed or a partition on your computer, there has to be a way you get at the files in there. For Linux, that means "mounting" the partition or hard drive as a fake folder. The folder doesn't actually exist. When you go to that folder, it just points to the partition.

Let's say, for example, that your new 250 GB hard drive is located at /dev/hdb1 and is FAT32. You could mount it to be at /extra_drive. Then, if you went to the /extra_drive folder, you'd see the contents of that hard drive.

If this is sounding too complicated, you may want to consider using Mepis. In Mepis, all your partitions and hard drives are automatically on your desktop. You click on them, and they automount and open. It's the same process, you just don't have to create the mount point and edit a configuration file to have it happen.

Did that clear things up or just make you more confused?

---

### Post by adduds on 2005-12-07
[QUOTE=aysiu]There's this thing called "mounting" in Linux. Basically, it's a way of letting you access the files on a device or partition by making it seem as if the device or partition is part of the larger filesystem--it appears as a folder.
[/QUOTE]

I'm sorry I may have confused you this is what i meant.

I have a 200GB HD (XP NTFS), and my g/f is buyin' me a new 250GB (CLEAN). I've never installed a HD so I'm not entirely sure how this is going to work period. But After i install the new 250 i want to put Ubuntu on it. During the boot/install process will i be able to repartition (create FAT32) on the 200(XP NTFS) and create a grub for it at the same time i'm partitioning and installing ubuntu on the 250 (Clean hd)

sorry if this is a stupid question or confusing you, i'm just not sure, i'm kinda worried about doing it....:( :???:...you know first timers nervs

---

### Post by Herman on 2005-12-07
Hi,adduds, I have no experience with more then one hard drive, but I also have a spare one around I'll add to one of my PC's sometime soon. Then I'll know more.
 Recently I added a new hard drive to the old computer I'm typing this to you now on and it wasn't much more difficult than replacing a light bulb. After fixing it into position and plugging it in, I just had to access the BIOS and get it to auto-detect the new drive, then start installing my operating systems. As easy as that!:D 
I don't feel comfortable advising anyone about more than one hard drive as far as installing on goes, because I have yet to try it myself. As far as I know they use the same methods basically, I haven't read any complaints yet anyway.

---

### Post by adduds on 2005-12-07
Thanks for the vote of confidence Herman :).  I'm getting ansy i just wanna get the HD and slap it in. I have another question as usual lol.

1. i have like 8-9GB of music on my computer what do you think the best way to back it up would be? i was thinking dvd's?

2. Would it be a good idea to install a fresh XP on here b4 i do all the dual boot?

---

### Post by Gray. on 2005-12-07
It's easier to install XP first (and while you're at it create the FAT32 partition).

---

### Post by adduds on 2005-12-07
so doing a fresh install of xp and creating the 180GB FAT32 partition would be the good idea? 

1. Windows junks up alot, what about fresh installing, do i also have to fresh install ubuntu every time?

---

### Post by Herman on 2005-12-07
> 1. i have like 8-9GB of music on my computer what do you think the best way to back it up would be? i was thinking dvd's?
My wife has a lot of music too, in XP, that requires the licenses (which are hidden files), to also be backed up and I would need to contact my ISP and quiz them about that. It's a problem for us because we can restore the files, but not the licences, so we loose all the music we paid for. There must be a way to back up the licences,... surely!

Gray said:> It's easier to install XP first (and while you're at it create the FAT32 partition). This is quite correct, and you can also: In Windows XP go 'Start', 'Control Panel','Administrative tools','Computer Management','Disk Managment'.
Then right-click on the partition you want formatted as FAT32 and click 'format', and then set the filesystem type in the middle feild from NTFS to FAT32 and click 'Okay'.

> 1. Windows junks up alot, what about fresh installing, do i also have to fresh install ubuntu every time?> 2. Would it be a good idea to install a fresh XP on here b4 i do all the dual boot?
I agree with you! I used to re-install XP every three months or so, I don't have any music licenses to worry about, and hate spyware! It's good to re-install Windows a lot if you use it for the internet, because there are always new kinds of spyware etc, being invented, that takes time for the antispyware people to find out about.
One of the best things about dual booting is you can use Ubuntu only for the internet, and restrict Windows to home use only. Then you'll never get any spyware any more ever again! :D 
My boss just called, I have work to do, bye for now, (Herman):(

---

### Post by adduds on 2005-12-07
[QUOTE=Herman]My wife has a lot of music too, in XP, that requires the licenses (which are hidden files), to also be backed up and I would need to contact my ISP and quiz them about that. It's a problem for us because we can restore the files, but not the licences, so we loose all the music we paid for. There must be a way to back up the licences,... surely!
[/QUOTE]

I have no licenses? lol at all just a lot of music i just mean in general having a lot of music 8-9 gigs is their an easy way to store it all (that's the only important data i have on XP)

---

### Post by Herman on 2005-12-07
adduds, well then if you don't need to worry about music licenses you are fine, you don't have anything to worry about, just back it up as data on CDs, DVDs, or on another computer or disk. 
Where I live, in the Australian Outback, we're several hours drive away from any big music stores, so we really appreciate the opportunity to be able to buy music on-line from our ISP, Telstra Bigpond. The problem is there is some kind of a deal between the music industry (record companies) and Microsoft (media player) and Bigpond, where the songs won't play without some kind of thing they call a 'licence'. I tried making back-ups of the hidden files already ,but it doesn't work. They made it pretty hard for people to cheat. I don't want to cheat anyone, I just want to be able to keep the music I paid for. So we can't re-install Windows on her computer until we solve that problem. To be honest I haven't really applied too much effort to that problem yet.
I was worried you might have the same problem in Canada too, so I wanted to warn you to be careful, music costs a lot of money. (Herman) :)

---

### Post by Justus on 2005-12-08
adduds, don't know if you gathered this much yet, but to create the mount point for the partition, go to System, Administration, Disk (someone correct me if I'm wrong, I'm not in linux at the moment, but anyway, it should be easy enough to find), and then select the hard drive, and then the partition, and the rest should be pretty obvious...choose the mount point, and click "Make Accessable".

---

### Post by adduds on 2005-12-08
[QUOTE=Justus]adduds, don't know if you gathered this much yet, but to create the mount point for the partition, go to System, Administration, Disk (someone correct me if I'm wrong, I'm not in linux at the moment, but anyway, it should be easy enough to find), and then select the hard drive, and then the partition, and the rest should be pretty obvious...choose the mount point, and click "Make Accessable".[/QUOTE]

thanks for the info, although i'm talking about dual booting w/ 2 seperate hard drives. But while we're on the topic of mounting. If I wanna network ubuntu w/ XP which i have using samba i can now see ubuntu files on XP. But how do i see XP from ubuntu over a network? can i still mount?

---

### Post by Justus on 2005-12-08
[QUOTE=adduds][QUOTE=aysiu]Not automatically. You'll have to specify a place for it to be mounted as a "folder" (really kind of like an alias or shortcut).[/QUOTE]I'm sorry, I don't understand[/QUOTE]

I was just explaining that;)

---

