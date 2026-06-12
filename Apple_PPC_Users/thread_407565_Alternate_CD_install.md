---
title: "Alternate CD install"
date: 2007-04-12
forum: Apple PPC Users
---

### Post by Lefkows on 2007-04-12
How do I download the Alternate CD. Also can Ubuntu be installed on a hard drive with a USB Interface, a Firewire interface or it doesn't matter what interface.

---

### Post by DerHesse on 2007-04-12
Check here for a location nearby (It's a good Idea to edit your profile regarding what country you are from): 
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) 

Now choose what version you want to download, e.g. Edgy from Germany.

Then look for "alternate"  e.g.: This one:
[http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso)

Language does not matter, they are all the same.

---

### Post by Lefkows on 2007-04-12
Thanks D,
   I didn't see any link to this from the Ubuntu website. I updated my profile as you suggested.

---

### Post by 3rdalbum on 2007-04-13
> **DerHesse said:**
> 
Then look for "alternate"  e.g.: This one:
[http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso](http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-i386.iso)

No! Don't waste your time trying to download this particular file - it's the x86 version and won't work on your PowerPC Mac.

You need this address:

[http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-powerpc.iso](http://de.archive.ubuntu.com/ubuntu-releases/6.10/ubuntu-6.10-alternate-powerpc.iso)

Also, you must install onto an internal hard drive or a Firewire one - the vast majority of PowerPC Macs will not boot up from USB, and the few that do boot from USB have USB 1, which will be waaaaay too slow for your liking.

---

### Post by Lefkows on 2007-04-13
Thanks very much for that info 3rdAlbum. I knew that an Tiger will not boot from a USB drive but was not sure about Ubuntu. After reading about the Alternate CD install I decided I really didn't neet it. I will wait for Feisty (PPC Version) that supposedly fixed the Fan Speed problem and attempt to install it on an external Firewire HD. I asked the question on the forum about booting Ubuntu from an external HD but got no responses. I was thinking that if I use the key combination at startup to ignore the internal HD then it would boot Ubuntu, but I am just guessing.

---

### Post by 3rdalbum on 2007-04-14
I haven't installed Ubuntu onto a Firewire hard disk before, but what should happen is this:

1. The Yaboot bootloader should install onto the external hard disk
2. The Mac's NVRAM (Open Firmware) will be told that it should boot up from the Firewire device
3. When the Firewire hard disk is turned off, Open Firmware will boot up from the startup disk that it CAN find - your internal one containing OS X.
4. When the disk is turned on, Open Firmware will find Yaboot and run it. Yaboot will then start Ubuntu.

---

### Post by Lefkows on 2007-04-14
Thanks again 3rdalbum. That means all I have to do is have the FW drive on and it will automatically boot from it. What would you expect would happen if I partition my external HD into 2 partitions. One with a clone of my Tiger internal HD and the other with Ubuntu. Would it still boot Ubuntu over Tiger?

---

### Post by 3rdalbum on 2007-04-15
It should do, as the Open Firmware will still be pointing to the Yaboot partition on the external hard drive, but Yaboot will discover the OS X partition and create an entry for it, so you'll be able to boot Tiger from within Yaboot.

NOTE: I'd appreciate someone who's dual-booted Ubuntu and OS X using external HDs to reply and confirm or deny what I'm saying.

---

### Post by pxwpxw on 2007-04-15
**Lefkows**

This is xubuntu610 on an external 160GB firewire drive with a powermacg5 with 2 sata drives, and macosx and other linux.

Firewire is the best solution, usb is also possible but not with direct booting. (tried both).

Please see your other thread, more appropriate topic for the external firewire aspect.

Booting Ubuntu from an external HD

[http://ubuntuforums.org/showthread.php?t=405102](http://ubuntuforums.org/showthread.php?t=405102)

---

