---
title: "24&quot; iMac freezes after failed 1.4 EFI Firmware update"
date: 2010-01-31
forum: Apple Hardware Users
---

### Post by Mr. Win on 2010-01-31
After scouring the internets I'm hoping you guys could help me.

I was having trouble with boot camp waking from sleep which was supposedly cured by installing the [1.4 EFI Firmware update.]("http://support.apple.com/kb/DL823") While I was installing the firmware upgrade the computer crashed... when it rebooted it took (and continues to take) about 10minutes to boot. Aside from random freezing (more frequent under heavy use), my firewire ports are dead. 

I've tried re-installing the firmware but the it say this computer does not need this update. 

I'm at a loss... any ideas has anyone else had this problem?

Computer Specs:

OSX 10.6.2
2.16 Core 2 Duo
2GB ram

---

### Post by Mr. Win on 2010-01-31
I've  also tried everything outlined in the article: [Can't install EFI Firmware Update? Check partition scheme; disconnect peripherals]("http://reviews.cnet.com/8301-13727_7-10329023-263.html")

> *"So the procedure would be: Use Disk Utility to Get Info on your internal drive (the whole thing, not just a partition of it) and thus check the partitioning scheme of your internal drive. If it isn't GUID, then you could clone to an external drive, boot from the external drive or from your installer DVD, repartition the internal drive as GUID, clone back from the external drive to the internal drive, boot up from the internal drive, and perform the firmware update."*

---

### Post by linuxopjemac on 2010-01-31
Serious stuff. I would ask the people at the [Apple discussion forums]("http://discussions.apple.com/index.jspa").

---

### Post by Mr. Win on 2010-01-31
Yea, I've cross posted over there... hopefully I can figure something out.

---

### Post by Mr. Win on 2010-02-01
still no luck... anyone have any success with this?

---

### Post by djchandler on 2010-02-01
Just a suggestion. Can you run a downgrade to the previous firmware version?

If you can't downgrade then re-run the upgrade, I hope this is a socketed chip for your sake. If it is, it should be a fairly simple fix to pry out the old chip and snap in a new one. I have no idea how expensive that could be.

If it's surface mounted, this is going to be a real pain, perhaps even requiring a logic board swap.

Do you have a local recycling center? Finding an iMac with a bad display that somebody threw away is what you would be looking for. I know a guy here that used to be a MacGenius, and is probably one of the few who can live up to that label. He's also a past president of the local Mac users' group. He and another friend of mine (now deceased) can/could revive Macs that any sane person would give up on. If you are still flummoxed after this, post here again, and I'll do what I can to put him in contact with you.

I also suggest that an adequate UPS may be a good idea if you experience power interruptions frequently at your location. This is an example of a worse case result due to a power failure. That's an assumption on my part as to why the computer crashed while flashing your firmware. If the power fluctuation/failure did not affect all service at your location, it may be that the power supply is going bad. What a terrible time to discover that.

I hope your iMac isn't ruined.

---

### Post by Mr. Win on 2010-02-02
It's mounted... the big problem is that the computer does not recognize a problem with the EFI firmware. I need a way to trick it into thinking there's a problem.

---

