---
title: "Device names / boot order keeps changing"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mbspark on 2007-04-22
I have the strangest problem. I've searched all over the web/forums for anyone with a similar issue and can't find it.

My boot order keeps changing every time I restart my computer. I have 3 hard drives in my pc. 1 has ubuntu on it, one has vista and 1 is used for storage.

1 out of 3 times my machine will boot correctly. If I reboot and load ubuntu I get the "tty control error." Telling me that the boot device isn't labeled correctly. If I restart my machine, same thing, restart again, same thing, then the 3rd time...bam, it loads up!

If I take a live cd and check out the partition names, they change every time I restart. It's like they keep cycling around. It makes no sense. I could just edit the grub listing and guess what my machine named it, but right now it's easier just to keep restarting until it kicks off.

Does anyone out there have an idea of what could be going on? If I'm not explaining this very well, let me know.

Thanks in advance!

---

### Post by SOULRiDER on 2007-04-22
No idea at all. Maybe some setting in your BIOS?

---

### Post by Mann1ers on 2007-06-16
I also have this problem.

I have two hard drives.

When I boot first time, they are:

HD1 = sda
HD2 = sdb

But after I restart they become

HD1 = sdb
HD2 = sda

This is messing my whole system up, as you can imagine. Any suggestions?

Thanks.

---

### Post by sw1ng on 2007-11-02
I had the same problem, which I just posted about here: [http://ubuntuforums.org/showthread.php?t=601105](http://ubuntuforums.org/showthread.php?t=601105)

If you're not using LVM, you might try using the mount-by-label or mount-by-UUID methods I mentioned (which I can't use because of lvm, I think). 

Instead of mount /dev/sda1, try using the entries in /dev/disks/by-label or /dev/disks/by-uuid.

Nick

---

