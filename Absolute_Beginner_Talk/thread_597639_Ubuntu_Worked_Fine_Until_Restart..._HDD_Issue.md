---
title: "Ubuntu Worked Fine Until Restart... HDD Issue?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Ocarina654 on 2007-10-30
I recently installed 7.10 from an Alternate CD and was extremely happy with how fast the system seemed to work.  I'm fairly new to Linux, and was getting used to how everything worked.  Aside from logging in to Pidgin and installing various audio and video codecs, I didn't change anything.

Then I restarted.

Now whenever I boot I get a blank screen for a few minutes then this error message:
ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata3.00: cmd c8/00:00:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Buffer I/O Errior on device sda, logical block 0

After a few minutes the first two lines start repeating.  I'm not shure the exact interval, but every few minutes or so those two lines pop up again.  This last for about 30 minutes before the machines just stops.

Now, SDA is my HDD, obviously, and there's some sort of error reading from it, but I've no idea what anything else could possibly mean.
This I/O error appears to be a Ubuntu error, as running a Knoppix Live CD it works and I can access the drive.

Google searches have yeilded no results, it seems the "Biffer I/O" problem occours in Flash Drives, of which my HDD is not!

I'm worried about HDD failure, but this doesn't seem to be it.

edit: I know that system information, as well as the make/model of the HDD will be useful, so I will be posting that soon, when I have most of it together.

---

### Post by snickers295 on 2007-10-30
yes i'm sorry, that sounds like hard drive failure.
can you give me your specs please?
i had a hard drive fail and i could still read it but could not write it or boot it.

---

### Post by Ocarina654 on 2007-10-31
Intel Pentium D Processor 830 (Dual Core) 3.00ghz
4 Gigs of DDR2 PC2--4200 RAM
250GB 7200RPM Serial ATA Hard Drive.  Can't tell who made it, but it's an HP machine.
ATI Radeon X300 SE

Sometimes I'm not shure what else anyone wants... haha.

I've sorta resigned myself to the fact that it is a HDD failure, and am shopping for a new one...

Any insights that would save me money would be appreciated.  Then again, if I replace it'll be an upgrade in size (i hear the 1 TB drives are really nice), not just a replacement.

---

### Post by snickers295 on 2007-10-31
> **Ocarina654 said:**
> Intel Pentium D Processor 830 (Dual Core) 3.00ghz
4 Gigs of DDR2 PC2--4200 RAM
250GB 7200RPM Serial ATA Hard Drive.  Can't tell who made it, but it's an HP machine.
ATI Radeon X300 SE

Sometimes I'm not shure what else anyone wants... haha.

I've sorta resigned myself to the fact that it is a HDD failure, and am shopping for a new one...

Any insights that would save me money would be appreciated.  Then again, if I replace it'll be an upgrade in size (i hear the 1 TB drives are really nice), not just a replacement.
some bigger drives don't work well with Linux.
it looks like ubuntu didn't ever read 1 byte off of the drive.
maybe your drive is not supported by Linux [http://www.linux.org/docs/ldp/howto/Hardware-HOWTO/disk.html](http://www.linux.org/docs/ldp/howto/Hardware-HOWTO/disk.html)

---

