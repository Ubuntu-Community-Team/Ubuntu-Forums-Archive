---
title: "DVD not working ---&gt; System not booting"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by karl-arthur on 2007-10-10
Hi,

I'm afraid I seriously damaged my computer trying to fix a problem with playing DVDs, but hopefully someone in here might have a solution. I'm running Ubuntu 7.04 on a two and a half year old Dell Insprion 9300. I'm currently unable to boot the machine, so all error msgs and such are off memory, but I wrote them down shortly after it happened, so it should be sort of accurate.

First, I put in a movie DVD, and got the message: "Cannot mount: can't open /etc/mtab for writing: Input/output error" So I googled the msg and found [http://ubuntuforums.org/showthread.php?t=59539]("http://ubuntuforums.org/showthread.php?t=59539"),
Being inexperienced (dumb) but bold, I tried to run:

root@laptop$fsck -a

which warned me that doing that to a mounted filesystem might cause severe damage, but I figured it wouldn't hurt, as the dvd wasn't mounted (only later did it cross my mind that my hardrive was a mounted filesystem, as I said, dumb), and proceeded. This gave several lines which I didn't write down, pertaining to several mountpoints I recognized (sda1, for instance), and the term "inode" occured repeatedly. At this point, several other programs running froze, I tried to open system manager in the GUI to end them, but it wouldn't open, so I tried rebooting. I would have no such luck, as the machine now halts with the message "Grub Loading failed: Error 17"

Any advice would be highly appreciated, if only to recover my personal files, if the computer is dead (It has given me quite a lot of grief since I dropped it on the floor about a year ago, so an excuse for getting a new one wouldn't be all bad). Would I, for instance be able to boot with a Live CD? (I'd try, but i don't have imediate access to another machine with a CD burner). 

Cheers, Karl Arthur

---

### Post by philinux on 2007-10-10
My hard drive failed recently and I bought a 4gig usb pendrive and copied my home folder to it using the knoppix live cd. I used the knoppix cos it boots up and runs quicker on my old machine. I would try your ubuntu live cd to have a browse of your home folder. Thats the stuff that needs backing up. 

Sounds like fsck bashed your mounted file system maybe. Someone else may have a solution though.

---

### Post by karl-arthur on 2007-10-16
So I was finally able to get a Live CD, which I posting from right now, but I can't seem to find my home folder. Searched around the forum and it seem others have been in similar situations, but I can't get anything working... This is what I've tried:

ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda1 /media/old
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:/$ dmesg | tail
[ 1358.140000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 1948.300000] VFS: Can't find ext3 filesystem on dev sda.
[ 1965.460000] VFS: Can't find ext3 filesystem on dev sda1.
[ 2037.708000] VFS: Can't find ext3 filesystem on dev sda.
[ 2144.760000] attempt to access beyond end of device
[ 2144.760000] sda2: rw=0, want=4, limit=2
[ 2144.760000] EXT3-fs: unable to read superblock
[ 2200.884000] VFS: Can't find ext3 filesystem on dev sda1.
[ 2314.324000] usb 5-8: USB disconnect, address 2
[ 2577.844000] VFS: Can't find ext3 filesystem on dev sda1.
ubuntu@ubuntu:/$ 


Any suggestions?

---

