---
title: "(K)ubuntu on 1015PEM"
date: 2011-06-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Zacariaz on 2011-06-21
On my new asus eee 1015pem I've tried to install debian 6.0 amd64, debian 6.0 i386 netinst and kubuntu 10.04 LTS and64 from usb, using both linuxlive and universal usb creator. I've event tried wubi, which also failed, though the problem may very well be unrelated.

[wubilog]
[http://myhideout.eu/temp/wubi-10.04-rev189.log](http://myhideout.eu/temp/wubi-10.04-rev189.log)
[http://myhideout.eu/temp/wubi-11.04-rev211.log](http://myhideout.eu/temp/wubi-11.04-rev211.log)
nb: the md5sum error is unlikely to be correct.
I may have made some sort of mistake, though I can't figure out what.
[/wubilog]

The problem is the step just before the partitioning, where there's some disk detection/scanning going on. In debian it stops at 50%, in kubuntu 47-48%. I've noticed no disk activity at all. It's not frozen, simply inactive. Yes, I have waited for a very long time for something to happen
I'm perfectly able to boot in to live mode.
The usb key has been used for this purpose on numerous occasions, so it is unlikely to be the problem.
I've tried messing around in the bios, ahci, ide, compatability, etc., but haven't made a difference.

I'm out of ideas and need help, as I absolutely refuse to run windows on a hardware platform like this.
I have of course done a lot of googlin, and tried various support chats, but have had no luck at all.

Best thing I can come up with, apart from some odd bios setting that I have overlooked, is that windows/asus have somehow "locked" the disk, though I'm not even sure that is possible.
Best solution I can think of is to nuke the disk, but I date not as it will render the computer completely useless if it does not solve the problem.

I do hope you can help, otherwise I've wasted a lot of money.

Edit:
I should mention after checking, the disk is mounted in live mode and don't seem to course trouble.
There are 3 partitions, 2 of which seem to be regular windows partitions, but the last one is rather odd, containing asus express gate. Not even sure it's actually located on the hard drive.

---

### Post by Zacariaz on 2011-06-22
Morning BUMP

Please, really need this.

---

### Post by Zacariaz on 2011-06-22
I haven't figured out exactly what the problem was. Turns out that nuking the disc didn't work, nor did using another USB stick, which I already knew of course.

Installing ubuntu 11.04 worked out perfectly though. I can only assume that it comes with another version of fdisk or something.

One thing that did strike me as odd though, is that the hdd apparently use a sector size of 2048. I though 512 was normal, but other than that, I really haven't got a clue.

If anyone has got an idea, I'd very much like to know.

---

### Post by Mark Rose on 2011-06-25
I just bought this machine right now. 

New hard drives us a sector size of 2048 bytes, because the old size (512 bytes) was very inefficient. The consistency checking and error correction overhead took up a significant percentage of the total disk space. Other new features include supporting drives over 2 TB in size.

---

