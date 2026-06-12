---
title: "problems since hard drive installation"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-11-06
im having serious problems since installing a new hard drive....i have a dell inspiron 600m approx 4 years old....i installed a hitachi travel star 60gb..since then...automatix hangs. the first install of edgy wouldnt save anything to sessions startup or hold any gpg keys from beerorkid repo..plus my gdesklets says its only a 54gb hd and has only 48.6gb free after installation of edgy...i previously had sabayon linux on here..and tried a gentoo install and got several kernel panics..im wondering if the previous install of sabayon or fedora is still on here...is there is way to manually check for other os on this hd...can anyone offer me help please this is agitating..thanks

---

### Post by Sef on 2006-11-06
Get [GParted]("http://gparted.sourceforge.net/").  It's a graphical partitioner, so you can see if your harddrive has any partitions on it and what they are.

---

### Post by rccharles on 2006-11-07
> **swp6499 said:**
> im having serious problems since installing a new hard drive....i have a dell inspiron 600m approx 4 years old.... my gdesklets says its only a 54gb hd 


Manufactures advertise harddrives with a K factor of 1000 whereas Operating Systems use a k factor of 1024. In addition, you use up some space when formating the drive.

> 
and has only 48.6gb free after installation of edgy...i previously had sabayon linux on here..and tried a gentoo install and got several kernel panics..im wondering if the previous install of sabayon or fedora is still on here...is there is way to manually check for other os on this hd...can anyone offer me help please this is agitating..thanks

Does this drive show up on the desktop?

You could reformat the drive. See:

System -> Administration -> Disks

Click on the drive to select

& click around 

Robert



  

To a

---

### Post by swp6499 on 2006-11-07
gparted shows nothing...except the ubuntu install as was the case the other day it did the same thing...i put the sabayon cd in and it tried to rescue the sabayon install after i had completely wiped the hard drive....im thinking the hard drive is a dud...my old hd was a hitachi 30gb 5400rpm this new one is a hitachi 60gb 7200rpm....could there be a conflict in the bios with the drive?..

---

### Post by rccharles on 2006-11-07
> **swp6499 said:**
> gparted shows nothing...except the ubuntu install as was the case the other day it did the same thing...i put the sabayon cd in and it tried to rescue the sabayon install after i had completely wiped the hard drive....im thinking the hard drive is a dud...my old hd was a hitachi 30gb 5400rpm this new one is a hitachi 60gb 7200rpm....could there be a conflict in the bios with the drive?..

Hitachi has a drive test utility.  See:

[http://www.hgst.com/hdd/support/download.htm](http://www.hgst.com/hdd/support/download.htm)

Drive Fitness Test ( v4.08 )

Robert

---

### Post by rccharles on 2006-11-08
> **swp6499 said:**
> im having serious problems since installing a new hard drive....i have a dell inspiron 600m approx 4 years old....i installed a hitachi travel star 60gb..since then...automatix hangs. the first install of edgy wouldnt save anything to sessions startup or hold any gpg keys from beerorkid repo..plus my gdesklets says its only a 54gb hd and has only 48.6gb free after installation of edgy...i previously had sabayon linux on here..and tried a gentoo install and got several kernel panics..im wondering if the previous install of sabayon or fedora is still on here...is there is way to manually check for other os on this hd...can anyone offer me help please this is agitating..thanks


Could try partitioning the drive.  Remember a 30gig drive is smaller when you use 1024 for the K factor.  I'd suggest three partitions to be safe.

For some reason, my 160gig drive had a jumper to make it a 28gig drive.

Robert

---

