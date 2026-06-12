---
title: "will a dual-boot keep my new laptop virus-free?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by shams on 2006-01-03
Hi, a big thanks in advance for replying.  

I just bought a new HP DV1411se Laptop, preinstalled with windows xp.  My last desktop was totally munged by a virus and I haven't yet put this PC online-- am a little goosey.  

I'm not super tech-savvy but I think I could pull off a ubuntu install, and probably find the drivers for the wireless card.  My plan would be to use windows for offline work, and then boot to linux when I want to go online.  I have the common impression that linux, properly configured, is much safer than windows -- 

-- but will windows still be vulnerable by viruses I might pick up surfing, and not notice?  Could linux be the carrier?

---

### Post by LaSSarD on 2006-01-03
If you pretend to be ever offline with Windows, then yes you are virus-free, at least in Windows. Linux has almost none viruses and they're almost impossible to infect you, so you can relax :)

---

### Post by proventech on 2006-01-03
you will want to put an Anti-Virus program in you windows and keep it updated just in case you get a disk from a friend, etc and it has a virus on it.

---

### Post by Chipmunk on 2006-01-03
Just one caution, Downloading a virus using Ubuntu and then running it from windows would infect the windows installation, but that would be a deliberate act, not going to happen by accident. Windows shouldn't be vulnerable at all, especially since it probably wouldn't be able to read the ext3 partition ubuntu would be using.

---

### Post by shams on 2006-01-03
<Chipmunk> my fear is not that windows would find the virus, but the other way around.  If it's not clear by now I have only the faintest clue about the mechanics of these viruses.  Guys, is this a good idea?  I guess I'm feeling nervous and I want some real enthusiasm...

---

### Post by 5-HT on 2006-01-03
Hi, while linux is safely guarded against most viruses (not impervious, but basically so for the time being), if you end up downloading an infected file (which most likely won't infect linux) and then boot into windows and execute/open it there is always the possibility that you could be infected.

Mostly, only any data accessible/writable by windows would be at risk.

The best course of action is just to be careful what you download, if you use internet explorer - to set up proper-minded security in it's config, and to do a quick scan of anything coming into your box.

To be honest, I have never come across a virus on my own box running windows, except for some email attachments which were detected before I dowloaded them, so just be a little carefull and you should have no problems.

Edit: As to your last post, as far as I know, any Linux virus scanner will also detect windows viruses.

HTH

Edit: Chipmunk beat me to the mark

---

### Post by Chipmunk on 2006-01-03
Any virus written for windows is going to be unable to propogate via linux.

The only danger would be such things as a friend sending you virus-disguised-as-a-game.exe and choosing to run it in windows after downloading in linux. (unlikely) :)

The advantage is this works both ways, you could download avg for windows using Ubuntu and download the update files the same way.:)

Your plan sounds like an excellent one :)

---

### Post by Omnios on 2006-01-03
Linux can not write properly to Ntfs so therefor can not put a virus onto windows unless you make a fat32 partition to share the files between XP and Linux, though you can read the ntfs partition with linux and copy files to linux. As for viruses I am running a dual boot Ubuntu/XP with a thirt partition as vfat32 as My Documents Drive and have not had a problem with viruses.

 As long as you have a anti virus probram on your Xp you should be ok and also there are anti viruse programs available for linux if that makes you feel safer.

---

### Post by shams on 2006-01-03
thanks for feeling me on that one chipmunk.  

very helpful replies, guys!!  what a great forum.  

Dan/San Francisco

---

### Post by shams on 2006-01-03
1.) avg for windows = ??  antivirus software?

2.) can I trust open-source software to change/shrink/add to my existing partition setup without bungling things?  


I just reg'd with launchpad and ordered some cds:

Date Requested: 2006-01-04 
Status: Approved  
PC CDs: 5

---

### Post by 5-HT on 2006-01-03
[quote=shams]1.) avg for windows = ?? antivirus software?[/quote]

Yup, and it's a free download (last I checked).

About resizing partitions, haven't done so myself with ubuntu's supplied software so I can't give any advice.

---

### Post by Chipmunk on 2006-01-03
1. Yes, avg for windows=antivirus, free for windows. [http://free.grisoft.com](http://free.grisoft.com) (free for private, non-commercial use only)

Usually it wants to do online updates but you can also find the stand-alone virus definition updates at the site.

2. I will leave that one to someone more experienced, I have just wiped windows completely off the system.

Edit to add the non-commercial use only info.

---

### Post by kingsidy on 2006-01-03
you can try something like mcafee viruscan enterprise 8 with antispyware module. I have installed in about 5 systems with questionable usage (if u know what i mean), no spyware at all and no viruses. You might give it a try i think that it is pretty good.

---

### Post by Suger on 2006-01-04
2) Yes, but always make backups before you mess with the partition table.

---

### Post by Sef on 2006-01-04
If you have the Ubuntu Live CD, you can use QParted to change the size of your partitions.    Applications --------> System Tools -------- QParted

---

