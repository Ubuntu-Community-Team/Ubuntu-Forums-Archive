---
title: "PCMCIA Iomega 2MB Jaz Drive"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by stelloscuro on 2007-02-25
I am trying to get my 2GB Jaz drive through a pcmcia card to work on My T21 Thinkpad running Edgy.  I have run dmesg and find no reference to the drive.  Has anyone done this?, I could do with some help!

---

### Post by george29 on 2007-02-25
a quick google search found this 

[http://www.linux.com/howtos/Jaz-Drive-HOWTO.shtml](http://www.linux.com/howtos/Jaz-Drive-HOWTO.shtml)

have a read it is a bit old - but you should be able to adapt it so you can use the drive with ubuntu

---

### Post by stelloscuro on 2007-02-25
Having read this I think my problem is pcmcia based, I have a serial cable somewhere I may try that.  The unit works under XP, so I need a little help in ubuntu:)

---

### Post by george29 on 2007-02-25
[http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS)

if you search for iomega on that page it will show you which pcmcia cards are supported - the pcmcia card just acts as a scsi link.

so you should be able to get it all working with the pcmcia connection.


edit - it's just occurred to me that pcmcia_cs refers to modules for 2.4 kernels, so the drivers necessary for a pcmcia scsi adaptor should be included in the 2.6 kernel (or you may need to compile your own with them included). maybe someone else will know more about that?

---

### Post by stelloscuro on 2007-02-25
hmm, if I change the SCSI id to 0 I can get a reference to the iomega jaz but without giving any mount name. I dunno anything about kernels!

---

### Post by george29 on 2007-02-25
that would appear to be some progress at least... all i can suggest is that you have a play, read the how to i linked to and see if you can get anywhere. make sure all the required utilities etc are installed and see what happens. 

hope you get somewhere with it all.

george

i wouldn't worry about the kernel until you've tried everything else first. then try reading up on it... it's not as difficult as you might think.

---

### Post by stelloscuro on 2007-02-26
I have managed to mount the drive once and now it has disappeared from /dev on reboot.  Strange!

---

### Post by stelloscuro on 2007-02-26
BUMP, Anyone?

---

### Post by stelloscuro on 2007-03-05
Well, all I can gather is that it is a kernel problem which does not support my scsi card.  I will leave it now :(

---

