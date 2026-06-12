---
title: "Recovering Breezy"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by InsanePenguin08 on 2006-06-01
I upgraded to Dapper Drake, and then I found out that my grpahics card isn't supported at the moment, so what am I supposed to do?  

I really, really don't want to lose all of my settings in Breezy by doing a complete reinstall.  I know that there is a way to back up the files that were in Breezy, then do a fresh install (on another partition, perhaps?).  How would I do this, though?  It's got to be done from the terminal, as Xserver and GDM are crashed right now and I can't use a GUI.

Thanks for the help, in advance!

---

### Post by aysiu on 2006-06-01
Are you talking about this?
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

Of course, the repartitioning part might be hard to do from the terminal...

Do you have a live CD?

---

### Post by ProjectGod on 2006-06-01
use tar and gzip to archive and compress your configuration files... e.g. 
/etc/X11/xorg.conf
/etc/skel/
/etc/samba/smb.conf
/home/insanepenguin

etc etc

then copy them to a storage device. then reinstall everything... then restore what you need... although i presume settings in breezy were lost due to the installation of dapper... but what's important is your personal data... don't worry too much about the system configuration settings... it'll improve your skills to reconfigure a system! :mrgreen:

---

### Post by InsanePenguin08 on 2006-06-01
Well this is odd.  I managed to stumble my way back into making it work, and I can log in with a GUI.  Everything seems the same as it was, except for my sound isn't working (it says the soundcard isn't configured, how would I do that?) and my internet is down.

---

### Post by ProjectGod on 2006-06-01
well that's just insane!!!! :mrgreen:

is your sound card a pci or onboard?

is your internet wireless or wired?

dialup or broadband?

always on or need logging off / on?

---

### Post by InsanePenguin08 on 2006-06-01
My soundcard is PCI, and it shows up in lspci as> 
0000:00:1f.5 Multimedia audio controller: Intel corp. 82801BA/BAM AC'97 Audio (rev 04)

I have wired, broadband internet that doesn't need to be logged into, it's always on.

---

### Post by InsanePenguin08 on 2006-06-01
Got my sound working, albeit not with great quality.  I'll fix that later.

On to fixing the internet!

---

### Post by InsanePenguin08 on 2006-06-01
Oh I feel dumb, the one thing I figured it wouldn't be.  Haha, I just had to activate the ethernet connection in Networking.

Thanks for asking those questions, God!  They really helped put me on the right track!

---

