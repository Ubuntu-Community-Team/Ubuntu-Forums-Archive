---
title: "Hardrive &amp; ubuntu help"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2007-02-21
I have two hardrives and I would like to keep Windows 98se on the current one and put Ubuntu on the second one.  I want to be able to boot into either one.  Anyhow, I have found some good information on here but nothing much to do with hardrives.  How should my jumper pins be set up?  Just as cable select?  Or master and secondary?  Thanks.

---

### Post by dannyboy79 on 2007-02-21
master and slave work best is my opinion. it doesn't matter which 1 is master either because you control which 1 gets booted first in the bios. you;'re going to want to have both hard drives in there when you go thru the install process so that grub picks up your other os install and adds it to it's boot list. when it asks where you want grub to be installed you'll want to chose which ever hard drive is being booted per the bios, then chose to install grub within the master boot record of that drive. then after you reboot without the ubuntu cd in your computer anc linux pops right up, than we just need to add an entry into your menu.lst file which isn't hard so post back if grub didn't add an entry for ya.

---

### Post by scrooge_74 on 2007-02-21
Hi,

your jumpers just put them as you will do with a XP only system.  Then just boot from a live CD and tell the system to install, when it gets to the partition section you tell it to leave alone your first disk which is going to be call hda and to use hdb which is the second disk

I f you partition it the partitions will be hdb1, hdb2, and so on.  The first disk will always be hda1.  The system will recognize you have another OS working and set GRUB to be able to boot any of them.

If later you want to change which OS boots by default there are easy instructions for it.

Post any questions here and people will help you.

You can also check this site for more info

[http://www.psychocats.net/](http://www.psychocats.net/)

---

### Post by lyceum on 2007-02-21
I would recomend you make Windows the master. It really doesn't matter, but for some reason I find things more successful when MS thinks it is in charge. :) 

Also, be sure to back up your Windows info, just incase things go south. You should be fine, but better safe than sorry.

---

### Post by overdrank on 2007-02-21
Hi, I am new to ubuntu but I have been working with the hardware of computers for awhile. Ubuntu I believe will let you select the drive you want to use for installation. The point is you will have to hook one drive up as a slave and the other as a master. This in turn will make the system that you install on the slave drive operate slowly. The master is always at the end of the IDE cable and the slave is in the middle. The data has to travel to the master and then to the slave, therefore the reduction in preformance. I would suggest using one drive for installation and the other for data and backup for the systems. And if you are using windows 98 (in my opinion) I would just use Ubuntu totaly. Hope this helps. Good luck

---

### Post by dannyboy79 on 2007-02-21
> **scrooge_74 said:**
> Hi,
 The first disk will always be hda1.  
 


Not true! What ever is hooked to the first ide channel will be hda, then if there is a drive chained off of that it will be hdb otherwise your second ide channel first drive will be hdb. so on and so forth. I have my dvd-writer hooked up as the master of the 1st ide channel so my "first hard drive" is actually hdb because my dvd writer is hda. partitions are as he said, hdb1, hdb2.

---

### Post by dannyboy79 on 2007-02-21
> **paul capps said:**
> Hi, I am new to ubuntu but I have been working with the hardware of computers for awhile. Ubuntu I believe will let you select the drive you want to use for installation. The point is you will have to hook one drive up as a slave and the other as a master. This in turn will make the system that you install on the slave drive operate slowly. The master is always at the end of the IDE cable and the slave is in the middle. The data has to travel to the master and then to the slave, therefore the reduction in preformance. I would suggest using one drive for installation and the other for data and backup for the systems. And if you are using windows 98 (in my opinion) I would just use Ubuntu totaly. Hope this helps. Good luck


i don't agree with this at all, I have tried ubuntu installed as the master on the first ide channel and it was no slower than how I have it installed now which is the slave on the first ide channel (my dvd writer is master because I read somewhere that this can give better burning results and it worked so who am I to disagree. I had problems burning stuff before in linux prior to making my writer the master on the first ide cahnnel). the way an ide cable is designed is NOT such that the data has to go thru the master drive to get to the slave drive. the ide connector is simply spliced into the cable, NOT daisy chained thru the hard drive.

---

### Post by dannyboy79 on 2007-02-21
> **lyceum said:**
> I would recomend you make Windows the master. It really doesn't matter, but for some reason I find things more successful when MS thinks it is in charge. :) 

Also, be sure to back up your Windows info, just incase things go south. You should be fine, but better safe than sorry.

or you could do what I did, just have the drive unhooked during the install, then chose to add it in after the install is complete. update your menu.lst, device.map and your fstab properly and you'll be good to go. this is of course the harder way you're a newbie. BUT this would ensure whole heartedly that your data will not be lost.

---

### Post by scrooge_74 on 2007-02-21
> **dannyboy79 said:**
> Not true! What ever is hooked to the first ide channel will be hda, then if there is a drive chained off of that it will be hdb otherwise your second ide channel first drive will be hdb. so on and so forth. I have my dvd-writer hooked up as the master of the 1st ide channel so my "first hard drive" is actually hdb because my dvd writer is hda. partitions are as he said, hdb1, hdb2.

Do you really need to confuse the poor guy with all of this? What i mean is that usually you have the IDE0 cable hook to your drive and any other drive will be either slave to this cable or will go to IDE1. In that sense the first disk will be hda1.

How many computers that come preloaded have the first disk hooked to anything else that the first IDE cable?

---

### Post by igknighted on 2007-02-21
> **dannyboy79 said:**
> i don't agree with this at all, I have tried ubuntu installed as the master on the first ide channel and it was no slower than how I have it installed now which is the slave on the first ide channel (my dvd writer is master because I read somewhere that this can give better burning results and it worked so who am I to disagree. I had problems burning stuff before in linux prior to making my writer the master on the first ide cahnnel). the way an ide cable is designed is NOT such that the data has to go thru the master drive to get to the slave drive. the ide connector is simply spliced into the cable, NOT daisy chained thru the hard drive.

He was right but for the wrong reasons.  Any time you have an optical drive and a hard drive running on the same IDE cable, the performance of the hard drive will suffer.  Optical drives run at a speed of 33mb/s, while hard drives typically run at 100 mb/s (I think I got the units right...).  Therefor, if you share the IDE cable, the whole cable runs at the slower speed.  It is best to do the optical drives on one cable and the HD's on another.

---

### Post by ACF1 on 2007-02-21
> **paul capps said:**
> Hi, I am new to ubuntu but I have been working with the hardware of computers for awhile. Ubuntu I believe will let you select the drive you want to use for installation. The point is you will have to hook one drive up as a slave and the other as a master. This in turn will make the system that you install on the slave drive operate slowly. The master is always at the end of the IDE cable and the slave is in the middle. The data has to travel to the master and then to the slave, therefore the reduction in preformance. I would suggest using one drive for installation and the other for data and backup for the systems. And if you are using windows 98 (in my opinion) I would just use Ubuntu totaly. Hope this helps. Good luck

I would still like to hold on to Windows (not really sure why).  What you are saying is I should put Ubuntu on a partition next to Windows on the master drive?  And then use the slave for data?  I only have a 40 gig master drive, is that big enough to do that with?  

Also, the live CD does not work on this computer for some reason, so I am hoping the alternate CD will work.  Here is my old thread, in case someone thinks of something new to add to it.  [http://www.ubuntuforums.org/showthread.php?t=341450]("http://www.ubuntuforums.org/showthread.php?t=341450")

---

### Post by igknighted on 2007-02-21
> **dannyboy79 said:**
> Not true! What ever is hooked to the first ide channel will be hda, then if there is a drive chained off of that it will be hdb otherwise your second ide channel first drive will be hdb. so on and so forth. I have my dvd-writer hooked up as the master of the 1st ide channel so my "first hard drive" is actually hdb because my dvd writer is hda. partitions are as he said, hdb1, hdb2.

Actually, regardless of whether there is a slave on the primary IDE channel, the first drive (optical or otherwise) on the secondary channel will still always be /dev/hdc

---

### Post by Patrick K on 2007-02-21
I think W98SE will need to be on the primary master. That is the first drive on the primary IDE connector. After all it boots to DOS first and DOS has to be in this position. 

Linux can be anywhere, including in an extended partition. Also, the primary master is hda, the primary slave is hdb, the secondary master is hdc, and the secondary slave is hdd. 

I don't use cable select primarily because of cable routing issues. Just set the jumpers. Also, to help with speed issues it is best to put the second drive as secondary master. That way it is on a different cable and this reduces the traffic on each cables. With modern IDE interfaces, having an optical drive on the same interface doesn't impact the speed, as it once did, of the HD sharing the cable.

---

### Post by lyceum on 2007-02-21
> **dannyboy79 said:**
> or you could do what I did, just have the drive unhooked during the install, then chose to add it in after the install is complete. update your menu.lst, device.map and your fstab properly and you'll be good to go. this is of course the harder way you're a newbie. BUT this would ensure whole heartedly that your data will not be lost.

Good call! Never thought of that....

---

### Post by overdrank on 2007-02-21
Hey I am sorry for causing any problems, I really did not mean too confuse or upset anyone. This is just what I have learn for myself. I will from now on keep it to the point.

---

### Post by ACF1 on 2007-02-21
> **Patrick K said:**
> I think W98SE will need to be on the primary master. That is the first drive on the primary IDE connector. After all it boots to DOS first and DOS has to be in this position. 

Linux can be anywhere, including in an extended partition. Also, the primary master is hda, the primary slave is hdb, the secondary master is hdc, and the secondary slave is hdd. 

I don't use cable select primarily because of cable routing issues. Just set the jumpers. Also, to help with speed issues it is best to put the second drive as secondary master. That way it is on a different cable and this reduces the traffic on each cables. With modern IDE interfaces, having an optical drive on the same interface doesn't impact the speed, as it once did, of the HD sharing the cable.

This computer is about 8 or 9 years old.  Is that still new enough?

What you are saying is this:  I should hook my hard drive up as master to the current CD drive IDE (thats the big, wide, flat cable, right?).  And then set the CD drive to secondary slave?  Thanks again for every thing.

---

### Post by ACF1 on 2007-02-21
> **paul capps said:**
> Hey I am sorry for causing any problems, I really did not mean too confuse or upset anyone. This is just what I have learn for myself. I will from now on keep it to the point.

Thats OK.  I learn more new stuff that way.:)

---

### Post by yanqui on 2007-02-21
It's okay that you want to keep your windows drive, especially if you're just getting your penguin feet wet; you also probably have programs on your windows drive that you may not find for Linux.

I've had limited luck with cable-selecting drives; go with one as master and the other as slave.  AS for performance degradation, with an 8 or 9 year old computer, I'd say the point is pretty moot.  Come to think of it, I don't know that I'd notice it on my brand new computer.  There are so many different possible things that can degrade performance; if your virus scanner kicks in at the same time you're trying to open another file, you will probably see some drop in performance.  But I can't count in nanoseconds.

You may notice that some of the programs seem to take longer to load than they do under windows, but probably not much longer or maybe not AS long as Win98SE.  I haven't found out how to make that go any faster, but I"m open to suggestions.

If your hard drives are different capacities, it'll be easy to tell which one is which when you go to do the install.

---

### Post by Patrick K on 2007-02-21
> **ACF1 said:**
> This computer is about 8 or 9 years old.  Is that still new enough?

What you are saying is this:  I should hook my hard drive up as master to the current CD drive IDE (thats the big, wide, flat cable, right?).  And then set the CD drive to secondary slave?  Thanks again for every thing.
I think it is new enough. It should be ATA66 which is new enough. 

Here is how mine are arranged.
Primary Master=Seagate 160GB
Primary Slave=CDRom
Secondary Master=Maxtor 80GB
Secondary Slave=DVDRW

My board is 5 years old and has an Intel chipset. The IDE controller runs at ATA100 (UltraDMA5). The opticals have no effect on the speed of the hard drives. I had my old MoBo (from 1998) and drives arranged similarly with no performance hit. 

W98 is installed on the primary master. Ubuntu is on a partition inside an extended partition on the same drive. It took some doing to get the 160gb drive to work with W98 (it has a 137gb drive size limit).

---

### Post by confused57 on 2007-02-21
> **ACF1 said:**
> I have two hardrives and I would like to keep Windows 98se on the current one and put Ubuntu on the second one.  I want to be able to boot into either one.  Anyhow, I have found some good information on here but nothing much to do with hardrives.  How should my jumper pins be set up?  Just as cable select?  Or master and secondary?  Thanks.

Another alternative would be to set your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Grub isn't installed to your Windows mbr...if Ubuntu fails, unlikely though, just switch to boot to your Windows drive first...Ubuntu would be connected as master & Windows as slave.

Just another option for your to consider.

---

### Post by Patrick K on 2007-02-21
> **confused57 said:**
> Another alternative would be to set your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Grub isn't installed to your Windows mbr...if Ubuntu fails, unlikely though, just switch to boot to your Windows drive first...Ubuntu would be connected as master & Windows as slave.

Just another option for your to consider.

Don't forget he has W98 and it must be on the primary master. I forget the exact location but it must be within the first so many clusters on the primary master.

---

### Post by confused57 on 2007-02-21
> **Patrick K said:**
> Don't forget he has W98 and it must be on the primary master. I forget the exact location but it must be within the first so many clusters on the primary master.

Good point...might be interesting to see if it would work with Windows 98, the 2 systems I have set up this way both have XP.
I've already installed Ubuntu over top of the old Win98 I had or I'd give it a shot.

---

### Post by ACF1 on 2007-02-21
So if I plug my hardrive (Ubuntu) into the secondary master, and leave the old hardrive (Windows98) on the primary master, would that be a good idea?  I would then have my CD drive hooked to the secondary slave.  Would this all work fine?  Thanks.

---

### Post by Patrick K on 2007-02-22
That should work fine. You will need to edit (or install) grub so you can dual boot. I'm not sure how to install grub after the fact. I've only done it once, during my install. I suggest before putting the drives into position you do a search on installing grub. I know you can do it with the livecd but I don't know how it's done. 

If grub is already installed on the Windows drive, I can help you getting it setup.

---

### Post by dannyboy79 on 2007-02-22
> **scrooge_74 said:**
> Do you really need to confuse the poor guy with all of this? What i mean is that usually you have the IDE0 cable hook to your drive and any other drive will be either slave to this cable or will go to IDE1. In that sense the first disk will be hda1.

How many computers that come preloaded have the first disk hooked to anything else that the first IDE cable?


well you apparently didn't read or understand at all what I said. The first disk is NOT always hooked up as the master to ide0 channel. that's all I was saying. So if this newbie made the assumption that he wanted to install on hda, that could be his cd or dvd drive, which is the way my system is. I don't recall him saying anything about this being a pre-loaded system. This could be a system he built hence my reasoning for "informing" him instead of just making assumptions and telling him what he should do. He won't learn anything that way either. A person could have a cd drive as ide0 master and a dvd writer as the slave on ide0, so his "first disk" wouldn't be hda or hdb, it would be hdc. I am merely trying to explain the way it works.

---

### Post by dannyboy79 on 2007-02-22
> **igknighted said:**
> He was right but for the wrong reasons.  Any time you have an optical drive and a hard drive running on the same IDE cable, the performance of the hard drive will suffer.  Optical drives run at a speed of 33mb/s, while hard drives typically run at 100 mb/s (I think I got the units right...).  Therefor, if you share the IDE cable, the whole cable runs at the slower speed.  It is best to do the optical drives on one cable and the HD's on another.


well again I have to disagree. I just ran a ```
sudo hdparm -t /dev/hdx
``` on my hdb drive which is the slave of the ide0 channel. hda is my dvd-burner, the output is 
/dev/hdb:
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.50 MB/sec

and then the same test of hdc which is the master on ide1
/dev/hdc:
 Timing buffered disk reads:  182 MB in  3.01 seconds =  60.42 MB/sec

so as you can see below I don't believe what you are saying is true. They are both running udma6 and exactly the same drive so we have a true testing scenario! 

```
sudo hdparm -Ii /dev/hdx
```

**/dev/hdb:**

 Model=Maxtor 6L300R0, FwRev=BAH41G10, SerialNo=xxxxxxxxx
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

this is where it states whether it is the master or the slave:
        Device num = 1 determined by the jumper


**/dev/hdc:**

 Model=Maxtor 6L300R0, FwRev=BAJ41G20, SerialNo=xxxxxxxx
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

this is where it states whether it is the master or the slave:

 Device num = 0 determined by the jumper

---

### Post by dannyboy79 on 2007-02-22
> **igknighted said:**
> Actually, regardless of whether there is a slave on the primary IDE channel, the first drive (optical or otherwise) on the secondary channel will still always be /dev/hdc

Well I guess now that I think about it, I am not sure as I have never tested it. how would ubuntu know to keep a place holder (hdb) for a drive that isn't there?? I would think that a drive hooked to the ide1 master would be hdb if there was no slave on ide0 but according to you this isn't the case. I would have to disagree until I tried it unless you're telling me that you tried it for sure? I don't see ubuntu knowing that it needs to save hdb just because an ide cable has an open connector but if you say so I can't say otherwise until I test this myself.

---

### Post by dannyboy79 on 2007-02-22
> **confused57 said:**
> Good point...might be interesting to see if it would work with Windows 98, the 2 systems I have set up this way both have XP.
I've already installed Ubuntu over top of the old Win98 I had or I'd give it a shot.

not true again, this is only if you are booting directly to that os which will not be the case. he is booting grub, which then boots the os. you can have windows on a secondary ide channel and as a slave. the only hard thing to accomplish is having windows installed on an extended partition but it can be done.

and I know this can be done, it's been done with over 100 os's and 4 hard drives and 144 partitions.

---

### Post by confused57 on 2007-02-22
> **dannyboy79 said:**
> not true again, this is only if you are booting directly to that os which will not be the case. he is booting grub, which then boots the os. you can have windows on a secondary ide channel and as a slave. the only hard thing to accomplish is having windows installed on an extended partition but it can be done.

and I know this can be done, it's been done with over 100 os's and 4 hard drives and 144 partitions.

I wasn't sure if what Patrick K said still applied, since grub would be booting Win98 rather than booting directly to Windows...from what you mentioned, it should work to install Ubuntu with the drive set as master drive and Windows drive as slave...the mapping commands fool Windows into thinking it's the first OS.

The OP could always connect the Ubuntu drive to hdb, set it as the first booted hard drive in bios, which should result in Ubuntu seeing it as hd0 & Windows on hda would be recognized as hd1.

Sounds like you've had plenty of experience with installing OS:
> and I know this can be done, it's been done with over 100 os's and 4 hard drives and 144 partitions
Thanks for your input, I believe Ubuntu master & Windows slave should work with Win98.

Then again, he could do it the "old-fashioned" way, Windows master, Ubuntu slave & install grub to Windows mbr...setting Windows drive as the first boot hard drive.

Of course, we've probably confused the OP so much, he'll start another thread.

---

### Post by ACF1 on 2007-02-22
Wow, I have learned a lot lately.  Thanks every one.  

Anyhow, kind of a dumb question, but does it matter what power cable I use to plug in my hardrive?  They are labeled P4, P5. etc.  They all look the same, are they?  Like the cable that is powering the DVD drive, can I take use it to power the hardrive? Thanks.

---

### Post by ACF1 on 2007-02-22
P.S.  It appears that the alternate CD is going to work.  It didn't error when loading the Linux kernel to do the CD check (like it did with the live CD).

---

### Post by dannyboy79 on 2007-02-22
> **ACF1 said:**
> Wow, I have learned a lot lately.  Thanks every one.  

Anyhow, kind of a dumb question, but does it matter what power cable I use to plug in my hardrive?  They are labeled P4, P5. etc.  They all look the same, are they?  Like the cable that is powering the DVD drive, can I take use it to power the hardrive? Thanks.

no, the power connectors labeled like that don't matter. it's just a numbering system and the p means power. you can put the windows hard drive as the master or the slave on the first ide or the second ide channel, it doesn't matter where you put it because the bios is what controls what hard drive is booting first. so you can decide to install onto the windows mbr or install it on the ubuntu disks mbr and decide to boor either hard drive in the bios because grub will load and then look for it's file which are in /boot/grub/. so what I am saying is that you should install grub to the mbr of the hard drive that is being booted by the bios, than grub will pop up and let you chose which os you want to run. good luck

---

