---
title: "A few questions before the switch..."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by bitbyter on 2007-09-11
Before I make the switch to Ubuntu I have a few concerns and don't really have the time at the moment to do an exhaustive search:

Will it be able to mount my windows storage drives (I believe that this is possible)?
Is there a method to convert the partitions of said drives to linux without deleting the data?
Is there a way to sync Thunderbird with a Windows PPC in linux (birdie synch is what I am using now in WinXP)?
I have a HDA Digital X-Mystique Sound Card which is not a very widely used card. Other than the post below I couldn't find anything regarding drivers for it. Can anyone here confirm if it will work or not?

"The CMI8768 (X-Mystique) is supported by the ALSA project, with windows the X-Mystique and X-Plosion use the same driver... but I'd hazard a guess that isn't the case for Linux.

Here they have the X-Mystique Linux driver: [http://alsa-project.org/alsa-doc/ind...vendor-C-Media](http://alsa-project.org/alsa-doc/ind...vendor-C-Media)

Obviously it is a rather young chipset and as some of the smarter minds get a hold of these cards, linux drivers could/should pop up."

Thanks

---

### Post by gautada on 2007-09-11
> **bitbyter said:**
> Will it be able to mount my windows storage drives (I believe that this is possible)?

FAT .or FAT32 yeah, no problem.  NTFS should not be a problem but is slightly less stable.  Not enough to stop you though.

> **bitbyter said:**
> Is there a method to convert the partitions of said drives to linux without deleting the data?

Create a new partition.  Copy data.  Delete old partition

> **bitbyter said:**
> Is there a way to sync Thunderbird with a Windows PPC in linux (birdie synch is what I am using now in WinXP)?

Not really sure what you mean.  Using POP? I leave the messages on the server for X days with my non-primary PC.  You should be able to use the same file base for windows and linux versions.  Basically mount the same point for each OS.  I would try this before commiting to a real email account.  So You won;t lose important emails.

> **bitbyter said:**
> I have a HDA Digital X-Mystique Sound Card which is not a very widely used card. Other than the post below I couldn't find anything regarding drivers for it. Can anyone here confirm if it will work or not?

"The CMI8768 (X-Mystique) is supported by the ALSA project, with windows the X-Mystique and X-Plosion use the same driver... but I'd hazard a guess that isn't the case for Linux.

Here they have the X-Mystique Linux driver: [http://alsa-project.org/alsa-doc/ind...vendor-C-Media](http://alsa-project.org/alsa-doc/ind...vendor-C-Media)

Obviously it is a rather young chipset and as some of the smarter minds get a hold of these cards, linux drivers could/should pop up."

No comment...

Note: You should be able to test all of this using the live CD before making the official switch.

---

### Post by mlentink on 2007-09-11
> **bitbyter said:**
> 
Is there a way to sync Thunderbird with a Windows PPC in linux (birdie synch is what I am using now in WinXP)?


Syncing with WM devices is a bit of an underdeveloped area at present. (Unfortunately!) [This link may help]("http://internetducttape.com/2006/08/11/the-holy-grail-of-synchronization-how-to-synchronize-microsoft-outlook-multiple-locations-google-calendar-gmail-ipod-and-mobile-phone-with-funambol-scheduleworld/")

---

### Post by callan79 on 2007-09-11
> FAT .or FAT32 yeah, no problem.  NTFS should not be a problem but is slightly less stable.  Not enough to stop you though

Howdy,

Yep, FAT32 can be easily mounted with full read/write access. NTFS can also be mounted, however given that NTFS is a proprietary format you're actually better to convert all your storage to Linux file system (ext3), and then use the software at [www.fs-driver.org](http://www.fs-driver-org) which will allow Windows to read your Linux disks. Then you're fully open source, and everything works fine. I've been doing this on  1 x 120GB and 1 x 300GB hard drive for the last 12 months, with zero hassles.

Cheers
Callan

---

### Post by bitbyter on 2007-09-11
> Create a new partition. Copy data. Delete old partition

So there is no way to change the partition from a windows partition to a linux one with the data intact (link partition magic does with fat32 to ntfs)? I only ask because the space requirements to do it as above would be troublesome.

---

### Post by gautada on 2007-09-11
> **bitbyter said:**
> So there is no way to change the partition from a windows partition to a linux one with the data intact (link partition magic does with fat32 to ntfs)? I only ask because the space requirements to do it as above would be troublesome.

Specifically you are not changing the partition but the file system on the partition.  I do not recall anyway to do this with ext3 or jfs.  Partition magic and windows installer do specifically allow for the conversion to make it easier for their customer base (I assume).  Backup the data to external media (CD, DVD).  Other than that you have a hardware constraint that will be tough to overcome.

---

### Post by Paul_world10 on 2007-09-11
So this gentleman cannot mount his  NTFS  partitions with Linux?

thanks for that stupid  link uni boy

---

### Post by sumguy231 on 2007-09-11
Regarding your soundcard, you can just boot the livecd and try to play the example content it comes with to see if you have sound working.

---

### Post by HermanAB on 2007-09-11
Well, you can read/write a NTFS partition using the ntfs-3g driver for Linux.  However, you would be better served if you can copy the data to a Linux partition.  All native Linux file systems are more efficient than NTFS and some are vastly so.  For example, NTFS uses 12 to 24% of its space for overhead.  While Ext3 uses 7% for overhead, JFS only uses 0.2% for overhead.  So, by converting to JFS, you can reclaim about 20% of your disk and with modern large disk drives, that 20% can be several gigabytes.

Cheers,

Herman

---

### Post by Snoopyowns on 2007-09-11
Umm.. My main windows xp drive is NTFS, and from Ubuntu i can read and copy files to my ubuntu drive, i just can't write to the NTFS drive.

---

### Post by bitbyter on 2007-09-12
Ok, thanks everyone. I guess I'm going to be offloading a lot of content to external storage. I realize that linux can read NTFS disks but ideally I would like to have everything native to linux eventually.

---

