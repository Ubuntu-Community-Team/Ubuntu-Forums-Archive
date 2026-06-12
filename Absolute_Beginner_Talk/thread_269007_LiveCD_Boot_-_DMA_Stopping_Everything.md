---
title: "LiveCD Boot - DMA Stopping Everything"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by walesmd on 2006-10-01
I've been working on this for 2 hours - still have yet to get Ubuntu to boot into it's LiveCD mode. After some looking around and finding nothing helpful I've decided to try a new topic.

I've md5 checked the iso - it's ok.

I ran the disc scan within the Ubuntu boot menu and it checked all the files, then proceeded to the point at which it stops during normal boot.

I get the following error messages once the screeen goes all black (immediately after Linux kernel uncompressing), the following repeats about 3-4 times:

> hdc: timeout waiting for DMA
hdc: drive not ready for command

Then I get:
> Buffer I/O error on device hdc
sb_bread failed reading block
Unable to read page... (other, location information here)

I have disabled UDMA in my BIOS as well as adding the nodma switch to the Ubuntu command line (hitting F6 while the normal boot is highlighted, adding the command, then pressing Enter).

From what I have read, I believe this is an issue with my CD player possibly? Would it be worthwhile to take the machine apart and switch my CD/RW and my DVD-ROM locations on the IDE cable?

Can anyone think of anything else? Thanks again! You guys are great.

---

