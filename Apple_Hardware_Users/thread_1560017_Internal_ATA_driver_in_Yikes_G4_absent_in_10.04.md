---
title: "Internal ATA driver in Yikes G4 absent in 10.04"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by Macalla on 2010-08-24
OK I have a problem when trying to install 10.04 directly from a alternate iso directly to my G4 Yikes. Apparently during the 'disk drive' detection phase of the install, right before partitioning, the internal ATA/IDE controller for the HDD cannot be found.

I don't understand how the DVD drive is detected whilst the HDD isn't because they use the same controller.

Any suggestions or work arounds?
Thanks

---

### Post by linuxopjemac on 2010-08-26
Do you have other hard drives connected? You might want to take out the drives you don't need. You might want to play with master/slave.

---

### Post by Macalla on 2010-08-26
There is only one drive connected on the first bus, a DVD-RW and a Zip on the second one.

This is what I did last night...

OK, so I started with 8.04 which installed and ran just fine. Used the software updater to install 10.04 and after a successful install, the G4 doesn't find the drive anymore. So my Yikes G4 just loops between the 1st and 2nd stage boot sequences.
Does an upgrade somehow rewrite the yaboot file and also wipe out the HDD drivers? I can't really tell what goes on during the install process as the text scrolls by too quickly..

Anyone with similar hardware figured out a way to get 10.04 installed? (G3 Yosemite, G4 Yikes, both with PCI graphics)

---

### Post by linuxopjemac on 2010-08-26
That looks like a driver issue. Maybe you can find a bug report about this.

---

### Post by Macalla on 2010-08-26
Thanks, I'll probe around a little more to see what I can find. I'll try my other alternate iso's to see at which release did support for my computer's ATA controller cease. Will report back.

8.04 - yes
8.10 - yes
9.04 - yes
9.10 - no
10.04 - definitely no.

---

### Post by Macalla on 2010-08-28
> **Macalla said:**
> Thanks, I'll probe around a little more to see what I can find. I'll try my other alternate iso's to see at which release did support for my computer's ATA controller cease. Will report back.

8.04 - yes
8.10 - yes
9.04 - yes
9.10 - no
10.04 - definitely no.


I found an alternative that solves the ATA drive controller issue. Debian 5.0.5.

---

### Post by linuxopjemac on 2010-08-29
Very good!

---

### Post by Macalla on 2010-08-31
An update. I decided to install Debian 5.0.5 on my powerbook Ti 500MHz after tackling the two PCI-graphics G4 towers (with the IDE/ATA driver issue) and discovered I had to edit the xorg.conf file like I did in Lucid to get my GUI up and running. It booted up with a blank screen as well.
The same [xorg.conf ]("http://mac.linux.be/content/xorgconf-powerbook-g4500-15-inch-ati-rage-128")file worked for me.

---

