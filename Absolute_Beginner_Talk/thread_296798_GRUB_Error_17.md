---
title: "GRUB Error 17"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by drewnoakes on 2006-11-10
Hi,

I'm fairly new to Linux and so have gone with Ubuntu.  All was going well until the machine started behaving strangely (saying that my disk was mounted as read-only), so I rebooted.  This worked temporarily as the problem repeated, only this time a reboot wouldn't launch the X server.  It said something about unmounting the disk, which I faithfully did.  Now the machine won't boot.  I'm sure more knowledgeable than I would laugh at this, and I'm hoping they'll be able to help!

I've hunted about for this problem -- seems like I need to boot using a rescue disk of some sort, then reconfigure Grub.  I'm stuck on the first step -- the installation disk I used boots ok but wants to do reinstall that would erase the disk's contents.  One thread I read mentioned using Knoppix (which is downloading now), but I don't know whether different flavours of Linux play well together.

Your help sincerely appreciated :)

Drew.

---

### Post by Sef on 2006-11-10
> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Get [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by drewnoakes on 2006-11-10
Hi Sef,

Thanks for your response.  I used the Knoppix LiveCD (which comes with TestDisk) to run TestDisk.  It validated the partition table, and I then overwrote the MBR with the TestDisk version.  This gives me the prompt...

1234F:

...at bootup, which the docs tell me means disk 1,2,3,4,floppy.  Pressing 1 moves the cursor to the next line as if it's doing something, but then nothing happens.  Pressing any other key simply repeats the prompt.

TestDisk said my first partition was bootable.

I'm officially confused and stuck now.  Help!

---

