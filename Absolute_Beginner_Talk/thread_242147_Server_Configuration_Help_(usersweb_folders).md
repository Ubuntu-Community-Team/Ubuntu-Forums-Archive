---
title: "Server Configuration Help (users/web folders)"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by adam1v on 2006-08-23
Hi people, im quite new to this, and never used Linux before, so i will need things explained in idiot terms im afraid.

Ive managed to install Ubuntu Server (6.06) and bolted on the desktop GUI.

Im looking to use the machine as a central server type application for hosting files with some type of security.

I dont need to use it as a webserver, as i already have a machine which is an email server with IIS and it works fine for us.

I would like to setup say, half a dozen shared folders (that i can map from each PC), and ideally set some type of security so that certain individuals have read/write/no access to certain files.

I was wondering how easily this can be done?

Secondly, i was thinking of using a raid setup (say 4x250gb drives) for mirroring as a means of backup, would this need to be setup inside the desktop gui or before?


any help on this, with some commands would be a big big help, thanks in advance.

Adam

---

### Post by FuriousLettuce on 2006-08-23
From what it sounds like, what you really want is NAS (Network Attached Storage). This is a simple box that just serves files to other computers on the network? If that's the case, you might be best off with a distribution like FreeNAS, which is designed to specifically do this. If you go to [www.freenas.org]("www.freenas.org"), you can check out this distribution. It's tiny and makes it easy to set up permissions and things like RAID.

---

### Post by adam1v on 2006-08-23
thanks.. i actually have FreeNas at home.. i tried booting off it, but i got some error messages.. and i think its because it requires one hard drive for the install and another for the storage, and at the moment, the PC im playing with only has the one drive inside.

I will see if i can "find" a drive from somewhere :)

We currently have 3 NAS drives which are the Snap Server model by Snap Appliance. We have had them for about 5 years now, they are starting to get a bit old, and starting to slow down as more and more people are joining the network.

We're looking at getting a dedicated PC with gigabit ethernet and an easier way for backing up.
IF we can add simple security to the folders, its a bonus.


IF you have any further advice, please say.

Adam

---

### Post by FuriousLettuce on 2006-08-23
Obviously it's perfectly possible to partition the hard drive so that you have your OS on the boot partition and your storage on another partition. 

The user guide at [http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf]("http://www.freenas.org/downloads/docs/user-docs/FreeNAS-SUG.pdf") is very comprehensive.

NB: You said you'd never used Linux. Are you aware that FreeNAS is BSD, which is similar to Linux?

---

### Post by Iowan on 2006-08-23
I have a couple of boxes I've set up as file servers - one using Ubuntu (Breezy), one using a single-floppy router called Freesco.  Both use Samba to share files.  Samba can provide the access control you seek. I haven't dealt with RAID, but presume Ubuntu could handle the RAID setup.  
I briefly tried the free version of NAS-Lite but it lacked the ability to access control different "shares".  I downloaded FreeNAS.  I don't remember what I disliked about it - aside from requiring the OS to reside on a different drive from the "shares". I'm not familiar with BSD, so that's a plus AND minus (I'd like to learn, but there's another learning curve).  
If you opt for a Samba server, check [http://howtoforge.com/]("http://howtoforge.com/").

---

