---
title: "Partitionning plan needed..."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by KeeperOS on 2007-10-13
My main (windows) HDD's MBR was broken big time and I need to delete this partition and make a new one. Taking this chance I'll be getting myself a 500GB HDD to backup everything there AND use a portion to install ubuntu on it.

The old 250GB HDD (after I've made it the new partition) will be just as it is now.
The first boot HDD (single partition) with XP on it.
The new HDD will be used solely for shoving every non-executable DATA I have in my current two HDDs to create some breathing room and to install Ubuntu.

I could use one of the automated scenarios ubuntu has but I'd rather make use of the more practical ways (ie neither too simplified nor too elaborate).
I'm thinking a partition for the OS, another for /home, obviously one for swap while I don't know if I'd benefit from sth else. Finally what won't be used for Ubuntu will be partitioned in NTFS (AFAIK the best FS windows XP can recognize with large files support) for backing up everything I would be using from both OSes.
(eg documents, mp3s, videos etc)

Basically what I want is help on how much space each partition should have (I have 2GB of DDRII RAM and an Athlon 64 X2 6000+) and in which order to put them as well as whether I'm forgetting sth... 
I'm not one to re-partition at will so I want this one time to count, only having to delete/re-create the OS partition at worst as well as sparing me from additional work at future re-installations...

---

### Post by Happy_Man on 2007-10-13
I suggest 10 GB /, and the rest (in ext3) for /home. There are ext3 drivers for Windows available @ [http://fs-driver.org](http://fs-driver.org) . And a 512 MB swap would be good too.

---

### Post by mivo on 2007-10-13
I'd also do 10 GB for /, as much as you need for /home (this is where all your personal files go, settings, etc,), and 2 GB for swap, though less will certainly do as well with 2 GB of RAM. Gutsy can see and read NTFS formatted partitions, so both Windows and Linux can access your media files if you keep them in a NTFS partition. In that case you don't need a large /home partition. 10-20 GB may be perfectly sufficient here, and that is probably spacey already. (This is different if you want to save media files in there.)

---

### Post by Pumalite on 2007-10-13
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Mach1US on 2007-10-13
To start with complements for Ext2 for Xp read-write support which i have used for years and love it.
Secondly you can make backup of the Xp partitions boot sector  with software like V2i protector (for windows only :( )
Your thinking for separate non executable partition is absolutely correct as well as separate /home partition , on my own i have Xp partition,Ubuntu patitions and another NTFS partition for storage.
The trick is that having your spare space after Ubuntu partition allows you to very easly extend it in the event if you need more room later  , remember you can only extend Ext3 partitions into space following it , starting point of a Ext3 partition is set permanently and can not be changed (only exception is if you back up entire partition ,reformat it again and then restore it in new space and reconfigure Grub to recognize your setup again - did it my self ,do not recommend ).
And unless you are a gamer be conservative on XP partition because when you start using VMware or other virual machine to run windows you won't be booting into Xp partition at all , i keep mine just out of habit but .

---

### Post by KeeperOS on 2007-10-14
Thanks guys!

Yeah, I'll be waiting for the Gutsy release (can't do otherwise, I can't very well get the new HDD on a Sunday :p) before doing any of this and I already know from pre-beta daily shots that it works with NTFS just fine.

I'm, looking for a FS that windows *natively* support (to avoid future hickups like when having to repair broken windows etc) and the Ext2 IFS seems to have some annoying limitations. What advantages does it have over NTFS?

Ubuntu will for sure going first, the data storage later, so the correct order would be
/
/home
/swap
everything else, right?

Another question, even among windows re-installs I always carry with me the firefox and thunderbird profile data. That to me is paramount.
Are these data stored in the home folder (or its' subfolders) or somewhere else?

Yeah, I occasionally play games, my current one is NWN2 which as some know is very Linux un-friendly and I have an ATI x1950 PRO which also is Linux un-friendly...

---

### Post by mivo on 2007-10-14
> **KeeperOS said:**
> Another question, even among windows re-installs I always carry with me the firefox and thunderbird profile data. That to me is paramount.
Are these data stored in the home folder (or its' subfolders) or somewhere else?

By default they are stored in ~/.mozilla (and sub-folders), yes. (~ being your home). I understand that the profiles are compatible between the platforms, so it might actually be possible to keep the information on a shared partition, but I'm not entirely positive. Can't test it since I no longer have a Windows partition. Generally, all application settings and all user-specific information are stored in your home directory.

---

### Post by KeeperOS on 2007-10-14
Just thought of sth, I think I'm gonna go for 10GB /, 8GB /home and 2GB swap (to have a neat 20GB total).

If I'll need to make the /home folder bigger will this be possible if I were to put /swap **after** it?

I don't suppose it would be too much work to delete /swap. extend /home and create a new /swap as long as Ubuntu would have no problem working like that (I mean without re-installing anything...).

Is that ok or should I better go
/
/swap
/home
NTFS DATA?

---

### Post by Happy_Man on 2007-10-14
Easier to put swap first, if you want to extend /home in the future. Linux itself will have no problem with it, but your physical HDD will.

---

### Post by KeeperOS on 2007-10-14
which brings us to the next problem, will NTFS have a problem with me shortening its' beginning instead of its' end?

If /home goes before the NTFS then this will inevitably mean that to extend the /home I'll have to cut from the beginning of the ntfs partition...

Oh this is giving me such a headache...

---

### Post by Frak on 2007-10-14
> **Happy_Man said:**
> I suggest 10 GB /, and the rest (in ext3) for /home. There are ext3 drivers for Windows available @ [http://fs-driver.org](http://fs-driver.org) . And a 512 MB swap would be good too.
I agree with this one, and for the NTFS problem, if its XP, it wont care, if its Vista, use the Partitioning utility to shorten it, then use the free space.

---

### Post by KeeperOS on 2007-10-14
It'll be XP, no way I'm paying for a re-vamped, de-functional version of XP.
Actually Vista was the reason I thought about making the switch, Ubuntu on the other hand was the reason I *decided* to make it ;)

I don't think the FS-driver will be a good idea because, frankly, it feels immature and un-safe.
I think ntfs-3g is more functional and comparably safer. After all this is a **backup** partition, not one that will take data corruption very well...

So you tell me the NTFS won't care if I shorten it at the beginning?
What would be the best method to do it? BTW, this will NOT be a partition that will hold an OS, only data, what I don't get is what happens to that data that reside on the space that I want to give to the /home partition...

---

### Post by Frak on 2007-10-14
> **KeeperOS said:**
> It'll be XP, no way I'm paying for a re-vamped, de-functional version of XP.
Actually Vista was the reason I thought about making the switch, Ubuntu on the other hand was the reason I *decided* to make it ;)

I don't think the FS-driver will be a good idea because, frankly, it feels immature and un-safe.
I think ntfs-3g is more functional and comparably safer. After all this is a **backup** partition, not one that will take data corruption very well...

So you tell me the NTFS won't care if I shorten it at the beginning?
What would be the best method to do it? BTW, this will NOT be a partition that will hold an OS, only data, what I don't get is what happens to that data that reside on the space that I want to give to the /home partition...
XP doesn't really care if you shorten it, Vista does.

Also, don't make a FAT32 Partition over 100GB (not that you are, just so you know).

Finaly, the FS-driver works 100% fine for me. It only crashed on me once because Windows hiccuped and set my X:\ drive as the C:\ drive and gave me a BSOD.

---

### Post by KeeperOS on 2007-10-14
Well, that's what I mean, chances are that if Windows hickups on an ntfs the damage is reversible (like with my current 250 drive, it works, just not very good but my data **is** safe), if windows hickups on an ext3 fs (that it'll see as a ext2, no journaling...) I'm screwed...

Later, when the driver is more seasoned (or fully supports ext3, including journaling) then sure, in fact then I'll perhaps even use my entire /home for that, but right now it's too high risk for a partition where I can't take any...

---

