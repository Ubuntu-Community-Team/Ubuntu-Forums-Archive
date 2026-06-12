---
title: "Crash when upgrading from 7.04 to 7.10"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Igniteflow on 2007-10-29
Apologies in advance if this has already been covered, but couldn't find a post on the topic.

I've recently installed Ubuntu 7.04 and was just started to get comfortable with it.  I tried to upgrade to 7.10 but then the download got stuck (crashed) at 42 mins remaining for a few hours so I had to reboot.  I tried to get back into Ubuntu but just got a whole load of errors.  I went into XP (dual boot setup) and used Norton Partition Magic to wipe the Linux partition so I could start again from scratch with the Ubuntu 7.10 install CD this time, but now my whole computer is screwed.  It won't boot into anything and just hangs on startup saying (The dual boot menu has vanished now):

GRUB Loading srage1.5.

GRUB loading, please wait...
Error 15

I'm guessing I need to reset the BIOS, but haven't the first clue how to do that.  Any help would be hugely appreciated, I reallly want to get Ubuntu up and runnning again and not give up back to Windows.

Noob

---

### Post by Clickbg on 2007-10-29
Get a fdisk or cfdisk on floppy or CD mount(DOS have fdisk) and manage the partitions(just delete them) BE CAREFUL that will erase all your data, so try to backup with Knoppix or from DOS mount. After you delete the old partitions, just boot the Ubuntu CD. If it does not work, reboot press DEL, enter the BIOS settings and set First Boot Device to be CD, same if you can`t boot the floppy/CD with cfdisk/fdisk. Good luck!

---

### Post by jaybombalous on 2007-10-29
couldn't u just theoretically boot to the LIVE cd and backup for your files from there by accessing the main disk?

---

### Post by Igniteflow on 2007-10-30
Thanks for the advice people, it was cool to get a response so quickly.  In the end I threw in the towel and went for a fresh install, which took a while but am up and running again now.  In hindsight, I think the problem was maybe down to my ATI Radeon graphics card.  If anyone finds themselves in a similar position, you might find the following thread helpful [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

